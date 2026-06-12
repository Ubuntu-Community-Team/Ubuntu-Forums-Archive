---
title: "Fglrx?"
date: 2013-01-21
forum: Hardware
---

### Post by LinXNut on 2013-01-21
Hey guys I recently installed Ubuntu on my Compaq Presario CQ56 laptop. Everything is working perfectly. However after installing FGLRX for my Amd graphics, everything became slower and bloated. I went back to the "Additional Drivers" installation and noticed there was a "Post_Updates" installation. So I installed those, but it stopped in its tracks and said it could not finish installation. I rebooted my laptop, and now for my lspci I get this.
```
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at 90300000 (32-bit, non-prefetchable) [size=64K]
    Memory at 90200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: **fglrx_updates**, radeon
```So instead of it being "fglrx,radeon", now it's this above. It does seem to be much faster. Does this mean I have the fglrx driver in use now? 

Thanks,
LinXNut

---

### Post by Mark Phelps on 2013-01-21
That would be my guess, too -- but you should open a terminal and enter "fglrxinfo" and see what it says.

---

### Post by LinXNut on 2013-01-21
This is what I get with fglrxinfo?

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.11627 Compatibility Profile Context

```Thanks for the quick reply :D

---

