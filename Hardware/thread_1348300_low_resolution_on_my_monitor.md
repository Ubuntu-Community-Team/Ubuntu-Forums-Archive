---
title: "low resolution on my monitor"
date: 2009-12-07
forum: Hardware
---

### Post by some1_genius on 2009-12-07
Hi ubuntu community, glad to talk to u.
This monitor is going to drive me crazy. Spatially with ubuntu 9.10 that doesn't have a xorg.conf file.
Monitor is HP L1706
when i try other monitors they work perfectly and when i try my monitor in other machine (but with the same graphics adapter) i have the same problem.
this is the case with the latest intel driver for the graphics card but when i install an older version of it (xserver-xorg-video-intel-2.4) i can run higher screen resolutions but with a bad performance and no compiz. What makes me think that there might be a conflict between the graphics card adapter and my monitor.
none of the ways described [here]("https://wiki.ubuntu.com/X/Config/Resolution") work with me.
can u provide some help cuz now i stuck at 800x600 screen resolution:-|.


*-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfd00000-cfd7ffff ioport:1800(size=8) memory:e0000000-efffffff(prefetchable) memory:cfd80000-cfdbffff

---

