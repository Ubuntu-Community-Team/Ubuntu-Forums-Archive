---
title: "Partition table entries are not in disk order"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by Zill on 2005-12-26
I have just installed Ubuntu 5.10, taking the opportunity to change my partition sizes from the old Mandriva installation and to introduce a new partition for backups.  The output from fdisk -l /dev/hda is shows below:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux  ---/
/dev/hda2            1217        9729    68380672+   5  Extended  
/dev/hda5            9608        9729      979965   82  Linux swap / Solaris  ---Swap
/dev/hda6            3528        9606    48829536   83  Linux  ---/home
/dev/hda7            1217        3527    18563044+  83  Linux  ---/bak
Partition table entries are not in disk order

Although everything seemed to install correctly, I am concerned that the last statement "Partition table entries are not in disk order" indicates a problem.  Although I _thought_ I entered my partitions sequentially, it seems that I didn't do it correctly.

My first partition, /dev/hda1, was set as a physical partition, and the rest logical.

Can anyone advise if I need to re-do my partitioning and installation and, if so, how do I ensure that all the partitions are in the correct order.  Should I have used physical partitions throughout?

Many thanks,

Zill

---

### Post by Sef on 2005-12-26
No need to do anything.   It's just the way it formats.  I am sure there is a reason it formats that way, but I don't know it.   It shows you the way it does, so it is easier to follow, if you need to fix or adjust something.

---

### Post by Sutekh on 2005-12-26
[QUOTE=Zill]
Partition table entries are not in disk order
[/QUOTE]
This does not indicate a problem, fdisk is just telling you that the partitions are listed in that order, but do not appear on the disc in that order.  No big deal, my partition lists says the same thing.

---

### Post by roelofs on 2005-12-28
If you wish, you can fix the partition order via fdisk's expert mode ("x").  The "f" option fixes the order; then do the usual "w" to write/quit.  If you do so, however, make sure you edit your fstab accordingly *before* you reboot, or you're liable to panic the kernel/init/whatever when it tries to mount the wrong partition somewhere.  (That's not fatal, but you'll have to boot from a floppy or CD/DVD, mount the root partition, edit fstab, sync, umount, reboot, etc.  Tedious.)

```
Command (m for help): x

Expert command (m for help): m
Command action
   b   move beginning of data in a partition
   c   change number of cylinders
   d   print the raw data in the partition table
   e   list extended partitions
   f   fix partition order
   g   create an IRIX (SGI) partition table
   h   change number of heads
   m   print this menu
   p   print the partition table
   q   quit without saving changes
   r   return to main menu
   s   change number of sectors/track
   v   verify the partition table
   w   write table to disk and exit

```

---

### Post by Zill on 2005-12-29
Thanks for all the info folks.

I thought I needed to understand more about the partitioner so I experimented with the settings and have now re-installed with a logical order.  Seems like I was confused by mixing up "beginning" and "end" of the whole disk area and the free area!

Now my fdisk shows a sensible order with no error message so I have reinstalled ubuntu and automatix.  My next challenge is to get the new installation to talk to my other (mandriva) PC via NFS!  I may need to post another message for further advice on this one ;-)

Thanks again for the responses :-)

Zill

---

