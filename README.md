eNiXHosting.deb
=================

A role for deploying and configuring deb softwar sources list on Debian based distributions using [Ansible](http://www.ansible.com/).


Requirements
------------

Supported targets:

- Ubuntu all
- Debian all


Role Variables
--------------

This roles comes preloaded with almost every available default. You can override each one in your hosts/group vars, in your inventory, or in your play. See the annotated defaults in `defaults/main.yml` for help in configuration. All provided variables start with `deb__`.

- `deb__distribution` - Distribution selected for source software installation. Default to `{{ ansible_distribution }}`. Options are `["Debian", "Ubuntu"]`.
- `deb__release` - Distribution release software suite. Default to `{{ ansible_distribution_release }}`. Can be override for release upgrade for example.
- `deb__backports` - Enable the backports repository. *Only supported on stable distributions*. Default: `false`.
- `deb__updates` - Enable the updates repository. *Only supported on stable distributions*. Default: `false`.
- `deb__ubuntu_universe` - Enable the universe section of Ubuntu repositories. Default: `true`.
- `deb__ubuntu_multiverse` - Enable the multiverse section of Ubuntu repositories. Default: `true`.
- `deb__clean_sources` - Remove existing sources. Default is false, options are `["distribution", "all"]`. _"distribution"_ clean `/etc/apt/sources.list` whereas _"all"_ clean all `*.list` found files.

Dependencies
------------

- None

Extra
-----


Callable tasks:

- `task`: ...


Usage
-----

Clone this repo into your roles directory:

    $ git clone https://gitlab.enix.org/ansible/ansible-deb.git roles/deb

Or use Ansible galaxy requirements.yml

    # deb from eNiXHosting
    # public role
    - src: eNiXHosting.deb
      name: deb

And add it to your play's roles:

    - hosts: all
      roles:
        - role deb:
            deb__var: true

You can also use the role as a playbook. You will be asked which hosts to provision, and you can further configure the play by using `--extra-vars`.

    $ ansible-playbook -i inventory --extra-vars='{...}' main.yml

Still to do
-----------

- var to Erase distro default sources
- add extra repositories options
- var to disable recommends installation
- var to add a proxy configuration
- Add Devuan support
- Add update, dist-upgrade, autoremove, clean tasks
- Add option to add src repositories

Changelog
---------

### 1.0

Initial version.

License
-------

GPLv2

Author Information
------------------

Laurent Corbes <laurent.corbes@enix.fr> - http://www.enix.fr
