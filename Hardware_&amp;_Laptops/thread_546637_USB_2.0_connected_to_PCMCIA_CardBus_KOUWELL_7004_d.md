---
title: "USB 2.0 connected to PCMCIA CardBus KOUWELL 7004 doesn't work"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by shyma on 2007-09-09
Hi Ubuntu, 

I need your help. I have got PCMCIA CardBus (2 x USB 2.0 and 2 FireWire ports). I have recently installed the last version of Ubuntu (kernel version 2.6)  And I am trying to connect my USB devices to it, none of them works properly. For example i take the USB flash (1GB) made by Corsair:

My trials to solve/recognize the problem:

 - When i do *mount*, i don't see any *sdb *devices, sda - is the partition to my hard drive
 - When i do *dmesg*, i don't see any particular errors with the device, it just doesn't work
 - When I launch Ubuntu with the USB flash connected - it seem to recognize the USB device, the led on USB is blinking and then stays lighted forever. When I do *lsusb*, *usbview*, it shows me that  device exists, but unfortunately no */dev/sdXN* identifier.

What should i do, anybody can help?

thanks,
Volodya

---

