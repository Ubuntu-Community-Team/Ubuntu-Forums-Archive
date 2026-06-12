---
title: "CD/DVD drive disappeared from /dev/"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by Mad Marty on 2005-07-17
Hi all,

I'm just getting to grips with Ubunutu, and have managed to find out answers to most of my questions, but this one has me foxed.

I install Ununtu from a CD I burnt, as a server.  This meant I could add on what I wanted, rather than remove what I didn't.  It installed fine - no problems there.

However, I have just started to get Ogle working, when I discovered that my DVD/CD drive is not showing up in /dev/.  hdb is there (which is my hard disk).

I know the drive works: I installed the base packages with it!  Can I get Ubutu to see it however?

```
$ ls /dev/hd*
/dev/hdb  /dev/hdb1  /dev/hdb2  /dev/hdb3
```

This is a snipped version of the dmesg output.  I can't see anything obvious.

```
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:02.5[A] -> GSI 11 (level, low) -> IRQ 11
SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
    ide0: BM-DMA at 0xa400-0xa407, BIOS settings: hda:DMA, hdb:DMA
Probing IDE interface ide0...
ide0: Wait for ready failed before probe !
hdb: Maxtor 6E040L0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdb: max request size: 128KiB
hdb: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 p3
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 489972k swap on /dev/hdb2.  Priority:-1 extents:1
EXT3 FS on hdb1, internal journal
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA
]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
```


Any help would be gratefully appreciated

---

