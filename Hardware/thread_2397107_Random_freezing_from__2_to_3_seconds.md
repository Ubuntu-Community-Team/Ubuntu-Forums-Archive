---
title: "Random freezing from  2 to 3 seconds"
date: 2018-07-25
forum: Hardware
---

### Post by prismctg on 2018-07-25
My system is randomly freezing from 2 to 3 seconds.  Keyboard, display , mouse cursor even audio stop responding in those time ! Although there is no problem when I use windows. Recently I upgraded the system from 16.04 to 18.04, but still the problem persists. I think the graphics driver is the main culprit, although I am not sure. I already tried to fix from some posts ([Link 1]("https://askubuntu.com/questions/835111/ubuntu-16-04-seemingly-random-freezing-on-amd-system"), [link 2]("https://askubuntu.com/questions/945895/solution-to-intel-graphics-screen-tearing-flickering-causes-excessive-fan-use"), [link 3]("https://unix.stackexchange.com/questions/360709/how-to-blacklist-amdgpu"), [link 4]("https://askubuntu.com/questions/696681/ubuntu-14-04-lts-screen-freezing-frequently") ) I am using Dell Inspiron N5442 , cpu :  4th Generation Intel(R) Core(TM) i3-4005U , gpu: AMD Radeon(TM) HD R5 M240 2GB DDR3 . 

Here is my current ```
lshw -c video
```  output :

```
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
       resources: irq:47 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Jet XT [Radeon R5 M240]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:a0000000-afffffff memory:c0500000-c053ffff ioport:3000(size=256) memory:c0540000-c055ffff

```

Right now I am using xubuntu.

---

