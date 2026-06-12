---
title: "IBM Thinkpad X41 video issues"
date: 2011-05-16
forum: Hardware
---

### Post by derango on 2011-05-16
Hey there everyone,i am facing some problems on my X41 that I didn't use to have and is quite limiting. 
Back a few months ago I could run applications with 3d acceleration, I could watch flash videos fullscreen or run blender. Some time passed and I started facing problems on fullscreen flash videos - indeed I had some issues, installs, reinstalls with flash, so it is not a really good reference point - and eventually I couldn't run blender either, because it said some OpenGL requirements are not sufficient. I thought ok, probably the system is just old enough, today I reinstalled and on my surprise it hasn't solved any of the mentioned problems - which I thought a completely raw reinstall would do.
I am not really into Linux system dynamics - I am quite a new Linux user myself - but based on what has being said I theorize that the problem is with my graphic driver.

This is what lshw says about my VGA:

       *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:a0080000-a00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:a0000000-a003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:40200000-4027ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=4096) memory:a0100000-a01fffff ioport:40000000(size=2097152)


If anyone has got anything constructive to say please go ahead, I am at a school project right now and I really need to get Blender working again.
Thanks in advance, Derango

---

