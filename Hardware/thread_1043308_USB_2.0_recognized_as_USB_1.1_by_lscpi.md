---
title: "USB 2.0 recognized as USB 1.1 by lscpi"
date: 2009-01-18
forum: Hardware
---

### Post by mgol on 2009-01-18
I've got ASUS A6B00U notebook (see [https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6B00U](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6B00U)). I use Ubuntu 8.04.1 (Hardy Heron).

lscpi output tells me that three of my four USB ports are 1.1 version, instead of proper 2.0:
```

$ lspci | grep USB
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller

```

It should show 4x USB 2.0. Why doesn't it?

---

### Post by Chemical Imbalance on 2009-03-14
Same here:

> 00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)



Asus M3N78 PRO mobo with *all* usb 2.0 hubs

---

