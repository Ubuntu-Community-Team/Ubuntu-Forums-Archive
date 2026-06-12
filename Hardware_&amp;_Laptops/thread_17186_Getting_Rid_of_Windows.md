---
title: "Getting Rid of Windows"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by jbrader on 2005-02-26
I have 2 windows partitions on my disk as well as the ext3 patition where Ubuntu lives. I've completly stopped using windows and was wondering if there's an easy way to reformat the partitions as ext3 and have them automatically mounted when I log in.
Thanks.

---

### Post by doitashimashite on 2005-02-26
First check which partitions are currently assigned to Windows:

sudo fdisk -l /dev/hda

will give you a list of partitions (use hdb if your harddisk is primary slave).

Then, if you know what you are doing, use fdisk to remove these two partitions, and make a new one, partition type 83. If you're not sure, then use a partitioning tool.

You can format this new partition by executing

sudo mke2fs -j /dev/hdaX

(change X into the new partition number).

The "-j" parameter will give you an ext3 partition.

Finally, in /etc/fstab you add a line like this:

/dev/hdaX       /               ext3    defaults    0       0

(X = partition number)

---

### Post by doitashimashite on 2005-02-26
Correction to my previous post:

/dev/hdaX / ext3 defaults 0 0

this will mount your partition to the root directory - don't use it like this!

Suppose the directory you want to mount this new partition under is /mnt/newpartition, then use this line in /etc/fstab:

/dev/hdaX     /mnt/newpartition     ext3      defaults      0      0

(change X into partition number)

---

### Post by jbrader on 2005-02-26
Perfect, that worked great.

---

