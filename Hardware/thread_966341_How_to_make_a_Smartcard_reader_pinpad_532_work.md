---
title: "How to make a Smartcard reader pinpad 532 work"
date: 2008-11-01
forum: Hardware
---

### Post by mindless1973 on 2008-11-01
Hi,

I would like to use my Smartcard Reader: SCM pinpad 532 (SPR532) work under Hardy/64. 

I already downloaded and installed pcscd and the latest vendor driver from SCM.

However, my software still says that there is not CT-API interface found on my machine.

lsusb finds the device:
> 
marcus@pundit:/dev$ lsusb
Bus 002 Device 006: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04e6:e003 SCM Microsystems, Inc. SPR532 PinPad SmartCard Reader
Bus 001 Device 005: ID 04f9:0027 Brother Industries, Ltd 
Bus 001 Device 004: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC 
Bus 001 Device 001: ID 0000:0000  
marcus@pundit:/dev$ 


How could I proceed on troubleshooting? 

Thanks for help,

bye
me.

---

