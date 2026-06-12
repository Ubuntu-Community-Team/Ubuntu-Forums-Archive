---
title: "Display Unclaimed - Lenovo SL500, Intel Mobile 4"
date: 2009-08-06
forum: Hardware
---

### Post by jhaensly on 2009-08-06
I have a novice question:  what driver should I use for the display below, and what's the best way to install it?  For the future, is there a list of recommended hardware-driver configurations?

I'm running Ubuntu 9.04 (x86-64) on a Lenovo SL500

```

$ uname -rv
2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009

$ lshw -C display

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

---

