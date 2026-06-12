---
title: "Hard drive failure.  Bad superblock, short read.  Can I salvage my data?"
date: 2010-05-10
forum: Hardware
---

### Post by davidshere on 2010-05-10
I've read several tutorials for FS recovery.  I have successfully performed several.  This one has shoved me into a wall.  Here's what I can and can't do:

```

david@thebone:/$ sudo e2fsck /dev/sdd1
[sudo] password for david:
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd1
Could this be a zero-length partition?
david@thebone:/$ mke2fs -n /dev/sdd1
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61054976 inodes, 244190000 blocks
12209500 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

david@thebone:/$ sudo e2fsck -f -b 32768 -B 4096 /dev/sdd1
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd1
Could this be a zero-length partition?
david@thebone:/$

```

One thing I have not tried is described on this page: [http://linuxgazette.net/issue32/tag_superblock.html](http://linuxgazette.net/issue32/tag_superblock.html)

[I]In a particularly bad case you can try mke2fs -S (make superblocks and group descriptors only). This is described in the man page --- and is for "last ditch" efforts only. 
[/I]

I also get nothing when I do this:
```
david@thebone:/$ sudo fdisk -l /dev/sdd
david@thebone:/$
```
... is the partition really gone?

I've found this in my dmesg:

```

[   43.893426] sata_via 0000:00:0d.0: version 2.3
[   43.893465] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   43.893581] sata_via 0000:00:0d.0: routed to hard irq line 12
[   43.895109] scsi2 : sata_via
[   43.896235] scsi3 : sata_via
[   43.897836] scsi4 : sata_via
[   43.897952] ata3: SATA max UDMA/133 port i16@0xdc00 bmdma 0xcc00 irq 12
[   43.897957] ata4: SATA max UDMA/133 port i16@0xd800 bmdma 0xcc08 irq 12
[   43.897961] ata5: PATA max UDMA/133 port i16@0xd400 bmdma 0xcc10 irq 12
[   49.277289] ata3: port is slow to respond, please be patient (Status 0x80)
[   53.892705] ata3: device not ready (errno=-16), forcing hardreset
[   59.437208] ata3: port is slow to respond, please be patient (Status 0x80)
[   63.932739] ata3: COMRESET failed (errno=-16)
[   69.497217] ata3: port is slow to respond, please be patient (Status 0x80)
[   73.932823] ata3: COMRESET failed (errno=-16)
[   79.477327] ata3: port is slow to respond, please be patient (Status 0x80)
[  108.908107] ata3: COMRESET failed (errno=-16)
[  113.933123] ata3: COMRESET failed (errno=-16)
[  113.933171] ata3: reset failed, giving up
[  114.262802] ata4: SATA link down (SStatus 0 SControl 310)
[  114.463844] Driver 'sd' needs updating - please use bus_type methods

```

Any suggestions will be greatly appreciated.

---

### Post by davidshere on 2010-05-10
I powered down the machine, reseated the SATA controller card, both sides of the data cable, and the power cable to the drive.  This seems to have solved the problem.

---

