---
title: "extending my EXT3 ubuntu partition"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by rvt20s on 2009-10-27
ok so I have ubuntu installed on a 4GB primary partion then next to that is my 139GB vista partition, then at the end is 5.86GB of Unallocted disk space.

my question is can I increase my ext3 ubuntu partition and use that unallocated space to make it bigger. how do I do it?
Thanks for any help
Rob

p.s when I load Gparted in ubuntu I cant resize my ext3 partition...I take it because its in use.

---

### Post by donsy on 2009-10-27
You need to boot from the live CD and use its version of Gparted. Click the partition to select it, then from the Edit menu select Resize and you'll be able to drag the right arrow to resize the partition.

---

### Post by oldfred on 2009-10-27
If Vista is between your Ubuntu and empty space you have a problem.

If you move or resize Vista with Gparted it may not boot and will required filecheck or other maintenance to get it going again. 

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

It is still better to shrink the Vista partition from within Vista. I would recommend shrinking Vista and just reinstall Ubuntu in the new space. leave the first 4gb partition as a data partition, if you delete it you may renumber partitions and cause other issues.

---

### Post by earthpigg on 2009-10-27
if possible, use a windows partitioner to shift the vista partition over to the right.

then using system -> admin -> partition editor on a LiveCD, expand ubuntu's partition.

you ***can*** use gparted on vista partitions, but look at #9 [here]("http://gparted.sourceforge.net/faq.php") first.

---

### Post by drs305 on 2009-10-27
> **rvt20s said:**
> ok so I have ubuntu installed on a 4GB primary partion then next to that is my 139GB vista partition, then at the end is 5.86GB of Unallocted disk space.

my question is can I increase my ext3 ubuntu partition and use that unallocated space to make it bigger. how do I do it?
Thanks for any help
Rob

p.s when I load Gparted in ubuntu I cant resize my ext3 partition...I take it because its in use.

This guide will give you help. It was written for installs that ended up at 2.5GB, but the principles and procedures are the same:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by donsy on 2009-10-27
> **donsy said:**
> You need to boot from the live CD and use its version of Gparted. Click the partition to select it, then from the Edit menu select Resize and you'll be able to drag the right arrow to resize the partition.

Sorry, I gave you the wrong information. I failed to notice in your post that your Vista partition was located after the Ubuntu partition. My humble apologies.

---

