---
title: "Dual Graphics - how change graphic card in Plasma KDE ?"
date: 2019-05-25
forum: Hardware
---

### Post by anderbuntu on 2019-05-25
Hi

I am using dual Graphics card in Plasma ( Kubuntu 18.04 ),  notebook with dual graphics i915 & ati
How to change as primary card my discrete ATI card in KDE ?
As you can see > modules  are loaded  ( I am using standard drivers that I got  with distro..)


[FONT=monospace][COLOR=#000000]modinfo -F filename `lshw -c video | awk '/configuration: driver/{print $2}' | cut -d= -f2`[/COLOR]
/lib/modules/4.18.0-20-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
/lib/modules/4.18.0-20-generic/kernel/drivers/gpu/drm/i915/i915.ko

[/FONT][FONT=monospace][COLOR=#000000]lshw -c video[/COLOR]
  *-display                  
       description: VGA compatible controller
       product: Park [Mobility Radeon HD 5430/5450/5470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:27 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
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
       resources: irq:26 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8) memory:c0000-dffff

FYI:
In Kinfocenter I see Opengl driver : Intel, not ati

Primary I am asking to change graphics for playing Videos in Plasma... ati should be better I guess

A.

[/FONT]

---

### Post by anderbuntu on 2019-05-26
So I had issues with scrambled video plying in VLC, even CPU was only on 20%. I was thinking that issue is video driver... (i915)
I fixed this with different player...
However   I am still curious how to change video driver in KDE Plasma.

---

### Post by anderbuntu on 2019-05-26
Also strange is that on my newer notebook ( Intel HD Graphics 520 ) VLC is playing fine...
Seems that VLC has some issue with playing on older HW.

A.

---

