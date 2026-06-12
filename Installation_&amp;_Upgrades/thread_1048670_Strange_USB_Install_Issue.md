---
title: "Strange USB Install Issue"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by Lucroth on 2009-01-23
I'm trying to install Ubuntu 8.10 using the built-in USB install utility to a 16GB Sony MicroVault.

Alright, so I follow the instructions listed here, [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/) and when it finishes I can boot from it into the live session like I should. However theres a large section of space on the drive I simply cannot access.

I have now ran several tests and will list the results below. 

Test ONE: 
Documents and Settings slider all the way over at 14.2GB
When installing, completion bar goes to 32% and then it immediately stops and says it is ready.
Partition manager details for the drive after install: Total 14.94 GB, Used 4.7GB, Unused 10.24GB
Filesystem Properties after booting from the USB: 2.6GB used space, 3.6 GB free space

Test TWO: 
Documents and Settings slider all the way over at 10.0GB
When installing, completion bar goes to 43% and then it immediately stops and says it is ready.
Partition manager details for the drive after install: Total 14.94 GB, Used 4.7GB, Unused 10.24GB
Filesystem Properties after booting from the USB: 2.6GB used space, 3.6 GB free space

Test THREE: 
Documents and Settings slider all the way over at 7.0GB
When installing, completion bar goes to 62% and then it immediately stops and says it is ready.
Partition manager details for the drive after install: Total 14.94 GB, Used 4.7GB, Unused 10.24GB
Filesystem Properties after booting from the USB: 2.6GB used space, 3.6 GB free space

Test FOUR: 
Documents and Settings slider all the way over at 3.0GB
Completion bar goes to 100%
Partition manager details for the drive after install: Total 14.94 GB, Used 3.7GB, Unused 11.23GB
Filesystem Properties after booting from the USB: 2.6GB used space, 2.7 GB free space

I'm not sure what the problem is here, but it simply refuses to use more than 4.7GB for some reason. There also seems to be no way for me to access that unused 10GB at all. Does anyone know what the problem is here?

---

### Post by Pumalite on 2009-01-23
Follow this guide by Herman:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

