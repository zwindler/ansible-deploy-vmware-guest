# ansible-deploy-vmware-guest
Playbook and role to deploy VMware virtual machine from templates using Ansible

# Installation
You can add this role by simple a simple git clone

```
git clone https://github.com/zwindler/ansible-deploy-vmware-guest
cp -rp ansible-deploy-vmware-guest/deploy_vmware_guest.yml ansible-deploy-vmware-guest/roles /etc/ansible
```

# Configuration

You should create a group_var file in order to set the variables that don't usually change in order to simplify playbook file, such as
 * **vsphere_host**, the address/hostname of the vcenter server
 * **vsphere_user**, a username with enough vSphere privileges to create VMs from templates
 * **vsphere_datacenter**, the vSphere datacenter name
 * **vsphere_folder**, the folder where to drop VM ("/TO_DEPLOY" for ex.)
 * **guest_network**, **guest_netmask**, **guest_gateway**, **guest_dns_server**, **guest_domain_name**, the usual network informations for your VMs
 * **guest_id** depending on the OS you want to deploy
 * **guest_memory** and **guest_vcpu** for your VM sizing
 * **guest_template**, the template name to copy the VM from
 * **vsphere_host**, **vsphere_user** (usualy I use a **group_var/mygroup/main.yml** file, group being declared in **hosts_to_deploy** inventory file)

Then you should create a **hosts_to_deploy** file that will be a temporary inventory file to store the hostname to deploy, and add them inside this group.

Examples of theses files can be found inside this repository, under **group_vars/example_group.yml** and **hosts_to_deploy**.

# Execution

Don't forget the vmware_guest variables that already are playbook variables such as
 * **notes**, **vsphere_password**, **esxi_host** (prompted by playbook)
 * **creationdate** (automatically created)
 * **vsphere_datastore**, **guest_custom_ip** (usualy I put these as variables of the host in a **hosts_to_deploy** file)
