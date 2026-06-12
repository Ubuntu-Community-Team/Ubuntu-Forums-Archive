---
title: "How To:  Move Unallocated Space from Primary to Extended Partition"
date: 2010-06-19
forum: Hardware
---

### Post by u2rcrazy on 2010-06-19
[SIZE=4][I]How To:  Move Unallocated Space from Primary to Extended Partition
[SIZE=2]
I would like to utilize space that I have in a previously used (now unallocated space) Primary partition, and add it to another block of [/SIZE][/I][/SIZE][SIZE=2]*unallocated*[/SIZE][SIZE=4][I][SIZE=2] application.  I have provided some more information that will help you [SIZE=4][SIZE=2]understand.  See picture below for more info.

[/SIZE][/SIZE][/SIZE][/I][/SIZE][ATTACH]160887[/ATTACH]
[SIZE=4][I][SIZE=2][SIZE=4][SIZE=2]
How can I perform there tasks?  I look forward to hearing your thoughts.

Truly, 
Bob:guitar:
[/SIZE]

[/SIZE][/SIZE][/I][/SIZE]

---

### Post by Sharang.d on 2010-06-19
> **u2rcrazy said:**
> [SIZE=4][I]How To:  Move Unallocated Space from Primary to Extended Partition
[SIZE=2]
I would like to utilize space that I have in a previously used (now unallocated space) Primary partition, and add it to another block of [/SIZE][/I][/SIZE][SIZE=2]*unallocated*[/SIZE][SIZE=4][I][SIZE=2] application.  I have provided some more information that will help you [SIZE=4][SIZE=2]understand.  See picture below for more info.

[/SIZE][/SIZE][/SIZE][/I][/SIZE][ATTACH]160887[/ATTACH]
[SIZE=4][I][SIZE=2][SIZE=4][SIZE=2]
How can I perform there tasks?  I look forward to hearing your thoughts.

Truly, 
Bob:guitar:
[/SIZE]

[/SIZE][/SIZE][/I][/SIZE]

Well i did it just today on Partition Magic 8.0 [but on Windows..sigh]

---

### Post by ronnielsen1 on 2010-06-19
Use a live cd, click on the partition that you want to resize and slide it over

---

### Post by u2rcrazy on 2010-06-19
[Sharang.d]("http://ubuntuforums.org/member.php?u=1095558") and [ronnielsen1]("http://ubuntuforums.org/member.php?u=61926"),

I tried to use the Ubuntu Live CD, but it won't allow me to do anything with either one of the two Unallocated Spaces.  See the screen shots below.  You'll see that I have selected each of the Unallocated Spaces (separate screen shots).  

[CENTER][ATTACH]160935[/ATTACH]     [ATTACH]160934[/ATTACH]
[/CENTER]


The only options that shows up in the option of creating a new partition.  When attempt the create a new partition, I'm confronted with the error message that states that there is a 4 Partition Limit (see screen  shot).

[CENTER][ATTACH]160933[/ATTACH]
[/CENTER]

Do you know of a free program in either Windows or Ubuntu that would merge the unallocated space on the Primary Drive (where Windows 7 resides) to the unallocated space on the Extended Drive (where Ubuntu is)?  I see so many free partitioning programs (see screen shot below) when I open when I search on Ubuntu's Software Center, but I can't pinpoint which one will be able to do this function. Thanks in advance!  =)

[CENTER][ATTACH]160936[/ATTACH][/CENTER]
 
Bob Marly):P

---

### Post by efflandt on 2010-06-19
You cannot move or resize a partition that is in use.  So you need to do this from live system on CD or USB, and temporarily disable swap on that drive with **sudo swapoff /dev/sda6**.

Then you should be able to resize the extended partition,  move the logical partitions in it down, and put a logical partition in the unclaimed space of the extended partition.  What I am not sure of is whether the logical partitions will automatically move down when you resize the extended partition.

Note that moving a partition can take a very long time (many hours) trying to safely move all the bits.  So you may want to make sure that power saving settings will not put your PC into suspend or hibernate, and do it overnight.

---

### Post by oldfred on 2010-06-19
You also have to move the extended to include the unallocated space  first. All logicals have to be inside the extended and with an extended you can only have 3 additional primary partitions that are not in the extended.

---

### Post by u2rcrazy on 2010-06-20
This worked.  Thanks:p




[LIST]
[*] Before
[ATTACH]161011[/ATTACH]
[*] After
[ATTACH]161010[/ATTACH]
[/LIST]

---

