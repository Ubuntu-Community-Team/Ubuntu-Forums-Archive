---
title: "Dual screen with laptop and TV, works in Windows 7 not in Ubuntu 11.04"
date: 2011-05-21
forum: Hardware
---

### Post by eekfonky on 2011-05-21
I have connected my laptop to a TV via an S-Video lead (as my TV is old) to watch movies etc. from the laptop. I get a picture with Windows 7 but not with Ubuntu 11.04, I only get a black screen. I have tried switching off the laptop screen and lowering the resolution to suit the TV but nothing. Ubuntu knows the TV is there and has selected the correct resolution but still no picture?
```

sudo lshw -C display; cat /etc/lsb-release
```

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f4000000-f40fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4100000-f41fffff
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```

---

