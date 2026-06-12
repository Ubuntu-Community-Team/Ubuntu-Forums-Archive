---
title: "Installing Brother network printer on Ubuntu 16 laptop"
date: 2018-12-26
forum: Hardware
---

### Post by allypi955 on 2018-12-26
Hello, I have a new Brother MFCJ955DX printer on my home network and have Ubuntu 16 on my laptop. I tried adding the printer to my laptop by going to system settings and adding the printer. It did not have my exact printer name so I picked the closest one. When trying to print a test page it gave message that the printer was idle. On the Linux Mint Forums I found the following post by ****@mint. I followed the instructions and solved the problem.

Linux-brprinter-installer

Step1. Download the tool.(linux-brprinter-installer-2.0.0-1.gz)
The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download

Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.

Step3. Enter this command to extract the downloaded file:
Command: gunzip linux-brprinter-installer-2.2.1-1.gz

Step4. Get superuser authorization with the "su" command or "sudo su" command.

Step5. Run the tool:
Command: bash linux-brprinter-installer-2.2.1-1 Brother machine name 

Step6. The driver installation will start. Follow the installation screen directions. 
 

When you see the message "Will you specify the DeviceURI ?",
For USB Users: Choose N(No)
For Network Users: Choose Y(Yes) and DeviceURI.
The install process may take some time. Please wait until it is complete.

Apparently Brother is a tricky printer to get to work with Ubuntu. Hopefully this will help someone.

---

