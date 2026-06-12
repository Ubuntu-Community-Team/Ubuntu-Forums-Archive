---
title: "Help With Graphics Card"
date: 2017-03-05
forum: Hardware
---

### Post by traveldaemon on 2017-03-05
I'm new to Linux, and I'm having trouble figuring some things out. The Laptop I'm using has an Nvidia card as well as an Intel card. I believe that the computer uses the Intel (On-Board) card when I'm running games (although I don't even know how to check to confirm this). I want it to use the Nvidia card. I don't even know if I have the drivers I need for the Nvidia card. Basically I want to know if I have the right drivers, if my computer is using the Nvidia card when I run games, and if not, how I make it use it. The only seemingly relevant information I could find came from the lshw command.

*-display UNCLAIMED
                description: 3D controller
                product: GM108M [GeForce 940MX]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff



And 


       *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:277 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff


This is the information displayed on my system details page.

Ubuntu 16.04 LTS
Memory 11.7 GiB
Processor Intel Core i7-7500U CPU @ 2.70 GHz x 4
Graphics Intel Kabylake GT2
OS Type 64-bit


Any help is appreciated.

---

### Post by mastablasta on 2017-03-06
to be able to use nVidia card you need to use bumblebee. [SIZE=2]https://wiki.ubuntu.com/Bumblebee
[/SIZE]

---

