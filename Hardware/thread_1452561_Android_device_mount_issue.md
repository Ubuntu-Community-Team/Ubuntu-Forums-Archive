---
title: "Android device mount issue"
date: 2010-04-12
forum: Hardware
---

### Post by beloved88 on 2010-04-12
I have an HP mini 1101 running UNR 9.10.  So far i have tried two seperate Android devices, and i had no succes at mounting either, one was an Archos 5 internet tablet, the other is a Samsung Moment.  On both devices, after i plug it into the computer, the notification comes up asking if i want to mount the filesystem, and i tap "Mount" but my computer does nothing.  I dismissed the Archos 5 without looking into too much, since it was a return to our shop and I figured it was defective, but the Samsung Moment is brand new.  oh, here are the results of lsusb after i've plugged in the device
```
beloved88@Skipper:~$ lsusb
Bus 001 Device 013: ID 04e8:681d Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 10f1:1a13  
Bus 001 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:2a1d Hewlett-Packard 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
is there maybe a package not included in unr that i might need to mount these devices?

---

