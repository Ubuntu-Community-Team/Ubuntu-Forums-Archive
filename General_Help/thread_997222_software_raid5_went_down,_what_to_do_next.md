---
title: "software raid5 went down, what to do next?"
date: 2008-11-29
forum: General Help
---

### Post by ubdime on 2008-11-29
So I have a 6 disk raid 5. I took care to properly pad the drives from vibrations and cool them. Then today this:

```
Nov 29 11:45:12 lanfear -- MARK --
Nov 29 12:00:33 lanfear kernel: [82553.825095] ata6: hard resetting link
Nov 29 12:00:33 lanfear kernel: [82553.825686] ata4: hard resetting link
Nov 29 12:00:37 lanfear kernel: [82558.073705] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 29 12:00:37 lanfear kernel: [82558.073715] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x40)
Nov 29 12:00:37 lanfear kernel: [82558.129623] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 29 12:00:37 lanfear kernel: [82558.129633] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x40)
Nov 29 12:00:42 lanfear kernel: [82563.073516] ata4: hard resetting link
Nov 29 12:00:42 lanfear kernel: [82563.129526] ata6: hard resetting link
Nov 29 12:00:42 lanfear kernel: [82563.557526] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 29 12:00:42 lanfear kernel: [82563.616017] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 29 12:00:42 lanfear kernel: [82563.663525] ata4.00: configured for UDMA/133
Nov 29 12:00:42 lanfear kernel: [82563.724644] ata6.00: configured for UDMA/133
Nov 29 12:00:43 lanfear kernel: [82563.796817] ata4.00: configured for UDMA/133
Nov 29 12:00:43 lanfear kernel: [82563.796840] md: super_written gets error=-5, uptodate=0
Nov 29 12:00:43 lanfear kernel: [82563.796867] ata4: EH complete
Nov 29 12:00:43 lanfear kernel: [82563.796968] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Nov 29 12:00:43 lanfear kernel: [82563.796986] sd 3:0:0:0: [sdd] Write Protect is off
Nov 29 12:00:43 lanfear kernel: [82563.797017] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 29 12:00:43 lanfear kernel: [82563.857938] ata6.00: configured for UDMA/133
Nov 29 12:00:43 lanfear kernel: [82563.857973] md: super_written gets error=-5, uptodate=0
Nov 29 12:00:43 lanfear kernel: [82563.858006] ata6: EH complete
Nov 29 12:00:43 lanfear kernel: [82563.858098] sd 5:0:0:0: [sdf] 976773168 512-byte hardware sectors (500108 MB)
Nov 29 12:00:43 lanfear kernel: [82563.858117] sd 5:0:0:0: [sdf] Write Protect is off
Nov 29 12:00:43 lanfear kernel: [82563.858140] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 29 12:00:43 lanfear kernel: [82563.858170] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Nov 29 12:00:43 lanfear kernel: [82563.858182] sd 3:0:0:0: [sdd] Write Protect is off
Nov 29 12:00:43 lanfear kernel: [82563.858207] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 29 12:00:43 lanfear kernel: [82563.891740] RAID5 conf printout:
Nov 29 12:00:43 lanfear kernel: [82563.891747]  --- rd:6 wd:4
Nov 29 12:00:43 lanfear kernel: [82563.891750]  disk 0, o:0, dev:sdf1
Nov 29 12:00:43 lanfear kernel: [82563.891752]  disk 1, o:1, dev:sdc1
Nov 29 12:00:43 lanfear kernel: [82563.891754]  disk 2, o:1, dev:sde1
Nov 29 12:00:43 lanfear kernel: [82563.891755]  disk 3, o:0, dev:sdd1
Nov 29 12:00:43 lanfear kernel: [82563.891757]  disk 4, o:1, dev:sdg1
Nov 29 12:00:43 lanfear kernel: [82563.891758]  disk 5, o:1, dev:sdh1
Nov 29 12:00:43 lanfear kernel: [82563.901518] RAID5 conf printout:
Nov 29 12:00:43 lanfear kernel: [82563.901524]  --- rd:6 wd:4
Nov 29 12:00:43 lanfear kernel: [82563.901528]  disk 1, o:1, dev:sdc1
Nov 29 12:00:43 lanfear kernel: [82563.901530]  disk 2, o:1, dev:sde1
Nov 29 12:00:43 lanfear kernel: [82563.901531]  disk 3, o:0, dev:sdd1
Nov 29 12:00:43 lanfear kernel: [82563.901533]  disk 4, o:1, dev:sdg1
Nov 29 12:00:43 lanfear kernel: [82563.901534]  disk 5, o:1, dev:sdh1
Nov 29 12:00:43 lanfear kernel: [82563.901792] RAID5 conf printout:
Nov 29 12:00:43 lanfear kernel: [82563.901794]  --- rd:6 wd:4
Nov 29 12:00:43 lanfear kernel: [82563.901796]  disk 1, o:1, dev:sdc1
Nov 29 12:00:43 lanfear kernel: [82563.901797]  disk 2, o:1, dev:sde1
Nov 29 12:00:43 lanfear kernel: [82563.901798]  disk 3, o:0, dev:sdd1
Nov 29 12:00:43 lanfear kernel: [82563.901801]  disk 4, o:1, dev:sdg1
Nov 29 12:00:43 lanfear kernel: [82563.901802]  disk 5, o:1, dev:sdh1
Nov 29 12:00:43 lanfear kernel: [82563.913518] RAID5 conf printout:
Nov 29 12:00:43 lanfear kernel: [82563.913525]  --- rd:6 wd:4
Nov 29 12:00:43 lanfear kernel: [82563.913529]  disk 1, o:1, dev:sdc1
Nov 29 12:00:43 lanfear kernel: [82563.913531]  disk 2, o:1, dev:sde1
Nov 29 12:00:43 lanfear kernel: [82563.913532]  disk 4, o:1, dev:sdg1
Nov 29 12:00:43 lanfear kernel: [82563.913534]  disk 5, o:1, dev:sdh1
Nov 29 12:00:43 lanfear kernel: [82563.913779] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.913899] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914012] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914119] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914232] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914339] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914445] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914551] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914657] lost page write due to I/O error on md1
Nov 29 12:00:43 lanfear kernel: [82563.914902] JBD: Detected IO errors while flushing file data on md1
Nov 29 12:01:13 lanfear kernel: [82593.956428] __ratelimit: 57 callbacks suppressed
Nov 29 12:01:13 lanfear kernel: [82593.956438] lost page write due to I/O error on md1
Nov 29 12:01:13 lanfear kernel: [82593.956516] lost page write due to I/O error on md1
Nov 29 12:01:13 lanfear kernel: [82593.956535] lost page write due to I/O error on md1
Nov 29 12:01:48 lanfear kernel: [82628.957680] lost page write due to I/O error on md1
Nov 29 12:01:48 lanfear kernel: [82628.957715] lost page write due to I/O error on md1
Nov 29 12:25:12 lanfear -- MARK --
```

