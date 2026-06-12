---
title: "Installer can't detect hard drive"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by thecwin on 2005-12-18
The Ubuntu installer stops at the screen that says "Detecting Disks" and asks me to choose a driver. I flipped over to the second virtual terminal and checked dmesg...

```
hda: max request size 128KiB
hda: 0 sectors (0MB) w/6812KiB cache, CHS=0/0/55
hda: cache flushes supported
hda: INVALID GEOMETRY: 0 PHYSICAL HEADS?
hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error}
hda: task_no_data_intr: error=0x04 { DriveStatusError}
ide: failed opcode was: 0xea
hda: wcache flush failed
```

This drive is fully working, since I'm currently running Gentoo from it. I was trying to install ubuntu via netboot, if it matters...

lspci says my IDE interface is:
```
IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
```

When booted into Gentoo, this is what dmesg says (irrelevant stuff cut out):
```
SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
Probing IDE interface ide0...
hda: HITACHI_DK23EB-40, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 hda8 hda9 >
```

On the screen it presented to me about choosing a driver, I tried sis5513, but it didn't work. Any ideas? :)

---

