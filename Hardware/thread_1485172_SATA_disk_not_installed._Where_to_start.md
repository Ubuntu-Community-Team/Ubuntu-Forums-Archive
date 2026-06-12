---
title: "SATA disk not installed. Where to start ?"
date: 2010-05-16
forum: Hardware
---

### Post by Remilegentil on 2010-05-16
Hi everybody ! 

This is my first post here, and although not completely a newbie with Linux, I'm having a hard time with hardware. 

I have a 1Tb SATA disk that I don't know how to mount with Ubuntu, although it worked perfectly yesterday, in the old times where I used Windows. Since my motherboard is quite old, it has no SATA port, I'm using a PCI card to connect it. 

So... Where to start ? The SATA card seems to be recognized, but I don't see any /dev/sdx anywhere, or any disk appearing in the Administration/Disk Utility

Here are some details that could help you : 
* I'm using Ubuntu 10.04

* This is what lspci tells me :
00:09.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

* This is what concerns my SATA card, when I ask lshw :
        *-storage
             description: Mass storage controller
             product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
             vendor: Silicon Image, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list rom
             configuration: driver=sata_sil latency=32
             resources: irq:17 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) memory:dffffe00-dfffffff memory:dff00000-dff7ffff(prefetchable)

Thanks all for your kind help !!!!

---

### Post by Remilegentil on 2010-05-17
Solved the problem, but I don't really know why. After reading many forums, and wasting a lot of time, I unplugged my disk, removed my PCI card, cleaned some dust, reconnected everything, and it worked ! 

:)

---

