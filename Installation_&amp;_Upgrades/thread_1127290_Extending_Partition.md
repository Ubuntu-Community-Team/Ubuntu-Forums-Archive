---
title: "Extending Partition"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by ravi_buz on 2009-04-16
Hai.
i have 2 Hdd .1st HDD has windows and ubuntu and 3 more ntfs partition, and the other Hdd contains software in one partition. I gave 11 gb to ubuntu and now want to give additional 5 gb to it from my 2nd HDD is this possible , i have gparted live cd, If its not possible how to give 5 gb from the 1st HDD .

---

### Post by Mark Phelps on 2009-04-16
Using standard partitioning, it's not possible for a partition to span physical drives -- doesn't matter which partitioning tool you use.

---

### Post by ajgreeny on 2009-04-16
You can do either of these options very simply.  Probably the simplest is to resize the partition in your 2nd drive down to whatever you want, and then make a new ext3 partition in the unallocated space which can be mounted each time you boot ubuntu by adding a line to /etc/fstab.

Boot your ubuntu live CD and go to System > Administration > Partition Editor.  There choose sdb and resize the existing partition and make a new one.  Now run ```
sudo fdisk -l
``` and you will see the current partition arrangement of your nachine.  You will need to make a new mount point in your installed ubuntu and edit fstab to include a line with the following format:-
```
/dev/sdb# /media/mountpoint ext3 defaults 0 2
```
You can use the UUID for the partition if you prefer, which is now the default for ubuntu, but the format is otherwise identical.  You will also need to make the partition yours (or you will only be able to write to it as root) with ```
sudo chown -R username:username /media/mountpoint
```

---

### Post by ravi_buz on 2009-04-16
> **Mark Phelps said:**
> Using standard partitioning, it's not possible for a partition to span physical drives -- doesn't matter which partitioning tool you use.
ok then how to expand it within the same HDD i will remove one of the partition in it and make it as ext3 , but how to add it to filesystem

---

### Post by ajgreeny on 2009-04-16
> 1st HDD has windows and ubuntu and 3 more ntfs partitionOK, so using the live ubuntu CD, delete one or more of the three ntfs partitions next to your main ubuntu partition, after copying any files you need, obviously.  Now you should be able resize your ubuntu partition by adding the unallocated space to it, assuming it is next to the ubuntu one.  If it is not adjacent, you will need to move partitions around perhaps, which can be done, but is a long winded job if they are large.  It would probably help to see a graphical display of your partition layout on sda1 from gparted, if possible.

Whatever you do to your partitions that contain important data, make sure you backup first.

---

