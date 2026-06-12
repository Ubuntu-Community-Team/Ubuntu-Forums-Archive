---
title: "[SOLVED] IOMEGA Rev 35 ATAPI Drive"
date: 2008-06-07
forum: Hardware
---

### Post by DrJohn999 on 2008-06-07
The IOMEGA Rev 35 ATAPI Drive is detected (in BIOS) either as secondary when ganged with the DVD-ROM or primary by itself. In Hardy (server), it shows up as dev/scd1, but won't mount. 

This system has a pair of 160 GB SATA drives in software RAID1 and an external 750GB ESATA drive. Here's fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=a52c2d8c-e78e-4394-a02a-3037efea7a1b /               ext3    relatime,errors=remount-ro,usrquota,grpquota  0       1
# /dev/md1
UUID=527cf3a4-c3eb-47b0-b6c2-0f076b98c85b /home           ext3    relatime,usrquota,grpquota        0       2
# /dev/sda2
UUID=1f09dcd1-dbd4-4300-80ad-61aee121d1a3 none            swap    sw              0       0
# /dev/sdb2
UUID=8a9d1772-7708-43d5-81cf-dcb138d2d43b none            swap    sw              0       0
#Added for the Seagate 750 GB external drive on eSATA
UUID=d8c01c03-a9c8-4771-9b96-fdbc7797be2c /var/lib/backuppc ext3 defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#this is the rev drive, no exec
/dev/scd1       /media/rev0   udf,iso9660 user,noauto,rw 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

mount /dev/scd1 -t iso9660 /media/rev0

gives a partition not found error, and a hardware error is logged on the drive. Specifying udf does no better, and udffs isn't recognized as a valid filesystem at all.

Trying to use fdisk to create a partition fails with the same h/w error. The OS seems to query the device once in a while and this also creates a hardware error:
```

1 Time(s): [13856.019999] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
 1 Time(s): [13856.020015] ata3.00: BMDMA2 stat 0x86c2201
 1 Time(s): [13856.020026] ata3.00: cmd 35/00:10:e7:1d:01/00:02:00:00:00/e0 tag 0 dma 270336 out
 1 Time(s): [13856.020040] ata3.00: status: { DRDY ERR }
 1 Time(s): [13856.344744] ata3: soft resetting link
 1 Time(s): [13856.504523] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
 1 Time(s): [13856.844251] ata3.00: configured for UDMA/100
 1 Time(s): [13856.844264] ata3: EH complete
```

It's curious that the log shows that a SATA link is up on ATA3 and then in the next line says it's configured for UDMA/100 (which makes sense since it's on IDE). Rebooting with the ESATA drive unplugged doesn't get the REV drive to work, however.

This same drive used to work on a different motherboard under Gutsy server; it also works today under WinXPPro with or without IOMEGA's windows drive installed.

I'm open to suggestions here.

Thanks,

DJ

---

### Post by DrJohn999 on 2008-06-24
Moved the REV 35 GB back to the WinXP Pro machine and replaced with a pair of external USB 350GB drives, which cost about as much as 4 REV cartridges (i.e. much less / GB). The new USB drives work very well in concert with BackupPC's archive function to save the current state of BackupPC's file pool.

---

