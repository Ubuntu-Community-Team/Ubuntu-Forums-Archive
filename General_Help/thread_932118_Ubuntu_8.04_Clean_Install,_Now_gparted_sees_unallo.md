---
title: "Ubuntu 8.04 Clean Install, Now gparted sees unallocated"
date: 2008-09-28
forum: General Help
---

### Post by varun990 on 2008-09-28
I installed Ubuntu 8.04 from a cd, clean install on the whole hard disk. Used ubuntu's partition manager, and did custom partitioning with the following config

 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c7e3c7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         622     4996183+  83  Linux
/dev/sda2             623       19208   149292045   83  Linux
/dev/sda3           19209       19457     2000092+  82  Linux swap / Solaris

/dev/sda1 - /
/dev/sda2 - /home
/dev/sda3 - /swap


Didn't change anything since then. Now the root partition [/dev/sda1] is running out of space. I need to resize it.

But when I load up gparted live cd it sees unallocated space on /dev/sda.
I have tried knoppix live cd same thing.

I also tried testdisk but it said everything was fine/healthy no problems.



Does anybody know what might be wrong and how can it can fixed so that 
[LIST]
i can reduce /dev/sda2  and increase /dev/sda1
[/LIST]

[LIST]
maybe if at all possible install windows in the remaining empty space derived from /dev/sda2 
[/LIST]

---

