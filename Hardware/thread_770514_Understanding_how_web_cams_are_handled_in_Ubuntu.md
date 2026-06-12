---
title: "Understanding how web cams are handled in Ubuntu"
date: 2008-04-27
forum: Hardware
---

### Post by adwallum on 2008-04-27
Hi 

I've got a 303b Z-Star Microelectronics Corp. ZC0303 WebCam. The driver is entitled vm303 in Windows but there appears not to be an equivalent for linux, i.e. not a '303' driver although there is a linux '301' driver.

Ekiga found the webcam, applied the '301' driver to it and it works. Skype, Cheese and Camorama don't recognise it and therefore don't run the webcam.

How can I get Skype, Cheese and Camorama to use the 301 driver? 

(I appreciate that this might get technical and that I'm new. I am willing to learn however.)

Camorama throws the following error message:

> Could not connect to video device (/dev/video0). Please check connection.

lsusb gives:

> Bus 003 Device 005: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 003 Device 004: ID 18e3:9101  
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 043d:0065 Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  


The ZCO303 webcam is plugged into the Genesys Logic hub.

Do I need a symlink to point /dev/video0 to the web cam? If so could somebody help formulate the command for me please.

---

### Post by adwallum on 2008-05-03
bump please

---

