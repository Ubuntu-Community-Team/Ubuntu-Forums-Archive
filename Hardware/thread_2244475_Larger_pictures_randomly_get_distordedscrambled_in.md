---
title: "Larger pictures randomly get distorded/scrambled in Ubuntu 14.04"
date: 2014-09-16
forum: Hardware
---

### Post by Stannis_King on 2014-09-16
Sometimes larger pictures get distorted. It happens in Firefox and it happens in Image Viewer, but it seems to happen completely at random.

The weird part is, when a picture gets distorted in Firefox and I save it, it opens up distorted in Image Viewer. When I visit the picture link in Firefox later, if the cache is cleared, the picture appears normal.

I'm guessing this has something to do with either downscaling or graphics' drivers (**which is why I posted in Hardware**).

I tried disabling downscaling in Firefox, but I can't know if it's working or not, because the distortion happens randomly.

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516/M64-S [Mobility Radeon X2300] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company 6910p
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=64M]
    I/O ports at 4000 [size=256]
    Memory at d8400000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d8420000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
```

---

