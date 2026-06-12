---
title: "Re-assembly of a software raid1 volume"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by pilou254 on 2009-11-03
Hello,  

 I need to recover a volume software raid1 (2 discs) from an old installation (Suse 9.2 ...) on my new machine (Ubuntu 9.04).

The system is on a third disc.

 Here is the informations I could get : 

> 
**sudo mdadm --examine /dev/sdb1:** 

/dev/sdb1: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : 1c0e01f4:fbcb5d87:55357bc2:af01e9f5 
  Creation Time : Mon Oct  3 15:30:02 2005 
     Raid Level : raid1 
  Used Dev Size : 80043136 (76.34 GiB 81.96 GB) 
     Array Size : 80043136 (76.34 GiB 81.96 GB) 
   Raid Devices : 2 
  Total Devices : 1 
Preferred Minor : 0 

    Update Time : Sat Oct 24 21:50:38 2009 
          State : clean 
 Active Devices : 1 
Working Devices : 1 
 Failed Devices : 1 
  Spare Devices : 0 
       Checksum : 582927ec - correct 
         Events : 101590 


      Number   Major   Minor   RaidDevice State 
this     0      22        1        0      active sync 

   0     0      22        1        0      active sync 
   1     1       0        0        1      faulty removed 


**sudo mdadm --examine /dev/sdc1 :** 

/dev/sdc1: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : 1c0e01f4:fbcb5d87:55357bc2:af01e9f5 
  Creation Time : Mon Oct  3 15:30:02 2005 
     Raid Level : raid1 
  Used Dev Size : 80043136 (76.34 GiB 81.96 GB) 
     Array Size : 80043136 (76.34 GiB 81.96 GB) 
   Raid Devices : 2 
  Total Devices : 1 
Preferred Minor : 0 

    Update Time : Sun Nov  1 02:14:15 2009 
          State : clean 
 Active Devices : 1 
Working Devices : 1 
 Failed Devices : 0 
  Spare Devices : 0 
       Checksum : 5832ba85 - correct 
         Events : 103094 


      Number   Major   Minor   RaidDevice State 
this     1      22       65        1      active sync 

   0     0       0        0        0      removed 
   1     1      22       65        1      active sync  
I guess the partitions  must be assembled now but a node has to be created before with mknod ?

 I can directly use the command :

> mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 ?or 

> mdadm -- assemble -- scan ? Has anybody ever had this type of case (I am a littke afraid to loose all my data ...) ?  
 If yes, I'd like to take advantage of his experience.  

 Thank you in advance for your help.  

 Sincerely.

---

