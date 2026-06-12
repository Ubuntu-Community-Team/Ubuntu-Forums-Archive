---
title: "mdadm borken in 9.10 -- I'm dying here!  HELP!"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2009-11-01
As far as I can tell mdadm is broken in 9.10...at least for me.

I think it all revolves around dmraid and volume management.

i have 11 disks in my system. 8 using mobo SATA ports and 4 on an internal sata board.

sda   500GB
sdb   160GB  -- boot
sdc   500GB
sdd   500GB
sde   750GB  -- partitions sde1 and sde2
sdf   750GB  -- partitions sdf1 and sdf2
sdg   750GB  -- partitions sdg1 and sdg2
sdh   1000GB
sdi   1000GB
sdj   1000GB
sdk   1000GB

I'm trying what I though would be a simple raid stripe.

mdadm --create /dev/md_d1 --level=0 --raid-devices=5 /dev/sde1 etc... I used the nvidia_dbhihcfc1 devices names from mapper... and it sets up fine...

i reboot and it's gone.

I don't use a raidtab and i shouldn't need a raid config file.....

i was able to setup md_d2 with sde2, sdf2 and sdg2 just fine...and it's persistent...but not with sde1 etc.

I HATE THIS!!!!

---

### Post by Kokopelli on 2009-11-01
what is the output of "cat /proc/mdstat"

EDIT: And while you do not need to add anything to mdadm.conf I have found that it makes things easier and more consistent if you provide an ARRAY line (using UUID) for each RAID.  This is especially true if you have multiple RAIDs on the same box.  Again, not required but helpful.

---

### Post by Cr0n_J0b on 2009-11-01
Any help would be seriously appreciated.  Based on what I'm seeing there is something SERIOUSLY messed up with the volume manager in 9.10.  As an example, i've been trying to build and rebuild these arrays md0, md1 and md2 for hours.  sometimes they build sometimes not.  I noticed that they alway change to md_d0, md_d1 and md_d2.  I'm guessing that's a device mapper thing...but then for some reason it built md_d64???  crazy and wrong! 

I successfully killed ALL of the old arrays and rebuilt using

mdadm --create /dev/md0 (not md_d0) --level=5 ...blah blah..

I can now see all of them listed and mdadm reports status...but only the md0 and md1 arrays.  I'm sure that when i reboot these will get renamed to md_d0 and md_d1 (STUPID)

here is the mdstat.

THANKS FOR THE HELP!  I apologize for my frustration...it's be a long 12 hours with no sleep...

root@linuxgate:/dev# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid0 sde1[0] dm-3[4] dm-4[3] sdf1[2] sdg1[1]
      2441919680 blocks 64k chunks
      
md0 : active raid5 sdk1[4] sdj1[2] sdi1[1] sdh1[0]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  2.9% (29007488/976759936) finish=163.0min speed=96856K/sec
      
md_d2 : active raid0 sdf2[1] sdg2[2] sde2[0]
      732563712 blocks 64k chunks

---

### Post by Cr0n_J0b on 2009-11-01
for some reason, the forum isn't reflecting that i replied to my post...is it possible that it doesn't take into account the starters reply?

---

### Post by Kokopelli on 2009-11-01
> md1 : active raid0 sde1[0] dm-3[4] dm-4[3] sdf1[2] sdg1[1]
2441919680 blocks 64k chunks

md0 : active raid5 sdk1[4] sdj1[2] sdi1[1] sdh1[0]
2930279808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
[>....................] recovery = 2.9% (29007488/976759936) finish=163.0min speed=96856K/sec

md_d2 : active raid0 sdf2[1] sdg2[2] sde2[0]
732563712 blocks 64k chunks


ok so lets see  

md_d2 is what you wanted so let's ignore that one for the moment.

md0  is a raid 5 with sd[hijk]1 as the component parts, is that right? (P.S. I would not recommend restarting till the RAID is rebuilt)

