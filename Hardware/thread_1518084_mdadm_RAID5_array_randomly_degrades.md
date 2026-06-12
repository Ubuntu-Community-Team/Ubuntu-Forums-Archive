---
title: "mdadm RAID5 array randomly degrades"
date: 2010-06-26
forum: Hardware
---

### Post by motoaxe on 2010-06-26
Hey guys, I've been battling (and cursing, and throwing stuff around) with this issue since I upgraded to 10.04 in April.  

I have an mdadm RAID5 array set up with 3 1TB sata disks.  All the same brand and model, and roughly 6 months old... I'll be humming along nicely, writing something to the array and BOOM.  The mount goes read-only, then craps out entirely.  I can usually manage to recover things with various reboots, mdadm --fail, mdadm --remove, mdadm --add/scan/assemble commands, but it seems to be getting more frequent, and it's really annoying to wait 3-4 hours every time the thing degrades for it to rebuild.

Palimpsest (Disk Utility) says all 3 drives are healthy.

Also, it now randomly reassigns /dev/ names so that screws things up sometimes when I reboot too.  Can you specify drives by UUID in mdadm.conf?

I know the whole mdadm thing is kinda gimmicky, but I'm not going out and buying a freaking filer and veritas volume manager for home :D

Has anyone else experienced this sort of thing?

Here's the details:
```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[2] sdd1[***](F) sdc1[3](F)
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/1] [__U]
      
unused devices: <none>

$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Feb 21 16:59:51 2010
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jun 25 23:18:57 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2b37f519:fa64f7c8:58a7b64f:475fa1cf (local to host eric-desktop)
         Events : 0.149852

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3      ()       ()         -      faulty spare   /dev/sdd1 ***
       4      8       33        -      faulty spare   /dev/sdc1

```*** I removed sdd1 and tried to re-add it but it wouldn't let me, and I don't want to reboot, lest I have to sort through more dmesg output!  So, I'm not sure what the major and minor device numbers were... I went past my buffer on my terminal :P

