---
title: "How to change the mousepolling rate?"
date: 2016-11-06
forum: Hardware
---

### Post by deadtom on 2016-11-06
I'm trying to resolve the mouse problem with unity3d games. A few people have reported that changing the mouse polling rate fixes the issue. The problem is that I can't figure out how to change mine.


I have a logitech trackball.


I've tried adding the following lines to /etc/modules:


-r usbhid
usbhid mousepoll=8


This should set the polling rate to 125HZ.


I reboot and do a cat /sys/module/usbhid/parameters/mousepoll and it always returns '0'.


I've also tried adding the following line to /etc/modprobe.d/usbhid.conf:


options usbhid mousepoll=8


Reboot, mousepoll still shows '0'.


I'm using 64bit Kubuntu 16.04, fully updated.


Any idea what I'm doing wrong?

---

