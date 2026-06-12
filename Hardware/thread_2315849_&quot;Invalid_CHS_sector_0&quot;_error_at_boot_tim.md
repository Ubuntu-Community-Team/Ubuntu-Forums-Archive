---
title: "&quot;Invalid CHS sector 0&quot; error at boot time"
date: 2016-03-03
forum: Hardware
---

### Post by Ashfaqur Rahman on 2016-03-03
Following error reports are showing at every time I try to boot.

```

[  132.811935] ata1.00: exception Emask 0x0 SAct 0x60000 SErr 0x0 action 0x6 frozen
[  132.811985] ata1.00: failed command: READ FPDMA QUEUED
[  132.812017] ata1.00: cmd 60/08:88:88:0b:00/00:00:00:00:00/40 tag 17 ncq 4096 in
[  132.812017]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  132.812089] ata1.00: status: { DRDY }
[  132.812110] ata1.00: failed command: READ FPDMA QUEUED
[  132.812141] ata1.00: cmd 60/60:90:00:47:31/00:00:32:00:00/40 tag 18 ncq 49152 in
[  132.812141]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  132.812211] ata1.00: status: { DRDY }
[  132.812235] ata1: hard resetting link
[  133.139800] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  133.152462] ata1.00: configured for UDMA/133
[  133.152470] ata1.00: device reported invalid CHS sector 0
[  133.152473] ata1.00: device reported invalid CHS sector 0
[  133.152483] ata1: EH complete
[  193.840521] ata1.00: exception Emask 0x0 SAct 0x700000 SErr 0x0 action 0x6 frozen
[  193.840571] ata1.00: failed command: READ FPDMA QUEUED
[  193.840603] ata1.00: cmd 60/08:a0:88:0b:00/00:00:00:00:00/40 tag 20 ncq 4096 in
[  193.840603]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  193.842296] ata1.00: status: { DRDY }
[  193.843149] ata1.00: failed command: READ FPDMA QUEUED
[  193.844014] ata1.00: cmd 60/08:a8:00:10:04/00:00:05:00:00/40 tag 21 ncq 4096 in
[  193.844014]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  193.845805] ata1.00: status: { DRDY }
[  193.846705] ata1.00: failed command: WRITE FPDMA QUEUED
[  193.847608] ata1.00: cmd 61/08:b0:00:10:44/00:00:1f:00:00/40 tag 22 ncq 4096 out
[  193.847608]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  193.849487] ata1.00: status: { DRDY }
[  193.850434] ata1: hard resetting link
[  194.176422] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  194.189099] ata1.00: configured for UDMA/133
[  194.189107] ata1.00: device reported invalid CHS sector 0
[  194.189109] ata1.00: device reported invalid CHS sector 0
[  194.189111] ata1.00: device reported invalid CHS sector 0
[  194.189122] ata1: EH complete
[  196.704394] ata1.00: exception Emask 0x0 SAct 0x2000000 SErr 0x0 action 0x0
[  196.705374] ata1.00: irq_stat 0x40000008
[  196.706336] ata1.00: failed command: READ FPDMA QUEUED
[  196.707299] ata1.00: cmd 60/08:c8:88:0b:00/00:00:00:00:00/40 tag 25 ncq 4096 in
[  196.707299]          res 41/40:00:88:0b:00/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  196.709281] ata1.00: status: { DRDY ERR }
[  196.710280] ata1.00: error: { UNC }
[  196.723921] ata1.00: configured for UDMA/133
[  196.723939] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  196.723943] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  196.723945] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  196.723947] sd 0:0:0:0: [sda] CDB: 
[  196.723949] Read(10): 28 00 00 00 0b 88 00 00 08 00
[  196.723957] blk_update_request: I/O error, dev sda, sector 2952
[  196.725003] ata1: EH complete

```

Most probably these errors are indicating a failed HDD. So I have tried to access the HDD from bootable ubuntu pendrive. I can access the HDD and my files without any problem.
I have two partitions in my HDD; one is a large ext4 partitions where my Ubuntu is located and another is a small NTFS partition for Windows OS. Windows is booting without any problem.

Here is the output of ***fdisk -l***

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d284

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83888127    41943040    7  HPFS/NTFS/exFAT
/dev/sda2        83890174   976771071   446440449    5  Extended
/dev/sda5       968773632   976771071     3998720   82  Linux swap / Solaris
/dev/sda6        83890176   968773631   442441728   83  Linux

Partition table entries are not in disk order

```

I have also tried to boot from some previous kernel versions. All are showing same problem. So Its not a kernel issue.

Is there any way to boot from this HDD?

Anykind of help will be appreciated, Thanks!

---

### Post by weatherman2 on 2016-03-03
if your hard drive is failing, you can't "fix" it - you need to get a new hard drive.  Try to use GSmartControl from your pen drive Linux to check the S.M.A.R.T. Attributes to confirm the drive is really failing (sounds like it).

I would back up everything as soon as possible, as failing hard drives tend to get worse and files may become unreadable quickly.  Just because you can "see" everything now doesn't mean you can still COPY everything.

Once you've backed up everything you care about on the failing hard drive, you could try cloning it to a new drive to avoid a complete re-install.  You can clone even a dual-boot setup with Clonezilla, but if you have trouble booting Linux, maybe it is too late to clone - you may have to re-install from scratch.  Just because you can boot Windows doesn't mean you should be able to boot Linux.  The failures on your hard drive could be only on the Linux portions and not on the Windows portions of the drive.

---

### Post by oldfred on 2016-03-04
I have seen frozen on some SSD, but do not know how to unfreeze.
exception Emask 0x0 SAct 0x60000 SErr 0x0 action 0x6 [COLOR=#ff0000]frozen
[/COLOR]
Hard drive info - will show locked frozen status or not:
 sudo hdparm -I /dev/sda

---