md1 is the odd ball.  "dm-3" and "dm-4" in particular.  Are you using some form of fakeraid?  e.g. do you have a RAID configuration in your BIOS?  From the looks of it you have a RAID0 made up of sd[efg]1 and 2 fakeraids, if I had to hazard a guess I would say they are raids made up of sda,b,c,and d. Two RAID 0s?

for MD0  I would suggest adding a line in your mdadm.conf as follows:
```

ARRAY /dev/md0 UUID=<UUID>
```

you can get the UUID from a "sudo mdadm --detail /dev/md0"

In my experience without the line my RAIDS were not given a consistent name. Which makes it a pain to mount, check status on, etc...  Again technically not required but it does get rid of headaches.

EDIT:  The forums are having problems today, this the reply issues etc.

---

### Post by Cr0n_J0b on 2009-11-01
Patience, or lack there of, might have been my downfall...but anyway...

to answer you questions.

here are the arrays in full:

md0----------------------------------------------------
root@linuxgate:/dev# mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Nov  1 11:11:57 2009
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Nov  1 11:55:30 2009
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 27% complete

           UUID : 2e13faf5:2899eca6:d4262458:ce04f656 (local to host linuxgate)
         Events : 0.7

    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8      129        1      active sync   /dev/sdi1
       2       8      145        2      active sync   /dev/sdj1
       4       8      161        3      spare rebuilding   /dev/sdk1

md1--------------------------------------------------------------
root@linuxgate:/dev# mdadm --query --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sun Nov  1 10:36:43 2009
     Raid Level : raid0
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Nov  1 10:36:43 2009
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : c73d3d68:2dbe6a0d:d4262458:ce04f656 (local to host linuxgate)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       97        1      active sync   /dev/sdg1
       2       8       81        2      active sync   /dev/sdf1
       3     252        4        3      active sync   /dev/block/252:4
       4     252        3        4      active sync   /dev/block/252:3

md2--------------------------------------------------------------
root@linuxgate:/dev# mdadm --query --detail /dev/md_d2
/dev/md_d2:
        Version : 00.90
  Creation Time : Sun Nov  1 09:10:27 2009
     Raid Level : raid0
     Array Size : 732563712 (698.63 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sun Nov  1 09:10:27 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 940e198b:72187113:d4262458:ce04f656 (local to host linuxgate)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       66        0      active sync   /dev/sde2
       1       8       82        1      active sync   /dev/sdf2
       2       8       98        2      active sync   /dev/sdg2
_________________________________________________________________

motherboard is an nvidia a8N-SLI deluxe with 8 onboard SATA and 2 IDE channels.  The first 4 SATA are nvidia chipset, the second 4 are Silicon Image(?).  all can do some type of RAID, but the RAID is disabled in the BIOS, so they should all be jbod.  as for the md2 disks, they are attached to a PCI based SI SATA board.  the 3 partitions are off of the same physical devices I"m using for md1.  

in all there are 3 sets, 

1) 4 drive raid 5 (4TB Raw, 3uTB)
2) 5 drives raid0 (2.5TB RAW, 2.5uTB)
3) 3 drives raid 0 (750GB raw, 750uGB)

thanks again for the help.  I'll add the 3 devices to the mdadm.conf file.  what is the format?  can i use any name i'd like for ARRAY or do i need to use the ones that md already knows about...that is md_d2, md0 and md1?

regards

---

### Post by Kokopelli on 2009-11-01
> **Cr0n_J0b said:**
> 
thanks again for the help.  I'll add the 3 devices to the mdadm.conf file.  what is the format?  can i use any name i'd like for ARRAY or do i need to use the ones that md already knows about...that is md_d2, md0 and md1?


All I have is 
```
 ARRAY /dev/md0 UUID=<UUID>
```

by convention software raids are md0,1,2  but I do not think it matters.


From the other thread (that you found :) )
> 
I have done some reading and found this:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/392510](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/392510)

the take away I got from it is you might try the "nodmraid" boot option.  The maintainer did not seem to like the solution but I think it would do what is needed for you.


your MD1 definitely **thinks** there is a dmraid in there.  Those raw block devices are pretty indicative.  You might try comparing hardware with the guy from the other thread and see if you are maybe using the same chipset.

---

