---
title: "Locate USB device in /dev"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by l2e on 2009-08-17
I just installed an OrigenAE IR221 IR module and need to start the irtrans daemon, but I need to know the exact device in /dev.  
 
I see the following when I run lsusb:
 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0471:060f Philips
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The device I am interested in is the fourth down (Philips).  The syntax for starting irtrans is:
 
irtrans /dev/(my usb device)
 
Unfortuantely, I don't know the device alias.  How do I find that out.
 
BTW - I running Jaunty.

---

