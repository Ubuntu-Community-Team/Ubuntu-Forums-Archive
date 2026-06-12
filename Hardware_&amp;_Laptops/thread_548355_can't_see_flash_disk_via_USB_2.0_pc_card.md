---
title: "can't see flash disk via USB 2.0 pc card"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by mr bob on 2007-09-11
Hi,

I am trying to mount a flash disk (amongst other things) via a USB 2.0 pcmia card. I've searched the forum and tried these commands and also installed Usbview, which can see the flash disk. 

But the flash disk is not auto mounting and I don't what device to mount manually.


```

lsusb:

Bus 004 Device 002: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lspci | grep USB

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
06:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

```

Can anyone give me any ideas?

---