Before I rebooted, I did a cat /proc/mdstat and saw a [F] next to sdd and sdf. I panicked and did a reboot. When I did, I got a deluge of ATA3.0 i/o errors (3.0 is sdd)

```
After I rebooted, this:
root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdc1[1](S) sdg1[5](S) sdf1[4](S) sdd1[2](S) sde1[0](S)
      2441919680 blocks
       
md0 : active raid1 sda1[0] sdb1[1]
      243167744 blocks [2/2] [UU]

smartctl shows all 5 drives that are plugged in to be working, so there might be hope? I check fdisk -l and: 

root@lanfear:~# fdisk -l /dev/sdc

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
root@lanfear:~# fdisk -l /dev/sdd

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5149e5d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux
root@lanfear:~# fdisk -l /dev/sde

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux
root@lanfear:~# fdisk -l /dev/sdf

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2015851e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux
root@lanfear:~# fdisk -l /dev/sdg

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf79fa279

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   83  Linux

However, when I try:
root@lanfear:~# mdadm --manage --run /dev/md1
mdadm: failed to run array /dev/md1: Input/output error

root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdc1[1] sdg1[5] sdf1[4] sdd1[2]
      1953535744 blocks
       
md0 : active raid1 sda1[0] sdb1[1]
      243167744 blocks [2/2] [UU]
```

It looks like sde is the one that didn't get added to the raid? Please help!

In the meantime, I am going to unplug all the drives.

---

