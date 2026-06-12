---
title: "Nvidia 1660ti"
date: 2019-07-08
forum: Hardware
---

### Post by leonida95 on 2019-07-08
Good morning everyone,
I am trying to install my nvidia 1660 Ti but I can't. Ihave 2 graphics card, an intel and the Nvidia one. I am a NOOB using Ubuntu but I'd like to understand how to activate my nvidia gpu. I installed nvidia 367

 *-display UNCLAIMED              description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:a4000000-a4ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128) memory:a5000000-a507ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:169 memory:a3000000-a3ffffff memory:80000000-8fffffff ioport:6000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Edit:
It seems the only way was to manually install the drivers from the command line, now that i've installed the right drivers everithing seems working fine...

 *-display                 
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:176 memory:a4000000-a4ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128) memory:a5000000-a507ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:169 memory:a3000000-a3ffffff memory:80000000-8fffffff ioport:6000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

