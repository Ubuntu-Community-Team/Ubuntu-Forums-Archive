---
title: "Ubuntu 14.04 GPU driver options greyed out"
date: 2015-12-10
forum: Hardware
---

### Post by giannis_androulida on 2015-12-10
[COLOR=#111111][FONT=Ubuntu]Hey,

i just realized that under 'Additional Drivers' on my Ubuntu 14.04 laptop all GPU driver options are greyed out and the only one chosen is : "Continue using a manually installed driver"
The thing is i do not remember manually installing some GPU driver for my discrete graphics card on Ubuntu. How can i revert either to X-org open source driver or fglrx proprietary ?

In case it helps:

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]```
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
lspci -nn | grep '\[03'
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] [1002:6900]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
```[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

```

sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:b0400000-b07fffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display
       description: Display controller
       product: Topaz XT [Radeon R7 M260/M265]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:b0000000-b01fffff ioport:3000(size=256) memory:b0900000-b093ffff memory:b0940000-b095ffff

```[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Any help or info is much appreciated!
Screenshot : [http://imgur.com/jY1QUr5](http://imgur.com/jY1QUr5)
[/FONT][/COLOR]

---