### Post by rgbtxus on 2008-11-29
Just take a deep breath, get out some note paper and be totally methodical.  It is likely you lost a drive and did not notice and continued happily running in degraded mode until some event dropped the second drive and murdered the array.  If that second event was transient or a drive failure of a tiny disk area you should come out of this fine.  If the second disk is significantly unrecoverable your array is toast (unless the first drive to die died very close in time to the array failure so it can serve as a "good" drive (even though it will be a bit out of sync and your data will come back but with some errors.  If these are media files that is probably better than losing the array.  If this contains important data you better be getting your backup out!)

1) test each component drive using smartctl -t long and/or whatever method you like.  Assuming at most one drive really failed you will be just fine.  If two physically failed you are in trouble.  If you cannot recover one of the two dead drives with dd_recover then it's game over
2) knowing that you have at most one dead drive look at the superblock info of each living drive with mdadm -E /dev/sdXX.  You will see something like this (your details will be different)

/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5bf98f0f:38057634:dafc93a3:f3c76e1e
  Creation Time : Wed Nov 14 23:40:31 2007
     Raid Level : raid5
  Used Dev Size : 312504256 (298.03 GiB 320.00 GB)
     Array Size : 937512768 (894.08 GiB 960.01 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 21

    Update Time : Sat Nov 29 14:57:19 2008
          State : clean
Internal Bitmap : present
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : aefd7c27 - correct
         Events : 9026

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1

write down the UUID & events for each.  Make sure the UUIDs all match.  
3) find the largest group of drives with the same events number.  If that is N-1 you will recover a perfect array.  If it is N-2 then the quality of the recovered array will be a function of how much out of date the odd ball is.  If the numbers are very close and it is better to recover the array "with some errors" than to lose it all, then proceed otherwise it's recreate the array and restore from backup time.  Anyway take the group of up to date drives (in my case this would be 2 out of 4) and reassemble the array with that.  Naturally it cannot run yet.  Then add the next best living drive as judged by the events counter to the array (I assume you will need to add force).  If your last drive is functional add it last.  Otherwise prepare a replacement drive (correct size partition, type fd) and add it instead.  You should be able to run the array now. watch cat /proc/mdstat should show you rebuilding.

Don't do anything I suggested without checking it out in the man page ('cause I didn't before writing this, but this is my recollection of how I recovered from just such an event recently).  I don't recall if I ran the array before adding the final drive but I do not see why it would not run in degraded mode at that point.  Anyway since running in degraded mode is dangerous - one failure and you are dead again - I would not use the array in degraded mode unless absolutely necessary to ensure the fastest rebuild time and to not tempt the gods :-)

---

### Post by ubdime on 2008-11-30
Thanks very much for the quick reply rgbtxus!

Here is an update:

```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
sdc: # 1  Extended offline    Completed without error       00%      6366         -
sdd: # 1  Extended offline    Completed without error       00%      6382         -
sde: # 1  Extended offline    Completed without error       00%      6436         -
sdf: # 1  Extended offline    Completed without error       00%      6336         -
sdg: # 1  Extended offline    Completed without error       00%      7795         -

I can't reboot with #6 (original sdd) at all because it just gives me an infinite amount of these errors:

[   55.715513] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   55.715573] ata3.00: irq_stat 0x40000008
[   55.715636] ata3.00: cmd 60/02:00:c3:4b:38/00:00:3a:00:00/40 tag 0 ncq 1024 in
[   55.715640]          res 41/40:02:c3:4b:38/05:00:3a:00:00/00 Emask 0x409 (media error) <F>
[   55.715783] ata3.00: status: { DRDY ERR }
[   55.715845] ata3.00: error: { UNC }

So I only have 5/6 alive and I'm assuming the 6th to be dead for sure (for now).

checking mdadm -E, you're right on the ball with the events #, 1 of them is slightly off.
sdc: UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 649564
sdd: UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 649564
sde: UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 649554
sdf: UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 649564
sdg: UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 649564

sdc,d,f,g show this table:
   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync

while sde shows this one:
   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync
```

It looks like sde is just off by 10 events. I notice now looking back at the system log, I didn't reboot until 3:43. So I was running on a degraded raid for almost 4 hours (running multimedia files off it as well as incoming/outgoing torrents).

So just to confirm, my next step is to reassemble the raid5 with 4/5 remaining devices. That is, sdc,sdd,sdf,sdg. Then force add sde back in?

Given that I have 4 out of 5 working disks with the same event #'s and 1 slightly off, could I also just use mdadm --assemble --force?

---

