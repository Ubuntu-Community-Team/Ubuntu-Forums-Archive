---
title: "14:04: AMD HD6370M laptop graphics not supported"
date: 2015-06-26
forum: Hardware
---

### Post by Wickedmoney on 2015-06-26
Has anyone else had any luck? I've been stuck with the exact same issue, regarding the "Low-graphics-mode" prompt after installation. 

14.04LTS, updated.

I have tried quite a lot of ideas, going through the steps amd have posted, through additional drivers, through command prompt, always have purged everything before every attempt, mind blowing confusing and needin some help!

Anything else and i'll get to it asap

;)

```

xxx@xxx-Laptop:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] [1002:68e4]
    Subsystem: Hewlett-Packard Company Radeon HD 6370M [103c:163d]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]

```

```

xxx@xxx-Laptop:~$ sudo lshw -C display
[sudo] password for xxx: 
  *-display               
       description: VGA compatible controller
       product: Robson CE [Radeon HD 6370M/7370M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

```

---

### Post by Frogs Hair on 2015-06-26
Hello and Welcome 

Moved to new thread.

---