dmesg brings up this sort of thing:
```

[27585.952832] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[27585.952837] ata5.00: failed command: FLUSH CACHE EXT
[27585.952842] ata5.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[27585.952843]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[27585.952845] ata5.00: status: { DRDY }
[27585.952851] ata5: hard resetting link
[27585.952853] ata5: nv: skipping hardreset on occupied port
[27586.011318] ata6: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[27586.011322] ata6: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[27586.011323]   dhfis 0x0 dmafis 0x0 sdbfis 0x0
[27586.011326] ata6: ATA_REG 0x40 ERR_REG 0x0
[27586.011327] ata6: tag : dhfis dmafis sdbfis sacitve
[27586.011330] ata6: tag 0x0: 0 0 0 1  
[27586.011340] ata6.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
[27586.011343] ata6.00: failed command: WRITE FPDMA QUEUED
[27586.011348] ata6.00: cmd 61/08:00:3f:59:70/00:00:74:00:00/40 tag 0 ncq 4096 out
[27586.011349]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[27586.011351] ata6.00: status: { DRDY }
[27586.011357] ata6: hard resetting link
[27586.011358] ata6: nv: skipping hardreset on occupied port
[27586.441924] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27586.504619] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27591.463233] ata5.00: qc timeout (cmd 0x27)
[27591.463239] ata5.00: failed to read native max address (err_mask=0x4)
[27591.463242] ata5.00: revalidation failed (errno=-5)
[27591.463250] ata5: hard resetting link
[27591.463251] ata5: nv: skipping hardreset on occupied port
[27591.520046] ata6.00: qc timeout (cmd 0x27)
[27591.520052] ata6.00: failed to read native max address (err_mask=0x4)
[27591.520055] ata6.00: revalidation failed (errno=-5)
[27591.520063] ata6: hard resetting link
[27591.520065] ata6: nv: skipping hardreset on occupied port
[27591.950071] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27592.010050] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27601.970050] ata5.00: qc timeout (cmd 0x27)
[27601.970056] ata5.00: failed to read native max address (err_mask=0x4)
[27601.970061] ata5.00: revalidation failed (errno=-5)
[27601.970066] ata5: limiting SATA link speed to 1.5 Gbps
[27601.970074] ata5: hard resetting link
[27601.970076] ata5: nv: skipping hardreset on occupied port
[27602.030045] ata6.00: qc timeout (cmd 0x27)
[27602.030050] ata6.00: failed to read native max address (err_mask=0x4)
[27602.030054] ata6.00: revalidation failed (errno=-5)
[27602.030057] ata6: limiting SATA link speed to 1.5 Gbps
[27602.030064] ata6: hard resetting link
[27602.030066] ata6: nv: skipping hardreset on occupied port
[27602.461415] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27602.520042] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[27612.480048] ata5.00: qc timeout (cmd 0x27)
[27612.480055] ata5.00: failed to read native max address (err_mask=0x4)
[27612.480059] ata5.00: revalidation failed (errno=-5)
[27612.480064] ata5.00: disabled
[27612.480071] ata5.00: device reported invalid CHS sector 0
[27612.480084] ata5: hard resetting link
[27612.540044] ata6.00: qc timeout (cmd 0x27)
[27612.540049] ata6.00: failed to read native max address (err_mask=0x4)
[27612.540053] ata6.00: revalidation failed (errno=-5)
[27612.540056] ata6.00: disabled
[27612.540063] ata6.00: device reported invalid CHS sector 0
[27612.540074] ata6: hard resetting link
[27613.392228] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[27613.392257] ata5: EH complete
[27613.392272] sd 4:0:0:0: [sdc] Unhandled error code
[27613.392275] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[27613.392279] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 74 70 59 3f 00 00 08 00
[27613.392291] end_request: I/O error, dev sdc, sector 1953519935
[27613.392301] end_request: I/O error, dev sdc, sector 1953519935
[27613.392307] md: super_written gets error=-5, uptodate=0
[27613.392312] raid5: Disk failure on sdc1, disabling device.
...
[27613.451438] md: super_written gets error=-5, uptodate=0
[27613.451442] raid5: Disk failure on sdd1, disabling device.
[27613.451443] raid5: Operation continuing on 1 devices.
[27613.478933] RAID5 conf printout:
[27613.478937]  --- rd:3 wd:1
[27613.478941]  disk 0, o:0, dev:sdc1
[27613.478945]  disk 1, o:0, dev:sdd1
[27613.478948]  disk 2, o:1, dev:sde1
[27613.541280] RAID5 conf printout:
[27613.541283]  --- rd:3 wd:1
[27613.541286]  disk 0, o:0, dev:sdc1
[27613.541289]  disk 2, o:1, dev:sde1
[27613.541298] RAID5 conf printout:
[27613.541300]  --- rd:3 wd:1
[27613.541302]  disk 0, o:0, dev:sdc1
[27613.541305]  disk 2, o:1, dev:sde1
[27613.621278] RAID5 conf printout:
[27613.621281]  --- rd:3 wd:1
[27613.621284]  disk 2, o:1, dev:sde1
...
[27613.621384] Buffer I/O error on device md0, logical block 263702175
[27613.621386] lost page write due to I/O error on md0
[27613.621428] EXT4-fs (md0): delayed block allocation failed for inode 49022753 at logical offset 19712 with max blocks 56 with error -5
[27613.621434] 
[27613.621436] This should not happen!!  Data will be lost
...
[29405.637173] sd 5:0:0:0: [sdd] CDB: Read(10): 28 00 74 70 59 41 00 00 06 00
[29405.637180] end_request: I/O error, dev sdd, sector 1953519937
[29405.637183] Buffer I/O error on device sdd1, logical block 976759937
[29405.637185] Buffer I/O error on device sdd1, logical block 976759938
[29405.637188] Buffer I/O error on device sdd1, logical block 976759939
[29405.637204] sd 5:0:0:0: [sdd] Unhandled error code
[29405.637206] sd 5:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
...

```Since I can rebuild it and get things working again, I don't *think* it's a drive problem.  At least I hope not, tearing apart this stupid antec case is a pain in the butt haha.

Any help would be much appreciated! Thanks!

---

### Post by nicolasdiogo on 2010-09-08
same problem here

did you manage to solve it?

---

### Post by r00tuk on 2010-09-12
Hi

It looks like I am having similar problems.  See [http://ubuntuforums.org/showthread.php?t=1572675]("http://ubuntuforums.org/showthread.php?t=1572675")

---

