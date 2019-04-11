# SSH-Access
Granting/revoking SSH access to a group of servers instances to a new developer

## Use the below command to add a new user and grant SSH access
ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml

## Use the below command to grant SSH access to an existing user
ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml --skip-tags=add

## Use the below command to revoke SSH access for a user
ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml --skip-tags=remove

## Use the below command to remove a user and revoke SSH access
ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml


## Notes
 - Please make sure to add IPs or DNS of target instances Under [instances] group in inventory/hosts files.
 - Update the varibale "user_name" and "user_des" as per requirements. You can add multiple values as well to run the action 
   for mutiple users at a time.
 - Make sure to create a directory under "sshkeys" directory of same name as user name and put its SSH public key under it.
 - I have used AWS instances as target instances so the user is "ec2-user". 
   Please make sure to use appropriate user in "ssh.yml" who has access to target servers.The machine from where you will run Ansible 
   should have passwordless login to target servers.  