### Post by rgbtxus on 2008-11-30
I think you will come out of this okay (assuming that these are media files and you can tolerate the near certainty that at least one file will be inconsistent, if you are real lucky it will just be some temp or incomplete torrent that you may restart anyway).  I'm not sure if you can just do the force assemble of the whole array since mdadm knows the array to be broken by the event counters.  I don't think I tried that.  I have be very impressed by mdadm's robustness so I would not be surprised if it did the right thing, I just don't think I tried it. I did the piecemeal reassembly.  I only had to do this once and my notes are 1800 miles away from my current location so I cannot consult them.  I would encourage anyone reading this thread to confirm that this is the way to proceed if they are able to do so.

Final thought -- replace the dead drive ASAP so you don't have to play this game again in the near future.  <G>
 
bonne chance

---

### Post by fjgaude on 2008-11-30
I can't remember if I've gone through exactly the same thing, but I'd try a forced assembly first, nothing to lose or go wrong:

```
sudo mdadm --assemble --force /dev/md0
```

If that doesn't work, I'd do this, but I'm not sure you want to: I'd rename the /etc/mdadm/mdadm.conf file, remove mdadm, reboot. Then after booting, re-install mdadm, where the mdadm.conf file is auto created. See if the array mounts.

If not, I'd do a -D on the array:

```
sudo mdadm -D /dev/md0
```

and see what that says.

After all that I'd add the new drive, or even try to add back the drive you know is bad. If it has failed once it should be taken out and a new drive put in with the --add command.

I tell you all this points to having good backups. I have three at all times, one online, one near-line, and one off-line. Always check to see if all drives are functioning correclty with the -D command.

Good luck!

---

### Post by ubdime on 2008-12-01
So the --assemble --force didn't work. So I first just reassembled with 4 devices.

```
root@lanfear:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Fri Oct 31 23:10:19 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Nov 29 15:30:06 2008
          State : active, degraded, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 0.649564

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

root@lanfear:~# mdadm /dev/md1 --add /dev/sde1
mdadm: re-added /dev/sde1
root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sde1[0] sdc1[1] sdg1[5] sdf1[4] sdd1[2]
      2441919680 blocks
       
md0 : active raid1 sda1[0] sdb1[1]
      243167744 blocks [2/2] [UU]
      
unused devices: <none>

root@lanfear:~# mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Fri Oct 31 23:10:19 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Nov 29 15:30:06 2008
          State : active, degraded, Not Started
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 0.649554

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
root@lanfear:~# mdadm --run /dev/md1
mdadm: started /dev/md1
```

Mounted it, all files are good.. immediately unmounted and shutdown the system to unplug drives until I get a spare one. THANK YOU FOR ALL YOUR HELP.

/dev/md1             2403601996 1175445008 1228156988  49% /media/save

All 1,175,445,008 bytes of my precious files thank you guys for the support!

---

### Post by fjgaude on 2008-12-01
Software raid works well, if you know what we are doing?

Happy you have everything back to normal and know what to do.

---

### Post by ubdime on 2008-12-07
Went to fry's and picked up a 1tb drive. Here is the recovery. sdg is the 5th of my raid5. sdh is the new drive.

```
root@lanfear:~# fdisk -l /dev/sdg

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf79fa279

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   83  Linux

(take note of the start and end of the the cylinders.)

root@lanfear:~# fdisk /dev/sdh
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6e7f8086.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 121601.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n   
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-121601, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-121601, default 121601): 60801

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (60802-121601, default 60802): 
Using default value 60802
Last cylinder, +cylinders or +size{K,M,G} (60802-121601, default 121601): 
Using default value 121601

Command (m for help): p

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e7f8086

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   83  Linux
/dev/sdh2           60802      121601   488376000   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@lanfear:~# mdadm --add /dev/md1 /dev/sdh1
mdadm: added /dev/sdh1
root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdh1[6] sdf1[0] sdg1[5] sdd1[4] sde1[2] sdc1[1]
      2441919680 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUU_UU]
      [>....................]  recovery =  0.0% (191104/488383936) finish=127.6min speed=63701K/sec
      
md0 : active raid1 sda1[0] sdb1[1]
      243167744 blocks [2/2] [UU]
      
unused devices: <none>
```

I built this raid a month ago because I went through a devastating loss of my old system drive that had a lot of important files on it. I took that loss and I turned it into my opportunity to install linux as my os on my desktop. And only a short time later, this drive goes down too and I would have been completely lost if I lost this second half of my files that's been almost 2 decades in the making. I'm quite fortunate to have linux and your support to have helped me through it.

---

### Post by fjgaude on 2008-12-08
Wonderful! You can use this to watch the build:

```
sudo watch cat /proc/mdstat
```

That way you see it move toward completion.

---

