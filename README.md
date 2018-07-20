# ansible-lubuntu-post-installation
Ansible script to automatically install all needed software and to fine tune some configuration on my new developer machine. The script is to be executed after a fresh Lubuntu installation with the following command:
```bash
ansible-playbook playbook.yml -i inventory -bK
```
(b: become, K: ask-become-pass)

## Instructions
1. modify the inventory/hosts file:
	1. change ansible_user to your user name
	2. if you want to execute the ansible script from another computer, then add the IP address of your newly installed computer under [local] and remove the localhost entry
2. check the playbook.yml to make sure, it only contains the software you want to be installed on your newly installed computer

## Notes
* If you want to execute the Ansible script from a remote machine you must first manually install the openssh server and start it (sudo apt-get install openssh-server).
* Then there must be a user with the same name as the ansible_user configured in the inventory/hosts file (with sudoer rights).
* To use this playbook locally the following software must be previously installed:
	* sudo apt install ansible
* To use the playbook from a remote machine the following software must be previously installed:
	* sudo apt install sshpass
	* plus you might have to ssh into the notebook previous to running the playbook, if you execute it remote.
* Some software must be installed manually (I was too lazy to write the tasks for those) -> see comments in the playbook