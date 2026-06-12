---
title: "External monitor (second) flickering to black"
date: 2022-04-23
forum: Hardware
---

### Post by Briga on 2022-04-23
Hi, I did a fresh install of 22.04 I have an issue with the second monitor, the external one.
After a while it starts switching off and on randomly for a second to some of them. The intervals look casual to me. When it does it frequently the second monitor is useless since it's continuous (on and off 10 times a minute).  

This is my video card on Huawei Mate D15:

03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series] [1002:15d8] (rev c2)

or

  *-display                 
       description: VGA compatible controller
       product: Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: /dev/fb0
       version: c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=1920,1080
       resources: irq:41 memory:b0000000-bfffffff memory:c0000000-c01fffff ioport:1000(size=256) memory:c0500000-c057ffff

This is my xrandr

Screen 0: minimum 16 x 16, current 3840 x 1080, maximum 32767 x 32767
XWAYLAND1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 310mm x 170mm
   1920x1080     59.96*+
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77  
XWAYLAND2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     59.88*+
   1440x1080     59.87  
   1400x1050     59.86  
   1280x1024     59.76  
   1280x960      59.79  
   1152x864      59.78  
   1024x768      59.68  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.85  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.20  
   320x200       58.96  
   1600x900      59.82  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.45  
   720x400       59.55  
   640x350       59.77

The freq is slighttly different from 
[ATTACH=CONFIG]290325[/ATTACH]

Any idea on how to troubleshoot it?

Thanks

---

### Post by Briga on 2022-04-24
Bit of extra info. 
I am not sure but the first black screen (or screen going off) may happen along with this line in dmesg:

[ 1837.111540] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7


and that's despite there is no hibernation happening (the computer is in use, lid open).

EDITED ---
I don't think it's related, it happened without that entry.

---

### Post by him610 on 2022-04-24
How did the external monitor behave when you were using LTS 20.04.4? If external monitor performance was satisfactory on 20.04.4 then you can eliminate hardware issues. 
If not satisfactory then 
  Check your external monitor cable connections.
  Try replacing the monitor's external cable.

If consistent monitor performance is important then you might consider falling back to LTS 20.04.4 until first point release of LTS  22.04 is released.

---

### Post by Briga on 2022-04-24
> **him610 said:**
> How did the external monitor behave when you were using LTS 20.04.4? If external monitor performance was satisfactory on 20.04.4 then you can eliminate hardware issues. 


Indeed it was working fine.

> **him610 said:**
> 
If consistent monitor performance is important then you might consider falling back to LTS 20.04.4 until first point release of LTS  22.04 is released.

Well that would be the last resort ... but of course if nothing else works I'll downgrade (and file a bug). Hopefully there is something I can do or a workaround suggested by someone with more knowledge than me.

---

