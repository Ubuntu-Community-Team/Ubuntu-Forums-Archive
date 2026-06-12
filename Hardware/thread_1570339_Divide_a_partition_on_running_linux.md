---
title: "Divide a partition on running linux"
date: 2010-09-08
forum: Hardware
---

### Post by alidanish on 2010-09-08
Hello

I have a dedicated server (Rack-mounted) which has Linux Redhat 5 installed on it. I want to install Debian lenny on it. The CD-ROM of the server is not working. USB CD-COM is not available too, due to organizational restrictions. I want to divide the linux partition so that I can place iso of Debian on the new partition where I will run it from and format  the linux redhat. 


**_PLEASE GUIDE ME HOW CAN I DIVIDE THE PARTITION ON RUNNING LINUX_[/I][/I]**


Thanks a lot
Ali Danish

---

### Post by hsoulen on 2010-09-08
Hi Ali,

You are in the wrong forums for sure, either Red Hat/Fedora or Debian forums would be a better choice but here is some generic advice:


[LIST=1]
[*]If Red Hat is running Gnome then GParted is the way to go, but without a live CD (no CD-ROM support) you will have issues as you will not be able to make changes to a mounted filesystem
[*]Can you not use a USB Key? Or is this the same Organizational Restriction?
[*]Even if you are able to partition the drive and copy the ISO file, you will only be able to mount it in Red Hat and start the install, it will then become a problem as if you remove the OS you used to mount the ISO file, well then you have no way to install!
[*]Your best bet is simple, setup a PC as a BootP/DHCP server on the same segment as your Red Hat server, if your network infrastructure allows setup a private IP address space then network boot the Red Hat server and install over the network.
[/LIST]
Good luck.

Hank

---

