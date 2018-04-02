# week-9
secure software engineering week 9
https://i.imgur.com/mZE2bZY.gifv

# Lab 
- [x] Challenge 1
- [x] Stretch Challenge 2
- Milestone 2
- [x] Challenge 1
- [x] Challenge 2
- Milestone 3
- [x] Challenge
- Milestone 6
- [x] Challenge


## Assingment
1. Initializing the gcloud with region and zone and creating a project.

2. used command 
(gcloud beta compute firewall-rules create mhn-allow-admin --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:3000,tcp:10000 --source-ranges=0.0.0.0/0 --target-tags=mhn-admin) to create firewall rule to allow ingress traffic on TCP ports 3000 and 10000

3. Creating a mhn admin vm using command
(gcloud compute instances create "mhn-admin" --machine-type "f1-micro" --subnet "default" --maintenance-policy "MIGRATE"  --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring.write","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --tags "mhn-admin","http-server","https-server" --image "ubuntu-1404-trusty-v20171010" --image-project "ubuntu-os-cloud" --boot-disk-size "10" --boot-disk-type "pd-standard" --boot-disk-device-name "mhn-admin")

4. Establishing SSH access to VM gcloud compute ssh mhn-admin

5.Installing the MHN admin application onto VM :
   $ sudo apt-get update
   $ sudo apt-get install git -y
   $ cd /opt
   $ sudo git clone https://github.com/RedolentSun/mhn.git
   $ cd mhn
   $ sudo ./install.sh
   
6. Setting up basic configurations:
   Server base url ["http://#.#.#.#"]:  http://35.192.135.69
   Honeymap url ["http://#.#.#.#:3000"]: http://35.192.135.69:3000
   Mail server address ["localhost"]:
   Mail server port [25]:
   Use TLS for email?: y/n n
   Use SSL for email?: y/n n
   Mail server username [""]:
   Mail server password [""]:
   Mail default sender [""]:
   Path for log file ["/var/log/mhn/mhn.log"]:
   
7. Creating a honeypot vm :
   (gcloud compute instances create "mhn-honeypot-1" --machine-type "f1-micro" --subnet "default" --maintenance-policy          "MIGRATE"  --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring.write","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --tags "mhn-honeypot","http-server" --image "ubuntu-1404-trusty-v20171010" --image-project "ubuntu-os-cloud" --boot-disk-size "10" --boot-disk-type "pd-standard" --boot-disk-device-name "mhn-honeypot-1")

8. Installing the Ubuntu - Dionaea with HTTP on honeypot VM 

9. nmap 35.184.149.118 shows the open port which the server Dionaea uses to attract hackers.

