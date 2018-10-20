# NetScaler MAS / Citrix ADM - Ansible configuration playbook
## Introduction
This playbook configures Citrix NetScaler MAS / Citrix ADM (on-premises). If a parameter is changed, you can just run the playbook again and it will update the configuration.

### What is configured
- Logs on to MAS using HTTPS
- Verifies if nsroot has been changed. If masAdminUsername is nsroot it changes the password to what is defined in masAdminPassword.
- Configures:
  - DNS servers
  - time zone
  - system settings
  - prune policy
  - syslog purge settings
  - backup policy
  - device backup policy
  - NTP sync and servers (reboots server if required)
  - LDAP servers and enables them as external authentication servers
  - Adds groups

## How to run the playbook
### Pre-requisites
- Python
- PIP
- Ansible

### Citrix ADM
- Deployed on-premises
- Change the parameters in [netscaler-mas.yml](group_vars/netscaler-mas.yml)

### Ansible playbook
ansible-playbook -i hosts hosts site.yml "masAdminUsername=*MAS-Username*" -e masAdminPassword='"*MAS-Password*"' -e "masIpAddress=*IPAddress*" -e ldapPassword='"*LDAP-Password*"'

## Todo
- Configure SSL for management
- Configure licenses
- Refactor with include_task to make the different easier to find and work with