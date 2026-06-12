---
title: "Optical drive - Ubuntu Feisty - HP Compaq 6710b"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by J-Red on 2007-07-10
Hey, I'm currently working on getting my optical drive in my HP Compaq 6710b to work, and with someone's help I finally found it in lshw. When i found it, it doesn't look like its supposed to, and is missing alot of information. Also, it says it is "UNCLAIMED". I checked my BIOS and it said that the optical drive is enabled.

My lshw output(only concerning the optical drive):

```
        *-ide UNCLAIMED
             description: IDE interface
             product: Mobile IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:40c0-40cf irq:10

```

What it should look like:

```
*-ide
description: IDE interface
product: Mobile IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@00:1f.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=PIIX_IDE latency=0
resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:40c0-40cf irq:16
*-ide
description: IDE Channel 0
physical id: 0
bus info: ide@0
logical name: ide0
clock: 33MHz
*-cdrom
product: TSSTcorpCD/DVDW TS-L632M
physical id: 0
bus info: ide@0.0
logical name: /dev/hda
capacity: 2744MB
capabilities: packet
```

to me, it looks like the optical drive is using whatever "IDE", and it doesn't seem to be working properly on mine. How would I go about changing the "IDE interface" so that it is no longer "UNCLAIMED"?

---

### Post by J-Red on 2007-07-10
Hey, I've found a solution. My brother has been posting everything to do with this laptop on his blog ([http://www.blaise.ca/blog/](http://www.blaise.ca/blog/)), in one of his blog posts, someone told me to do a sudo modprobe piix That worked fine and now the drive works :)

---

