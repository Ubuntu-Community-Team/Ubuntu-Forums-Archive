---
title: "screen resolution problem"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by alan_18 on 2008-01-15
I just installed Gutsy 7.10 and my monitor is locked into either 640x480 or 800x600 resolution.  I'm pretty sure that I'm running in safe graphics mode.  When I go to edit the xorg.conf file, I see that my screen and driver are both labeled the "generic" type.

lshw results in:

*-display
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga cap_list
                configuration: latency=0

does anyone know of a compatible driver that i can use to fix this?  I also don't have any direct 3d support right now either.

---

### Post by johnleonard on 2008-01-15
Have you tried 

[HTML] sudo dpkg-reconfigure xserver-xorg[/HTML]

---

