---
title: "How do I troubleshoot monitor wake-up problems?"
date: 2016-06-04
forum: Hardware
---

### Post by marseille2 on 2016-06-04
My monitor is having trouble waking up after the computer goes to sleep. I'm at a loss here. I have to turn it on and off about 3 times before its functional. I didn't have this problem until sometime after I upgraded the kernel to 4.x. (I'm still on Trusty ... using hardware stack enablement). What am I doing wrong?

```
$ lshw -c video

  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:a000(size=256) memory:fe7f0000-fe7fffff memory:fe600000-fe6fffff
  *-display
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:d0000000-dfffffff memory:fe8c0000-fe8dffff ioport:b000(size=256) memory:fe8a0000-fe8bffff

```

---

### Post by X-RED_Tech on 2016-06-04
Have you tried the proprietary drivers already? You probably need them in 14.04. No need for additional drivers (and those cannot be installed anyway) in 16.04.

---

