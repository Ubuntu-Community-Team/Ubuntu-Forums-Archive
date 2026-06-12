---
title: "Defragmentated the wrong partition !"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2006-02-15
Hi , 

I have a 80 GB HD with XP pre-installed on 1 partition, also  with an other pre-installed partition with W95 if XP craches.

Mmmm, oke I gave XP 10 GB and installed Ubuntu.
I gave Ubuntu 10GB Ext3, swap 1 GB and I put /Home on the rest.

But ! I defragmented the W95 part on the end of the HD !

Is it possible to get it back ? Because probable only the head of the HD with start and end is gone ? with the info about the W'95.

The W'95 was FAT3 and I made it EXT3.

---

### Post by aysiu on 2006-02-15
Defragmenting doesn't damage a drive's contents--it just moves bits and bytes around.

Reformatting, however, destroys all information on a drive or partition. If you overwrote a FAT32 partition and formatted it as Ext3, your FAT32 partition is gone, and so is all the information that was on it before.

---

