Terone Buie Project 1 read.me steps to creating virtual network

I started the creation of the cloud network by first creating the resource group and naming it “Red-team”


I then set up a virtual network that has the capacity to hold any resource that the red team needs. I named it “Red-net”

I created a network security group rule that blocked all traffic.

I created a key-gen for virtual machines using “ssh-keygen” in command line to create a new ssh key pair

I created my first virtual machine “Jump box provisoner”. This machine is used as a “jumpbox” to access my cloud network and any other machines inside vnet. The jumpbox is on the same “rednet” virtual network and the “redteam” resource group. It has a public ip address of 40.76.99.52


I created two more virtual machines “web-1, web-2” They have 2 gb of ram as where the jumpbox only required 1. They are using same resource group as all other resources. Web-1 has a private ip address of 10.0.0.5 Web-2 has private ip of 10.0.0.6



## Automated ELK Stack Deployment
 
The files in this repository were used to configure the network depicted below.
 

 
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.
 
  File-playbook.yml
 
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
 
 
### Description of the Topology
 
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
 
Load balancing ensures that the application will be highly efficient in addition to restricting overload to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?_
 load balancers add additional layers of security with changes to application. 
 load balancers protect networks from hackers with daily rule updates.
 having a jump box gives you the advantage of having remote access to vms.
 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_
 
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
 
| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| web 1    |   vm     | 10.0.0.5     Linux                      |
| web 2    |   vm     | 10.0.0.6   | Linux                 |
| elk vm   |   vm     | 10.1.0.4   | Linux
 
### Access Policies
 
The machines on the internal network are not exposed to the public Internet. 
 
Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
10.0.0.4
 
Machines within the network can only be accessed by jumpbox provisoner vm
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
 Only the jumpbox through the configured ansible container can access the elk vm
A summary of the access policies in place can be found in the table below.
 
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | 10.0.0.4 10.0.0.5 10.0.0.6    |
| web-1    | no                  |                      |
| web-2    | no                  |                      |
 elk vm      no                     local ip/10.0.0.4
 
### Elk Configuration
 
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
automated configuration allows for elimination of error, less maintaining of files needed
 
The playbook implements the following tasks:
- install docker i.o
- install python-pip3
- install docker module
 
The following screenshot displays 
 
We have installed the following Beats on these machines:
- web 1: 10.0.0.5
  web 2: 10.0.0.6
  Beats successfully installed: Filebeat
These Beats allow us to collect the following information from each machine:
Filebeat collects log files, sends data to elasticsearch for indexing
 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
 
SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible
- Update the host file to include...[elkadmin]
- Run the playbook, and navigate to http://machinepublicip on web brower to check that the installation worked as expected.
 
- _Which file is the playbook? Where do you copy it?_
- install-elk.yml, /etc/ansbile
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ /etc/ansible/hosts you set the elk servers to their own groups in /etc/ansible/hosts file path
- _Which URL do you navigate to in order to check that the ELK server is running?
http://publicipofmacine

