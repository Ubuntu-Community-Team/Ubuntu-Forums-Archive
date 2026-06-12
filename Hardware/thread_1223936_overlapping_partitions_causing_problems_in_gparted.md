---
title: "overlapping partitions causing problems in gparted"
date: 2009-07-26
forum: Hardware
---

### Post by allenbina on 2009-07-26
as per this thread, i'm making a new thread [http://ubuntuforums.org/showthread.php?t=1126190&page=3](http://ubuntuforums.org/showthread.php?t=1126190&page=3). 


allen@allen-laptop:~$ **sudo fdisk -lu**
[sudo] password for allen: 
Error: Can't have overlapping partitions.
allen@allen-laptop:~$ **sudo sfdisk -d**
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=815362947, Id= 7, bootable
/dev/sda2 : start=815364096, size= 51388416, Id=af
/dev/sda3 : start=866752512, size= 88874013, Id= 5
/dev/sda4 : start=895463100, size= 56066850, Id=83
/dev/sda5 : start=866755008, size= 14474502, Id=83
/dev/sda6 : start=881229573, size= 14233527, Id=83
/dev/sda7 : start=951530013, size=  4096512, Id=82
allen@allen-laptop:~$ **sudo parted print**
Error: Could not stat device print - No such file or directory.           
Retry/Cancel? c                                                           
allen@allen-laptop:~$ **sudo parted /dev/sda print**
Error: Can't have overlapping partitions.  
 
and while i'm at it, how do nest text in the nice looking boxes?

---

### Post by drs305 on 2009-07-26
The boxes are text/code placed inside either 'code' or 'quote' tags. These are available by clicking either icon at the top of the post. Code tags are the # icon, the quote tag is the yellow text page icon. You place your entry between the tags that appear when you click either icon.

Your partition table needs to be corrected. Back up any important data before doing anything to the partition table.

Testdisk is a very useful tool. Here is a link on how to use it. There are also very good threads on this forum. Look for posts by caljohnsmith.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

You can also inspect the partition table with (substitute the correct device): 
```

sudo fdisk /dev/sdXX

```
and type "p" to print the partition table for inspection, which will show the start/ends of each partition.

---

### Post by allenbina on 2009-07-26
GNU Fdisk 1.2.1
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

Error: Can't have overlapping partitions.  


I ran testdisk and it found all the partitions, but I'm not extremely versed in linux and don't know how to back it up before I mess with it.  I'll give it a go in a bit.

THANKS!!!

---

### Post by drs305 on 2009-07-26
> **allenbina said:**
> 
I ran testdisk and it found all the partitions, but I'm not extremely versed in linux and don't know how to back it up before I mess with it.  I'll give it a go in a bit.

THANKS!!!

sorry about the fdisk command - forgot you had tried that and it wouldn't run. Testdisk has an option to save the current partition table - make sure you do that so your can restore it should any changes you make not work.

I'm not a partition table expert but the guide is fairly good at explaining things. Here is another step-by-step guide:

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

---

