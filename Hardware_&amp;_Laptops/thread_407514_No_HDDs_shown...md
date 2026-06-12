---
title: "No HDDs shown..??"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by icehammer on 2007-04-12
I have 2 HDDs, primary master and slave. And a DVD-ROM as Secondary Master.

Whenever i remove the DVD-ROM and connect another hard drive in place, ubuntu refuses to read any drive. GParted scanned all night but refused to show any drive connected.. why??

---

### Post by kidders on 2007-04-13
Hi there,

This sounds like a hardware problem to me. Are the hard disks & cables you're trying okay?

---

### Post by icehammer on 2007-04-14
Absolutely, everything works perfectly, given that the HDDs connected are the same as they were during ubuntu install. 

If i try to change my slave HDD, or simply remove it.. ubuntu refuses to show any drive as mounted.
GParted shows that there are no HDDs connected at all!!!

---

### Post by kidders on 2007-04-14
Hmmm... The first place to look is your system logs (just in case you haven't done so already). Also, to be honest, I wouldn't trust Gparted to do *anything* right hehe ... try something a little more basic (like cfdisk, for instance).

The other thing worth checking is that your disks' jumpers are all set properly, and that your BIOS is correctly configured.

---

### Post by icehammer on 2007-04-15
i'll try cfdisk.. bt jumpers are set correctly..

---

### Post by kidders on 2007-04-15
> **icehammer said:**
> i'll try cfdisk.. bt jumpers are set correctly..


It really is worth taking a look at your system logs first. If they don't describe your hard disks the way you expect them, no partitioner will see them. For instance, an inspection of _my_ **dmesg** log reveals...

```
...
...
SCSI subsystem initialized
libata version 2.20 loaded.
...
...
sata_nv 0000:00:0e.0: version 3.3
...
...
ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001d400 irq 20
ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001d408 irq 20
ata3: SATA max UDMA/133 cmd 0x00000000000109e0 ctl 0x0000000000010be2 bmdma 0x000000000001c000 irq 23
ata4: SATA max UDMA/133 cmd 0x0000000000010960 ctl 0x0000000000010b62 bmdma 0x000000000001c008 irq 23
...
...
Uniform CD-ROM driver Revision: 3.20
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
SCSI device sda: 976771055 512-byte hdwr sectors (500107 MB)
sda: sda1 sda2 sda3
SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
sdb: sdb1
...
...
```That tells me...[LIST]
[*]The proper drivers (sata_nv, sr_mod) are loading for me.
[*]My ATA interfaces are all being detected correctly.
[*]Ubuntu sees one optical drive and two hard disks (4 partitions).[/LIST]...so I know everything is as it should be. If you don't see something similarly reassuring (depending, of course, on how your own system is built), something fairly low-level is wrong. In theory, your system logs should help you determine what the problem might be.

---

