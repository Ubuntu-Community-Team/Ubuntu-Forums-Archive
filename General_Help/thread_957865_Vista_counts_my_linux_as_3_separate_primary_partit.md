---
title: "Vista counts my linux as 3 separate primary partitions?"
date: 2008-10-24
forum: General Help
---

### Post by Castlef on 2008-10-24
Hey I was wondering.. I have xp, and ubuntu installed on a computer. On the ubuntu part i have a partition for the root files system, the /home folder... and the swap folder.

My question is aren't the home folder and swap folder NOT primary partitions? isn't a primary partition the bootable one on the root drive? If so why is vista counting it as 3 seperate primary partitions... 

because now I can't install vista as a 3rd OS since it says there are 4 including the xp one.

Or will I have to just install the windows OS's first and then linux last?

---

### Post by The Cog on 2008-10-24
I can't be sure without seeing the output of fdisk -l, but they could be either. 

Original IBM PCs could only have 4 partitions. These are now known as primary partitions. Later, as disks got bigger and more partitions were wanted, they invented a partition type called an extended partition. Any one of the 4 primaries can be configured as the extended partition. The extended partition acts as a container for further logical partitions (up to 64 partition descriptions I think) and has its own partition table inside along with all the logical partitions. Since the disk always has 4 entries in the primary partition table (whether used or zero size), these are always numbered 1-4 and the logicals are always numbered 5 upwards.

---

### Post by jerome1232 on 2008-10-24
And unfortunately for you, vista MUST be on a primary partition, Linux doesn't care it if it's on a logical (inside an extended partition) or a primary partition.

Primary partitions are labeled sdx1, sdx2, sdx3, and sdx4. sdx5 and higher are logical partitions.

---

### Post by louieb on 2008-10-24
> **Castlef said:**
> My question is aren't the home folder and swap folder NOT primary partitions?

 /home can be just folder in the / (root) partition or it can be in a partition by itself (primary or logical). Same things for swap it can be a file inside the root partition or it can be in its own partition (again it can be in a primary or logical partition).

Just depends on how you set it up.    

> Or will I have to just install the windows OS's first and then linux last?                                                           Generally thats the easiest way.

---

