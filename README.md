# Azure route server no-advertise lab

This creates an onprem vnet with Cisco ASAv connected to a hub vnet ASAv that is peered with a route server, and a spoke vnet peered to the hub. This lab adds a vpn gateway to the hub and a second onprem vnet with an asav that has an ipsec tunnel to the vpn gateway. The hub asav is advertising the 192.168.0.0/16 route to the route server with the no-advertise community so the vpn gateway will not learn this route but vm's in the hub vnet will.  VM's are created in all 4 vnets. You'll be prompted for the resource group name, location where you want the resources created, your public ip, and username and password to use for the VM's and NVA. NSG's are placed on the default subnets of each vnet allowing RDP access from your public ip. This also creates a logic app that will delete the resource group in 24hrs. The topology will look something like this:

![RSlab-asav-noadvertise](https://github.com/quiveringbacon/Azurerouteserver-noadvertise-lab/assets/128983862/00191cf2-000e-483b-ba5e-2c78c9bf1da6)

You can run Terraform right from the Azure cloud shell by cloning this git repository with "git clone https://github.com/quiveringbacon/Azurerouteserver-noadvertise-lab.git ./terraform". Then, "cd terraform" then, "terraform init" and finally "terraform apply -auto-approve" to deploy.
