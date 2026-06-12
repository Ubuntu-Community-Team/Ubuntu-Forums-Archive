---
title: "geniatech t328 dvb-t  ID 04b4:8613"
date: 2010-06-26
forum: Hardware
---

### Post by ulissess on 2010-06-26
hello i have usb-dvb geniatech t328 dvb-t

$ lsusb
Bus 005 Device 002: ID 04b4:8613 Cypress Semiconductor Corp. CY7C68013 EZ-USB FX2 USB 2.0 Development Kit

[http://wiki.debian.org/DeviceDatabase/USB](http://wiki.debian.org/DeviceDatabase/USB)

now it's supported .. how can i do work it?? thanks u

---

### Post by ulissess on 2010-06-27
if i recompile my kernel and i add 'usbtest' module can my dvb work? thanks..

---

### Post by davidmohammed on 2010-06-27
this [link]("http://code.google.com/p/r5000-for-linux/source/browse/trunk/README?r=8") mentions this device - does this help you?

---

### Post by ulissess on 2010-06-27
oh yes yesterday i just tried it.. with that firmware i change device in 
ID 0547:1002 Anchor Chips, Inc.
but if i use this command 
dmesg | grep dvb
i dont find nothing...

---

