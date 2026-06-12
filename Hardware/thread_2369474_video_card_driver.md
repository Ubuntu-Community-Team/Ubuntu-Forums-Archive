---
title: "video card driver"
date: 2017-08-22
forum: Hardware
---

### Post by tazzycoolman on 2017-08-22
hi  i try to find driver for ati radeon grapics card for my laptop

```
*-display                 
       description: VGA compatible controller
       product: RV635/M86 [Mobility Radeon HD 3650]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:c0000000-cfffffff ioport:7000(size=256) memory:d2300000-d230ffff memory:c0000-dffff
```
please help me .. thanks

---

### Post by vasa1 on 2017-08-23
Moved to its own thread.

---

### Post by Yellow Pasque on 2017-08-23
> driver=radeon
The driver is already loaded.

---

### Post by mastablasta on 2017-08-24
this card is well supported and as mentioend driver is already loaded as it is part of the kernel. what is the issue?

abotu radeon driver: [https://www.x.org/wiki/radeon/](https://www.x.org/wiki/radeon/)
features: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

