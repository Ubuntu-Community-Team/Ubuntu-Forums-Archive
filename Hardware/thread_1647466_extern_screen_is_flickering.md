---
title: "extern screen is flickering"
date: 2010-12-17
forum: Hardware
---

### Post by konbs on 2010-12-17
Hey Guys,

I just got an new external screen for my Thinkpad T510. Unfortunately, the external screen is flickering on Ubuntu 11.4. I'm using the nvidia driver.

```

kon@kon-laptop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GT218 [NVS 3100M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:cd000000-cd07ffff

```

I've tried to disable the visual effects - same issue. Do you have any suggestions? Thanks in advance!

Kon

---

