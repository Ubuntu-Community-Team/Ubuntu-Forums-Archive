---
title: "Can't set brightness on Acer Aspire Z3770"
date: 2013-06-30
forum: Hardware
---

### Post by temmokan on 2013-06-30
Hello,

I am using Ubuntu 12.04 on Acer Aspire Z3770. The problem is it doesn't change screen brightness, regardless of settings. Slider in brightness settings in system settings, xbacklight, direct output to /sys/class/backlight/acpi_video0/brightness -- nothing works, brightness doesn't change.

In case that could be of help:

lshw -C display

```
  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical ID: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: IRQ:16 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f7000000-f707ffff
*-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical ID: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: IRQ:51 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

lsb_release -a

```
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

```

uname -a

```
Linux leo-home 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:43:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

I would appreciate any advice.

Thanks!

---

