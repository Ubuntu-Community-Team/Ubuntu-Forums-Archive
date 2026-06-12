---
title: "Power off USB harddrive"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by wildekek on 2006-06-27
I've got a USB harddrive which is used for backup purposes which i'd only like to be switched on when the backup process is running. I already have it spooling down, helped by the sdparm utility, but i'd like to turn off the USB power so the disk switches off, and the power light is off (so my friendly colleagues can see it is finished and ready to take home)

In order for it to switch off, i'd like to disable a port on the USB 2.0 PCI card that it is attached to, because disabling usb switches it completely off (tested on Win32). Disabling the entire USB card is also fine, since no other device is attached to it.

I tried the setpci command and was able to power the whole card down, with the "command=0" option but switching it on is a problem, since i can't seem to comprehend how the pci parameters work (and i did RTFM ;) ).

Anyone got an idea how to switch of this usb device from command line?

---

