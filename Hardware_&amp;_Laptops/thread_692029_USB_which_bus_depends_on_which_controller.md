---
title: "USB: which bus depends on which controller?"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by donmiguel on 2008-02-09
Hey guys. I'd like to know how i find out, which bus depends on which controller:

I have following info and do not know how to put it together: 

```

$ lspci | grep USB
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller

$ lsusb 
Bus 004 Device 004: ID 046d:xxxx Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 046d:xxxx Logitech, Inc. 
Bus 002 Device 006: ID 07b8:xxxx D-Link Corp. 
Bus 002 Device 005: ID 058f:xxxx Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

One would think that 03.1 is Bus 001 etc. but how could I be sure?

---

