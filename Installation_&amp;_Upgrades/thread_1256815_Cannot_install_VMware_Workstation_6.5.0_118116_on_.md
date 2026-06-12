---
title: "Cannot install VMware Workstation 6.5.0 118116 on Ubuntu 8.04"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by iniesta on 2009-09-03
Hi everyone,

I failed installing VMware Workstation 6.5.0 118116 on Ubuntu 8.04 from a .deb package.

Here is what I've done:

sudo dpkg -i vmware-workstation_6.5.0-118166_i386.deb

and I got some messages as follow:

"...158943 files and directories currently installed.)
Preparing to replace vmware-workstation 6.5.0-118166 (using vmware-workstation_6.5.0-118166_i386.deb) ...
Unpacking replacement vmware-workstation ...
Setting up vmware-workstation (6.5.0-118166) ...
Extracting VMware Installer...done.
You must accept the EULA to continue. Press enter to proceed..."


I then accepted the EULA and the installation process continued until it reached:

"Installing VMware Installer 1.0
Copying files...
Configuring...
Installing VMware Player 2.5.0
Copying files...
Configuring...
Installing VMware VIX API 1.6.1
Copying files...
Configuring...
Installing VMware Player 2.5.0
Copying files...
Configuring...
Installing VMware Player 2.5.0
Copying files...
Configuring...
"

and it just hangs there. I waited more than 2 hours but nothing happened. I rolled back the process and reinstalled it but the result was the same.

There must be something wrong with my machine. Please help me to find out the problem.

Thank you very much for reading my topic. Any responses would be much appreceated.

Iniesta.

---

### Post by stefangr1 on 2009-09-03
Did you install the headers of your running kernel?

If not, install them with:
sudo apt-get install linux-headers-`uname -r`

You also need to install the build essentials:
sudo apt-get install build-essential

---

### Post by iniesta on 2009-09-03
> **stefangr1 said:**
> Did you install the headers of your running kernel?

If not, install them with:
sudo apt-get install linux-headers-`uname -r`

You also need to install the build essentials:
sudo apt-get install build-essential

Hi **stefangr1**, thank you very much for your answer. I did install those two items. To be sure, I typed the above commands again and I got the following messages:


:~/Desktop$ sudo dpkg --configure -a
:~/Desktop$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-24-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
:~/Desktop$ 

Please help me to solve my problem. Its very urgent. Thank you again.

---

### Post by stefangr1 on 2009-09-03
The problem is that your installation process did not result in specific error messages, which makes it very difficult to track the problem.

Would it also be possible to use vmware-server-2 for your purposes? If so, you can try the .tar from the vmware website and see whether it installs correctly or produces any error messages.

---

### Post by iniesta on 2009-09-03
> **stefangr1 said:**
> The problem is that your installation process did not result in specific error messages, which makes it very difficult to track the problem.

Would it also be possible to use vmware-server-2 for your purposes? If so, you can try the .tar from the vmware website and see whether it installs correctly or produces any error messages.

Thank you for your suggestion but I use VMware for software testing, I need the snapshot feature which vmware server does not have. So I have to stick with vmware workstation.

About the specific error messages, if my memory serves me correctly, there has been a message about an illegal number (7) or something like that. I can't reproduce it right now because I am not at my computer.

Well, anyway thank you very much for your help. I will try again and hope that I can find a way... :(

---

### Post by stefangr1 on 2009-09-03
> **iniesta said:**
> Thank you for your suggestion but I use VMware for software testing, I need the snapshot feature which vmware server does not have. So I have to stick with vmware workstation.

VMware-server does also have the snapshot feature.

---

### Post by iniesta on 2009-09-09
> **stefangr1 said:**
> VMware-server does also have the snapshot feature.

Well, I have found an excellent alternative to VMware workstation: Sun VirtualBox. I've installed it and run it smoothly on my machine. It's light and free and enough for my purposes.

Thank you for your answers :D

---

