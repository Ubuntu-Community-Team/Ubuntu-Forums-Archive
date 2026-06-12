---
title: "Kwumsy/Kefeya P2 Pro Triple Portable Monitor"
date: 2022-12-30
forum: Hardware
---

### Post by massimo.paulin on 2022-12-30
Hi everyone,

I can't find a driver to make this device work on Ubuntu.

The same product is distributed by both Kwumsy and Kefeya, but appears to be exactly the same.

Can someone help me?
A thousand thanks!

---

### Post by massimo.paulin on 2022-12-30
[COLOR=#000000][FONT=Ubuntu]sudo lshw -c video[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
*-display[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]product: Skylake GT2 [HD Graphics 520][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]physical id: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]bus info: pci@0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]logical name: /dev/fb0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]version: 07[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]configuration: depth=32 driver=i915 latency=0 resolution=1920,1080[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]resources: irq:131 memory:d1000000-d1ffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]*-display[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]description: Display controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / Radeon 520 Mobile][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]vendor: Advanced Micro Devices, Inc. [AMD/ATI][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]bus info: pci@0000:01:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]version: 81[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]capabilities: pm pciexpress msi bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]configuration: driver=radeon latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]resources: irq:130 memory:c0000000-cfffffff memory:d0000000-d003ffff ioport:e000(size=256) memory:d0040000-d005ffff[/FONT][/COLOR]

---

