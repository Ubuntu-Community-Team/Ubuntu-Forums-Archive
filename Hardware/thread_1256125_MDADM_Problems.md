---
title: "MDADM Problems"
date: 2009-09-02
forum: Hardware
---

### Post by xupetas on 2009-09-02
Hello,

I have a problem with mdadm, by the fact that it will not stop rebuilding the drive going above the 100% mark.

mdadm --detail /dev/md1

/dev/md1:
        Version : 0.90
  Creation Time : Mon Mar 10 14:48:53 2008
     Raid Level : raid1
     Array Size : 15359872 (14.65 GiB 15.73 GB)
  Used Dev Size : 15359872 (14.65 GiB 15.73 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Sep  2 13:11:32 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           UUID : 207547ae:e3a3a6fe:ae63c8df:77914238
         Events : 0.4416

    Number   Major   Minor   RaidDevice State
       0       8       97        0      active sync   /dev/sdg1
       2       8       81        1      spare rebuilding   /dev/sdf1

cat /proc/mdstat 
Personalities : [linear] [raid1] 
md1 : active raid1 sdg1[0] sdf1[2]
      15359872 blocks [2/1] [U_]
      **[=====================>]  recovery =106.9% (8215488/7679936) finish=40741090.4min **speed=17226K/sec
 mdadm  --examine /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 207547ae:e3a3a6fe:ae63c8df:77914238
  Creation Time : Mon Mar 10 14:48:53 2008
     Raid Level : raid1
  Used Dev Size : 15359872 (14.65 GiB 15.73 GB)
     Array Size : 15359872 (14.65 GiB 15.73 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Wed Sep  2 13:20:44 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 669779e3 - correct
         Events : 4418


      Number   Major   Minor   RaidDevice State
this     0       8       97        0      active sync   /dev/sdg1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       0        0        1      faulty removed
   2     2       8       81        2      spare   /dev/sdf1

mdadm  --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 207547ae:e3a3a6fe:ae63c8df:77914238
  Creation Time : Mon Mar 10 14:48:53 2008
     Raid Level : raid1
  Used Dev Size : 15359872 (14.65 GiB 15.73 GB)
     Array Size : 15359872 (14.65 GiB 15.73 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Wed Sep  2 13:20:44 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 669779d1 - correct
         Events : 4418


      Number   Major   Minor   RaidDevice State
this     2       8       81        2      spare   /dev/sdf1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       0        0        1      faulty removed
   2     2       8       81        2      spare   /dev/sdf1

PS: both disks are ok and not faulty in any way.
They where transfered from another system and now i can access the data but it will not stop rebuilding.         

Can anyone tell me how to stop this? I just want to rebuild the md1 array.


Thanks.

---

