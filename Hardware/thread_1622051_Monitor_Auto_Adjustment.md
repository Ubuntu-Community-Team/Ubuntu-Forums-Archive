---
title: "Monitor Auto Adjustment"
date: 2010-11-15
forum: Hardware
---

### Post by shashanksingh on 2010-11-15
I have a samsung 22' LCD monitor which has a resolution option of 1360x768 (16:9).

But in that configuration the screen shifts a bit towards left each time the monitor restarts and needs an auto adjust from the monitor settings. I also have Windows 7 which shows maximum resolution of 1024x768.

Working on 1024x768 doesn't need any adjustment.

an lshw gives me this:


*-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:fea80000-feafffff ioport:ec00(size=8) memory:d0000000-dfffffff memory:fe900000-fe9fffff

---

