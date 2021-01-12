# [virtualbox](#virtualbox)

Install and configure virtualbox on your system.

|Travis|GitHub|GitLab|Quality|Downloads|Version|
|------|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-virtualbox.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-virtualbox)|[![github](https://github.com/robertdebock/ansible-role-virtualbox/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-virtualbox/actions)|[![gitlab](https://gitlab.com/robertdebock/ansible-role-virtualbox/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-virtualbox)|[![quality](https://img.shields.io/ansible/quality/46445)](https://galaxy.ansible.com/robertdebock/virtualbox)|[![downloads](https://img.shields.io/ansible/role/d/46445)](https://galaxy.ansible.com/robertdebock/virtualbox)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-virtualbox.svg)](https://github.com/robertdebock/ansible-role-virtualbox/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.virtualbox
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.ca_certificates
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for virtualbox

virtualbox_version: "6.1"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-virtualbox/blob/master/requirements.txt).

## [Status of requirements](#status-of-requirements)

The following roles are used to prepare a system. You may choose to prepare your system in another way, I have tested these roles as well.

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |
| [robertdebock.ca_certificates](https://galaxy.ansible.com/robertdebock/ca_certificates) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-ca_certificates.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-ca_certificates) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-ca_certificates/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/ansible-role-virtualbox/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|el|7, 8|
|debian|buster|
|fedora|32|
|ubuntu|focal, bionic|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| centos:8 | Ansible module rpm_key is not idempotent. |
| fedora | file /usr/bin/VBox conflicts between attempted installs of VirtualBox-6.1-6.1.10_138449_fedora31-1.x86_64 and VirtualBox-5.2-5.2.42_137960_fedora29-1.x86_64 |


## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-virtualbox) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-virtualbox/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
