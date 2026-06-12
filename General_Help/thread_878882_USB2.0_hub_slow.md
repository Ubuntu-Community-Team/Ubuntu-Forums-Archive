---
title: "USB2.0 hub slow"
date: 2008-08-03
forum: General Help
---

### Post by jubilee0824 on 2008-08-03
Hi evreyone,

I have recently noticed my USB2.0 flush memory, attached to a no-brand USB2.0 hub, is working slow.

So I logged onto Ubuntu (I usually use Xubuntu), and found out that the flush memory was connected by "USB2.0 at 12Mbps",

Now I plug the same flush memory directly to any of my laptop USB ports, (it is Acer Aspire 1350 with VIA chip), the flush memory works as "USB2.0 at 480Mbps" and much faster. So I guess it is not a driver or kernel or BIOS issue.

Thus I'm assuming that the USB2.0 hub is operating at low-speed for some reason. Is its being a bass-powered hub (no external power adapter) a problem?

I have attached the output from lsusb. The last one seems to be my USB2.0 hub, whereas the second last entry is the flush memory attached to it.

Any help is appreciated, thanks!

> 
~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 012: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 


---

### Post by comwiz7 on 2008-08-03
A USB hub only has the power of one USB port and it divides it between the three. It's possible that your drive is not getting enough power especially if you have another USB device plugged into the hub.

---

### Post by jubilee0824 on 2008-08-03
hello comwiz7,
Yes, thats the very thing I was concerned with. But I only have one thumb drive plugged into this hub, and I highly double it requires the whole 400mA. Also does it onlt affect the speed? I mean the thumb drive is working fine, just too slow.
So I am suspecting that the hub itself is recognised as a 12Mbps device, rather than 480Mbps.

---

