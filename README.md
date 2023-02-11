# ansible-role-iptables
Configure iptables

## Install

```shell
ansible-galaxy role install git+https://github.com/sergelogvinov/ansible-role-iptables.git,main
```

## Usage

```ini
# inventory file

[servers]
server-1          ansible_host=1.2.3.1
```

```yaml
# hosts/server-1.yaml
iptables_ipset:
  - name: ADMINS
    type: hash:net
    hosts:
      - 3.4.5.0/24

iptables_rules:
  - protocol: tcp
    port: 22
    ipset: ADMINS
    comment: "OpenSSH"
  - protocol: tcp
    port: 80
  - protocol: tcp
    port: 443
```

```yaml
# values.yaml

- hosts: servers
  roles:
    - ansible-role-iptables
```
