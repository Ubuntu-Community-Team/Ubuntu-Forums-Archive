---
title: "how to setup graphic card? for Nvidia Geforce 750M"
date: 2014-07-28
forum: Hardware
---

### Post by hinaimran-mehr on 2014-07-28
Hi,
I tried to install a proper driver for my graphic card using this tutorial [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) but ended up screwing up as my desktop was lost. So i returned back after much struggle to additional drivers and got NVIDIA binary driver -version 340.24 from nvidia 340 (open source). The problem is that the grpahics quality is very bad and the screen transfers when i for example switch between browser pages or various windows i get blank white pages for quite some time, until i refresh the window. My card specification is as follows: 

 *-display               
       description: 3D controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:52 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:5000(size=64)

how can i fix this without screwing up my computer? I have ubuntu 14.04 64 bit. My computer is Acer Aspire-V3-772

---

### Post by hinaimran-mehr on 2014-07-28
no reply yet :(

---

