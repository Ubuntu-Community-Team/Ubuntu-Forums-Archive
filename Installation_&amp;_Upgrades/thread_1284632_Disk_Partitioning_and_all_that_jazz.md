---
title: "Disk Partitioning and all that jazz"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by uWitchDoctor on 2009-10-06
Hello,

I have been stupid, i didn't know about Primary, Extended and Logical partitions and cannot now create more than 4 primary partitions on one drive, understandable I guess?

Anyway,

I have:

Primary: Windows XP
Primary: Ubuntu 9.04
Primary: Linux-Swap
Primary: Data

Is there a way I can sort this out and reorganise my drive and obtain 

Primary: Ubuntu 9.04
Primary: Windows XP
Extended:
-Logical: Linux-Swap (For Ubuntu)
-Logical: Data
etc... if needed.
-Logical:
-Logical:
-Logical:

(Does this make sense? or is it a stupid layout and I don't get the partitioning types)

Can someone clarify the definitions of Primary, Extended and Logical for me aswell?

Primary: One you can boot from?
Extended: A container for logicals?
Logical: Just data, a drive you cannot boot from?

...

I am getting a second hard drive soon aswell if that helps...

I wish I could just have ubuntu :( but I need Windows for whilst I'm at uni.

---

### Post by drs305 on 2009-10-06
Can you store all your Data somewhere else temporarily?

If so, the easiest way to accomplish this would be to:
1. Transfer your DATA to another drive
2. Delete the Primary swap partition
3. Delete the Primary data partition
4. Create an extended partition
5. Make a logical partition (sda5) for swap
6. Make a logical partition for data (sda6)
7. Configure Ubuntu for the new locations/UUIDs of swap and Data.

If you don't have anywhere else to put the Data, is your Data partition at least twice as large as the data it contains?

Windows must be in a primary partition.
Turn off swap before working on the partitions. (In gparted, highlight the partition, then Partition, Swapoff).
Unmount the data partition if it is mounted. Mounted partitions have a "Keys" icon next to them in the lower panel.

Here are two good guides:
[Partitioning basics]("http://ubuntuforums.org/showthread.php?t=282018")

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

