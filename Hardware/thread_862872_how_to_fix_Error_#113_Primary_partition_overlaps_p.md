---
title: "how to fix? Error #113: Primary partition overlaps previous partition."
date: 2008-07-17
forum: Hardware
---

### Post by nightingale2k1 on 2008-07-17
Hi,

I have dualbot, linuxmint 4 (ubuntu based right?) and windows xp on my notebook. Yesterday I want to replace linuxmint with Ubuntu one. But when it asked the partition, it seems GParted cannot detect the Windows or other partition. It just said that there are unlocated partitions (so my disc is all available). I stopped and back to windows. Do checking with Partition Magic 8. and here what i got. It said disc geometry in wrong position and linux swap overlapping something .... 
I don't understand about this and I don't know how to fix it. Can you tell me how to do this ? 

```

===========================================================================================================
Disk Geometry Information for Disk 1:    10337 Cylinders,  240 Heads,  63 Sectors/Track
System              PartSect  # Boot BCyl Head Sect  FS    ECyl Head Sect    StartSect     NumSects
===========================================================================================================
                           0  0  80     0    1    1  07    1023  239   63           63   71,683,857
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  0  80      0    1    1  07   4740  239   63        63  71683857
                           0  1  00  1023  225    1  07    1023  239   63   71,698,095   66,166,065
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  1  00   4741  225    1  07   9117  239   63  71698095  66166065
Error #105: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 225.
SWAPSPACE2                 0  2  00  1023  254   63  82    1023  254   63  137,853,765    3,903,795
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  2  00   9117   75    1  82   9375  119   63 137853765   3903795
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 75.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 119.
                           0  3  00  1023  254   63  83    1023  254   63  141,757,560   14,538,825
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  3  00   9375  120    1  83  10337   14   63 141757560  14538825
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 120.
Error #109: Partition ends after end of disk.
  ucEndCylinder (10337) must be less than 10337.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 14.



===========================================================================================================
Partition Information for Disk 1:    76,316.1 Megabytes
Volume         PartType    Status    Size MB    PartSect  #   StartSect  TotalSects
===========================================================================================================
C:             NTFS        Pri,Boot 35,001.9           0  0          63  71,683,857
H:             NTFS        Pri      32,307.6           0  1  71,698,095  66,166,065
*:SWAPSPACE2   Linux Swap  Pri       1,906.1           0  2 137,853,765   3,903,795
Error #113: Primary partition starting at 137853765 overlaps previous partition.
               Linux Ext3  Pri       7,099.0           0  3 141,757,560  14,538,825

```

---

