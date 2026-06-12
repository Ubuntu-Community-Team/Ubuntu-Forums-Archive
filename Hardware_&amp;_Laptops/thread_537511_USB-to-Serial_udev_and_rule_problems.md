---
title: "USB-to-Serial udev and rule problems"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by Fezzler on 2007-08-29
I have a Belkin F5U109 USB-to-Serial cable I am using with Ubuntu 7.04.

I use it to connect and old Tandy Model 100 to Ubuntu PC.  I download Tandy programs to the PC and us a program called Desklink plus for Linux ([http://bitchin100.com](http://bitchin100.com)) in Terminal on the PC and a program on the M102 to transfer files.  The program is ./dl

It all works, but I want to set up a udev rule to make ./dl load automatically when the cable is plugged in.  Can't get it to work.

My 10-local.rules in /etc/udev/rules.d read:
SUBSYSTEMS=="usb",ATTRS{product}=="Belkin Components",KERNEL=="ttyUSB*",NAME="desklink",SYMLINK+="usbdevices/desklink",GROUP="christopher",RUN+="/dlplus/./dl /dev/ttyUSB0"

My fstab line for the cable reads:
/dev/desklink   /media/desklink usbdevfs defaults            0     0

I'm lost.  I really could uses a step-by-step instruction.  How does one mount ttyUSB0?

---

