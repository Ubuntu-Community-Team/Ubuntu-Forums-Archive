---
title: "Intermittent Black Screen Using Intel HD Graphics 620"
date: 2018-01-09
forum: Hardware
---

### Post by anbuck2 on 2018-01-09
I have a Dell i5378-7171GRY laptop with an Intel HD Graphics 620 video card. A few times a day my external monitor goes blank for a few seconds and then comes back. It happens most frequently when the computer is under heavy CPU load and the fan turns on. It only affects the external monitor. The built in display stays on the whole time. Another symptom that may or may not be related is that If I attempt to share my screen using WebRTC, the screen share is black except for the mouse icon. The mouse icon is there and I can see it moving around. The screen sharing issue affects both the internal and external displays.

```

~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)

```

```

~$ lshw -C video
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:277 memory:d0000000-d0ffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff

```

```

~$ modinfo i915
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
firmware:       i915/bxt_dmc_ver1_07.bin
firmware:       i915/skl_dmc_ver1_26.bin
firmware:       i915/kbl_dmc_ver1_01.bin
firmware:       i915/skl_guc_ver6_1.bin
firmware:       i915/kbl_huc_ver02_00_1810.bin
firmware:       i915/bxt_huc_ver01_07_1398.bin
firmware:       i915/skl_huc_ver01_07_1398.bin
srcversion:     F27B28CF28ECAE28997AF44

```

---

### Post by anbuck2 on 2018-01-30
The screen sharing issue was resolved by switching from Wayland to Xorg, but the problem of the external monitor going black intermittently persists.

---

