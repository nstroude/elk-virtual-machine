# elk-virtual-machine
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/nstroude/elk-virtual-machine/blob/main/Diagrams/cloud%20security%20diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/nstroude/elk-virtual-machine/blob/main/Ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and reliable, in addition to restricting and distributing traffic to the network.
- Load balancers help mitigate DDoS attacks by helping to avoid overloading nodes on the network by effieciently distributing incoming traffic                          - A jumpbox is a secure computer that admin can use to securely ssh into their servers to do various administrative tasks

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resouces.
- Filebeat watches for logfiles and sends them to logstash or elasticsearch for indexing than data can be mined once it is structured
- metric beat records the output and statistics of services running on a server also sending those to logstash and elasticsearch

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux Ubuntu     |
| Web1     |Web Server| 10.0.0.5   | Linux Ubuntu     |
| Web2     |Web Server| 10.0.0.7   | Linux Ubuntu     |
| Elk vm   | Elk Stack| 10.1.0.5   | Linux Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-73.7.130.183

Machines within the network can only be accessed by the jumpbox.
-the jumpbox has access your ELK VM and its IP address is (public) 20.120.25.11 (private) 10.0.0.4 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 20.120.25.11         |
|  Web1    | No                  | 10.0.0.5             |
|  Web2    | No                  | 10.0.0.7             |
|  Elk     | No                  | 10.1.0.5             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- an advantage of configuring machines with ansible is that it is an efficient way to deploy configurations onto multiple machines, especially if you are running on a large network

The playbook implements the following tasks:
- Configure Elk VM with Docker
- install docker with docker .io for running containers
- Install python 3-pip to install python software
- Install Docker module
- Increase virtual mermory
- Download and lauch a docker elk container
- enable service docker on boot to restart docker when ELK vm restarts

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-The elk server is monitoring the following ip addresses 10.0.0.5 and 10.0.0.7

We have installed the following Beats on these machines:
Both filebeats and metricbeats are installed on the web vm's

These Beats allow us to collect the following information from each machine:
-Filebeats organize log files from Apache, Azure tools, Nginx webserver and My SQL database and sends it to Logstash and Elasticsearch to be searched and monitored
-Metricbeats collects measurements of a systems resources such as cpu usage and memory make sure the machine is working efficiently

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
