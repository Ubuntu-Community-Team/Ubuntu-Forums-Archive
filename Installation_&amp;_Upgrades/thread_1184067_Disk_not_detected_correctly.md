---
title: "Disk not detected correctly"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by gaurab on 2009-06-10
Hi,

I had installed Linux Mint on my laptop along with vista. Recently I wanted to install jaunty in the place of Linux Mint. 
But from the live CD when I wanted to repartition it won't show any existing partition. 

The hard drive is 120 gb but gparted would show 150 gb of unpartitioned and un formatted space.

I ran "fdisk -l" and it doesn't give anything, just returns the $ prompt back.

fdisk /dev/sda returns
Unable to open /dev/sda.
But I can mount all the sda1 through sda6 partitions and read then.

I also tried to run gparted from the terminal and the output is
==========================
libparted : 1.8.8
==========================
Can't have overlapping partitions.
And when it opens it shows 150 gb of unallocated space.

I haven't seen anything like this before. 
Please respond. I need some advice.

Thanks for reading,
Gaurab

---

