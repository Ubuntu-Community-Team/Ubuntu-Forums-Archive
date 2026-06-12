---
title: "Hard drive trouble."
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by eddorey2k3 on 2006-06-13
Hey,

So i'm currently using 2 hard drives. They're both too small to be used on their own (40gb per drive), but together 80gb is fine.

However. The space isn't adding up. What I'm trying to do, is have one drive so it is for mp3's (I'm thinking of adding video later), and another for system files and whatnot.

So at the moment, they're both mounted fine, but the total space isn't adding up to any where near 80gb (I know i'll lose 800mb for Swap, that's fine).

I have one drive mounted normally, as hda1, and the other mounted as hdc1, which should have just my music on. I have a fair amount (20gb) or so, so there should be about 20gb left on that drive and about 30gb left on the system drive. 

However, if i do Right-click > Properties in Konqueror, it's showing the free space as 30gb out of 37gb, with 17% used.

Any ideas? Anyone have a clue what I'm going on about? :razz: Do I need to reinstall with LVM? >_>

---

### Post by tonyr on 2006-06-13
Generate some more information.  
Run **gparted** (**System-Administration->Gnome Partition Editor**) and report 
what it says about partitions and sizes for the drives.

and/or

Bring up a terminal (**Applications->Accessories->Terminal**), enter these
commands:
```

df
fdisk -l /dev/hda
fdisk -l /dev/hdb

```

and post the results here.

---

### Post by eddorey2k3 on 2006-06-13
Sure thing.

df
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1            38804428   4942116  31891140  14% /
varrun                  254096       116    253980   1% /var/run
varlock                 254096         4    254092   1% /var/lock
udev                    254096       112    253984   1% /dev
devshm                  254096         0    254096   0% /dev/shm
lrm                     254096     18856    235240   8% /lib/modules/2.6.15-23-386/volatile
/dev/hdc1             39516436  19613492  17895616  53% /home/ed/mp3
/dev/hdb                  1200      1200         0 100% /media/cdrom0

```

The 2 fdisk commands return "Cannot open /dev/hda1" etc.

---

### Post by tonyr on 2006-06-13
[QUOTE=eddorey2k3]Sure thing.
The 2 fdisk commands return "Cannot open /dev/hda1" etc.[/QUOTE]

Did you type **fdisk -l /dev/hda1** or **fdisk -l /dev/hda** (no **1** at the end).

I mis-guessed your configuration. I should have said

```

fdisk -l /dev/hda
fdisk -l /dev/hdc

```

Be aware that to some people 40 Mbytes means 40 million, not 40 x 1024.  There
will be some discrepancy in numbers because of this.
The **df** result shows 38804428 1K blocks (1K=1024) for hda1, and
39516436 1K blocks for hdc.  Do the math.  You can also figure out the true
capacity of the drive from the **fdisk -l **results when you get them.

When the filesystem were created on hda1 and hdc1, some disk space was 
taken for **inodes** (file blockmaps), and 5% or 10% was reserved for 
emergency/admin/problem-recovery purposes.

I don't know what Konqueror uses to report disk space.

---

