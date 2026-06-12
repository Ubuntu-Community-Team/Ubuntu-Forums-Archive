---
title: "trying to create partition"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by eyebrowman92 on 2005-12-26
on my hda theres a windows partition with an nfts filesystem and im trying to shrink it so i can install ubuntu. problem is after i resize it, make a new partition, when i press apply it says a device was busy. what does this mean?

---

### Post by eyebrowman92 on 2005-12-26
anyone....

---

### Post by \root\home\ on 2005-12-27
First of all you need to make unused space, If you have 40 gb Hard disk and you are using it like C:\ for Win XP with NTFS file system you can cut from that 40 GB 5 gb with Partition Magic and make unused space. Than when you start ubuntu installation use manager to create swap and ext3 partition. For swap use 2 x size of your RAM memory.

---

### Post by Thunk on 2005-12-27
I'm confused. Are you trying to install Ubuntu as dual-boot with windows? Because if you are, you don't need to create new partitions for it, the installation process will guide you through re-partitioning and distribution of free spcae.

---

### Post by Herman on 2005-12-27
What partitioner are your using, eyebrowman?
Gparted should be able to do that easily, on the 'Breezy' live CD.   :D (Herman)
Edit: Thunk is correct, there is a good partitioner in the install CD that works fine, that's the one I normally use too.

---

