---
title: "Funky Disk Problem after 9.10RC upgrade: sdb and sdc partitions not found"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by jwagner95 on 2009-10-28
After upgrading to the RC of 9.10 following [these directions]("https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu"), I can no longer access my two secondary sata drives sdb and sdc after bootup.  Both are 750GB drives with a single partition.  I can, however, unplug the drives and hotplug them and have them available at /dev/sdd1 and /dev/sde1.  This is a bit annoying for internal drives though.  Anyone have any ideas why these would fail to show up in the device tree on boot? Relevant info follows; feel free to ask for more.

Thanks in advance,
Jonathan



```
jonathan@jonathan-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf193f193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux
``````
jonathan@jonathan-desktop:~$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf193f193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux

``````
jonathan@jonathan-desktop:~$ uname -a
Linux jonathan-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
``````

jonathan@jonathan-desktop:~$ dmesg | grep -nC 5 sdb
711-[    1.380720] ata2.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 31/32)
712-[    1.400302] ata5.01: configured for UDMA/33
713-[    1.420620] ata2.00: configured for UDMA/133
714-[    1.420702] scsi 1:0:0:0: Direct-Access     ATA      ST3750330AS      SD15 PQ: 0 ANSI: 5
715-[    1.420819] sd 1:0:0:0: Attached scsi generic sg1 type 0
716:[    1.420840] sd 1:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
717:[    1.420875] sd 1:0:0:0: [sdb] Write Protect is off
718:[    1.420877] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
719-[    1.420884] scsi 2:0:0:0: Direct-Access     ATA      ST3750330AS      SD15 PQ: 0 ANSI: 5
720:[    1.420897] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
721-[    1.420978] sd 2:0:0:0: Attached scsi generic sg2 type 0
722-[    1.421006] sd 2:0:0:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
723:[    1.421012]  sdb:
724-[    1.421041] sd 2:0:0:0: [sdc] Write Protect is off
725-[    1.421043] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
726-[    1.421065] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
727-[    1.421150]  sdc:
728-[    1.431772] ata4: SATA link down (SStatus 0 SControl 300)
729-[    1.432785] scsi 4:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P55 PQ: 0 ANSI: 5
730:[    1.434890]  sdb1
731:[    1.435046] sd 1:0:0:0: [sdb] Attached SCSI disk
732-[    1.437806]  sdc1
733-[    1.437993] sd 2:0:0:0: [sdc] Attached SCSI disk
734-[    1.438006] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
735-[    1.438013] Uniform CD-ROM driver Revision: 3.20
736-[    1.438063] sr 4:0:1:0: Attached scsi CD-ROM sr0
``````
jonathan@jonathan-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdc
```

---

### Post by jwagner95 on 2009-10-28
Never mind.  I was using these drives in a mirrored RAID configuration at one point in their history.  Apparently I forgot to erase the metadata on the drives and the Kubuntu's now smart enough to automatically set up dmraid for me based on said metadata.  Sorry for wasting bandwidth.  All is well now.  Nothing to see here; move along.

---

