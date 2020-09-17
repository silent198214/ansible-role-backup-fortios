Ansible Role for backup Fortinet FortiGate config
=========

Fortinet FortiGate config backup via ansible playbook

Requirements
------------

1. Add ssh public key Public to admin user.

```bash
config system admin
    edit "admin"
        set ssh-public-key1 "<your public key>"
    next
end
```
2. Predefined ncftp bookmark

Role Variables
--------------

### defaults

|variable name|default|description|
|:-:|:-:|:-:|
|device_user|admin|FortiOS user account|
|device_port|22|FortiOS ssh port|

### vars

|variable name|default|description|
|:-:|:-:|:-:|
|ssh_option|"StrictHostKeyChecking=no"|bypass ssh host key|
|backup_local_path|"{{ role_path }}/files"|temp backup file path|
|backup_srv_path|"/Downloads/{{ inventory_hostname }}/"|backup server file path|
|backup_filename|"{{ inventory_hostname }}_{{ lookup('pipe', 'date +%Y%m%d') }}.conf"|backup filename|

Dependencies
------------

No

Example Inventory
----------------

example of inventory

```
firewall ansible_host=192.168.1.1

[fortios]
firewall
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: fortios
  gather_facts: no
  connection: no
  tags: fortios

  roles:
    - backup-fortios
```

Author Information
------------------

Sam Chen
