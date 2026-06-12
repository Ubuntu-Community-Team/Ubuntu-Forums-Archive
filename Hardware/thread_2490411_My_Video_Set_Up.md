---
title: "My Video Set Up"
date: 2023-09-02
forum: Hardware
---

### Post by kinddolphin8827 on 2023-09-02
[SIZE=4][FONT=arial]Listed below are the specifications of   my video subsystem.

```
sudo lshw -c video
*-display
description: VGA compatible controller
product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:05:00.0
logical name: /dev/fb0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
resources: irq:48 memory:d0000000-dfffffff memory:efd20000-efd3ffff ioport:c000(size=256) memory:c0000-dffff
```
[/FONT]
```
lspci -nnk | grep -i vga -A2
05:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] [1002:68f9]
    Subsystem: Hightech Information System Ltd. Radeon HD 5470 [1787:3000]
    Kernel driver in use: radeon

```
[/SIZE]

---

### Post by ajgreeny on 2023-09-03
What do you wish us to do with this information? 
Do you have a problem of some sort?

---

