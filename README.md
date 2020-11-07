# Project_1
Files and resources for project 1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images\Project_Diagram.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook.yml
  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly monitored, in addition to restricting SSH to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancing ensures the availability of the information by keep the VMS from doing too much work at once. The jumpbox gives you an single entrance point to the VMS. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the operating system and system logs.
What does Filebeat watch for? Any changes to your system logs
What does Metricbeat record? the system metrics, letting you know when things are back online

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table.

| Name     | Function                   | IP Address | Operating System |
|----------|----------------------------|------------|------------------|
| Jump Box | Gateway                    | 10.0.0.5   | Linux V 2.2.5.2  |
| Elk      | Watch vulnerabilities      | 10.1.0.4   | Linux V 2.2.5.2  |
| Web-1    | Test for File/Metric beats | 10.0.0.6   | Linux V 2.2.5.2  |
| web-2    | Test for File/Metric beats | 10.0.0.7   | Linux V 2.2.5.2  |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Add whitelisted IP addresses_ 104.40.0.84 (10.0.0.5)

Machines within the network can only be accessed by the JumpBox.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Jumpbox - 104.40.0.84

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Address |
|----------|---------------------|--------------------|
| Jump Box | Yes                 | PC public IP       |
| Elk      | No                  |                    |
| Web-1    | No                  |                    |
| Web-2    | No                  |                    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible? there is one place for editing if there are any errors. Lowers the possibility of run errors and syntax errors

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.ip and modules
- Installs python3-3 pip
- Increases the virtual memory
- tells system to use more memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
-10.0.0.6
-10.0.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- filebeat

These Beats allow us to collect the following information from each machine:
- Filebeats allows us to collect the logs from web-1 and web-2 and allows us to query the information in a systematic way. Allowing us to see things like runs and logtimes.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat congifuration file to filebeat.yml
- Update the config file to include the elk group
- Run the playbook, and navigate to Module status on the Elk server GUI to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ filebeat-playbook.yml you copy it to the Web VM's
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ the Host file. in the individual plabooks you would change the hosts to the appropriate name
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
