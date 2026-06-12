---
title: "Wireshark .deb install w/ no Internet"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by krimzen85 on 2009-08-17
Hey All,
 
Getting ready to install Wireshark on my Servers, but I have no internet, so I am going to download:
 
wireshark_1.0.7-1ubuntu1_i386.deb
 
from a Window's machine, throw it on a USB stick, and then boot up Ubuntu and put the stick in the drive.
 
**Can anyone give me the commands to install a .deb file/application in Ubuntu from USB stick?**

---

### Post by Partyboi2 on 2009-08-17
Hi, once you have your usb mounted you would change into the directory with 'cd' so if it was mounted at /media/disk
```
cd /media/disk
```
then install the deb with
```
sudo dpkg -i  wireshark_1.0.7-1ubuntu1_i386.deb
```

---

