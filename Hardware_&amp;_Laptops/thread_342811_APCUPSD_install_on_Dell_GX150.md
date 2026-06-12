---
title: "APCUPSD install on Dell GX150"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by bspratt on 2007-01-20
I have compiled and installed latest version of APCUPSD trying to communicate with ES-350 and this is the output of ./apctest:

when 2007-01-20 15:22:09 apctest 3.12.4 (19 August 2006) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest error termination completed
root@ubuntu-server61:/opt/apc/apcupsd-3.12.4/src# ./apctest
I run ./apctest 

Anyone have a clue on how to troubleshoot or get this guy going?  Thanks - Bill

---

