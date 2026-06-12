---
title: "root file system not defined on partition"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by Rdogg on 2005-12-06
AM tryin to install a dual boot xp and breezy badger

Used partition magic to partition the disk

On installing the breezy badger all was well until i came to partitioning th disk on the instalation disk

i choose to do so manually i picked out the 5gb partition for the breezy bagger  was told i had no root file system defined and that i should correct this from the partitioning menu 

am lost any help

thanks

---

### Post by Leif on 2005-12-06
if you don't know how to partition, it's probably best if you just allocate some free space and then let ubuntu auto-allocate. otherwise, you need to assign at least two partitions : root (/) and swap, and you need to mark them as such. swap should be about the same size as your ram, and the rest can go to /.

there are better ways of doing a manual partition, if you want to know how, search the forums.

---

### Post by mike4ubuntu on 2006-01-02
How do you allocate swap partition in the install partitioner when I manually edit the partition table?  I don't see an option to do that.  when I create a partition, I see mount points such as /, /home, /boot, /var, and so on, but nothing for swap.

---

### Post by scotartt on 2006-01-02
[QUOTE=mike4ubuntu]How do you allocate swap partition in the install partitioner when I manually edit the partition table?  I don't see an option to do that.  when I create a partition, I see mount points such as /, /home, /boot, /var, and so on, but nothing for swap.[/QUOTE]

Choose "swap" as the file system type and the mount point is taken care of for you.

---

