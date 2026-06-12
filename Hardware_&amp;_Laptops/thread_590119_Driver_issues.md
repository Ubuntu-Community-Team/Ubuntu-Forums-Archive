---
title: "Driver issues"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Maube-Not on 2007-10-24
Okay, I'm having problems installing drivers. This has been a problem since day one with Ubuntu, so i haven't been able to game at all. 

Thing is, it doesn't seem to work. I used Restricted drive managers, and even tried a direct update from [www.intel.com](www.intel.com) 

None of the things enabled Hardware acceleration as it should. 

System specs:

Intel(R) Pentium(R) M Processor 1.70GZ (Not sure if this is relevant, but whatever.)
Mobile 915GM/GMS/910GML Express Graphics Controller 

But whenever i run games, it says i don't have hardware support.

---

### Post by nelson.bolanos on 2007-10-27
You could try installing 915resolution, and checking tat your "device" listed in xorg.conf is using the appropiate driver "i810"

> sudo apt-get install 915resolution
> sudo vi /etc/X11/xorg.conf

---

