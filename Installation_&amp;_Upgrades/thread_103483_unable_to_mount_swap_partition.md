---
title: "unable to mount swap partition"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2005-12-14
I'm using Ubuntu Breezy 5.10, Virtual Server 2005, and erasing a new hard driver using LVM.

When trying to write the partition table, the partitioner doesn't want to mount the swap partition.

"The attempt to mount a filesystem of type swap in LVM LG Ubuntu LV swap_1 at none failed.

You may resume partitioning from the partitioning menu."

Why am I able to mount all the other partitions, but not the swap?

Thanks

---

### Post by taurus on 2005-12-14
What does your /etc/fstab look like anyway???  You can mount your swap by hand if you wish...

swapon /dev/hda2 (or whichever the partition is...)

---

### Post by kacheng on 2005-12-14
Unfortunately, I'm not nearly that far along.

I'm still trying to install the system and this is the Partitioner dialog of the installation CD that I'm stuck at.  The base system is not installed yet.

---

