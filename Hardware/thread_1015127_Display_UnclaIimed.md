---
title: "Display UnclaIimed"
date: 2008-12-18
forum: Hardware
---

### Post by darkcard on 2008-12-18
I have been trying to get my graphics card working properly, and I'm not sure what to do.

Dell Inspiron XPS
Ubuntu 8.10

I'm currently in low-graphics because i installed fglrx thinking maybe that was the problem, but look at me now I messed up my graphics settings. I'll figure out how to fix that back to what it was...

Anyway, when i do lshw i get(more than) this:

```
*-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display **UNCLAIMED**
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8

```

How do i get it to be claimed? How can I use it?

Thanks for helping.

---

### Post by darkcard on 2008-12-18
I hate to bump topics but this has been a problem of mine I have been having for my whole linux experiance and I'm sick of it. Can anyone help me at all?

---

### Post by camionrouge on 2008-12-19
Might be something here that could help.
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

