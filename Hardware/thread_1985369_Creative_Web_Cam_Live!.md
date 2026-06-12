---
title: "Creative Web Cam Live!"
date: 2012-05-23
forum: Hardware
---

### Post by altella on 2012-05-23
Hello all;
I have a very old Creative Live! Webcam, and I want it to work with Skype or other programs under Xubuntu.
I have tested it With the "Cheese" program and with Skype, installed from the 10.04 Ubuntu package available from Skype website.
The web cam does not work in either of them. Running in the console "lsusb" command I obtain the following output:
 
alberto@alberto-desktop:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro 
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305 
alberto@alberto-desktop:~$ 

How could I make my camera to work?
Gspca modules do not appear in Synaptic...
 Thank you all in advance.
Regards,

---

### Post by mörgæs on 2012-05-23
How does it work in a live boot of 12.04?
Guvcview (in 12.04 - not in earlier releases - is also worth trying).

---

### Post by altella on 2012-05-23
Cheese is a very simple program also.
Somehow the camera is detected but it seems it does not have the proper drivers...
I want it to use with Skype.

---

