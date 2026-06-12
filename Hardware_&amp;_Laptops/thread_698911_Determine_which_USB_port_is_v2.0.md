---
title: "Determine which USB port is v2.0"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by x1a4 on 2008-02-16
Hi,

I need confirmation that my printer is connected to my USBv2 port.
lsusb gives me this: 
```

*<snip>*
Bus 003 Device 004: ID 04a9:10c2 Canon, Inc. 
*<snip>*

```
lspci gives me this: 
```

*<snip>*
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
*<snip>*

```

Since the printer (Canon) is connected to Bus 003 Device 004 and USBv2 is on pci 3.3 I gather that that's bus 3 dev 4.  Am I correct?

---

