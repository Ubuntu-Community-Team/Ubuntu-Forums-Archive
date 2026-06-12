---
title: "partition trouble"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by iconzero36 on 2009-04-03
I recently bought an Asus eee pc 1000, linux version. The installed OS was xandros... of course i had to get rid of it. I am actually a windows user that has taken a huge interest in linux. I installed linux fine, but im having partition issues. 

Out of the box 40 gig ssd was partitioned into 2 parts: 8g and 32g etc. I thought when i installed ubuntu i used the whole drive for install. i guess i didnt. it was installed on the 8g partition. 

1. im unsure if im able to choose to save to the other partition.
or
2. is there a way to consolidate both partitions?

---

### Post by logos34 on 2009-04-03
You want to delete the larger partition and then grow the smaller to reclaim the unallocated space (if /swap is between the two you'll have to delete it and recreate a new one at the end of the disk.  Don't forget to edit /etc/fstab).  Since / cannot be mounted during resize, you'll have to boot a live USB of Gparted or a rescue/utility iso like Parted Magic (my fav):

[http://partedmagic.com/documentation/116-creating-the-media.html](http://partedmagic.com/documentation/116-creating-the-media.html)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

(or maybe you installed using a ext. usb cdrom, in which case use gparted on ubuntu live cd)

---

### Post by iconzero36 on 2009-04-03
thanks man i really appreciate it. i will definitely dl gpart and try to do exactly what u said. theoretically i understand you but mind you im new to linux! :)

---

### Post by Mark Phelps on 2009-04-03
If your machine doesn't boot after you remove and resize partitions, it's most likely because some of the lines in your menu.lst file are incorrect.  If you look in there, you will see lines containing "UUID=".  These probably refer to your first partition.  The UUID of the second partition is different.  

Use the "blkid" command to get a list of UUIDs.

You will then have to go to console mode, edit the menu.lst file, and substitute the new UUIDs for the old UUIDs.

---

### Post by iconzero36 on 2009-04-03
ok i dl used the gparted...

new problem: maybe i dont understand what an ssd drive i have. out of the box it had to "partitions" or "drives". the 8g and 32g. now im thinking they were actual drives because in gparted i was able to select both "drives"? the top left was a drop down menu:/dev/sda and dev/sdb. 

does that mean to drives or partitions

---

### Post by iconzero36 on 2009-04-03
... (Move up to top of thread) :)

---

### Post by logos34 on 2009-04-03
these two commands should give us some info on your storage:

sudo fdisk -l

sudo lshw -C disk

---

### Post by Mark Phelps on 2009-04-03
If you do an "fdisk -lu" and get a result like:
/dev/sda1 ...
/dev/sda2 ...

They are partitions on one drive.

If you get a result like:
/dev/sda1
/dev/sdb2

They are drives.

With partitions, the trailing number changes; with drives, the letters change.

---

### Post by iconzero36 on 2009-04-04
okay so they are definitely drives.

how do i save to the other drive? like how in windows, when i choose to save to the other drive, it is indicated by a drive letter. am i able to do that in ubuntu?

---

### Post by iconzero36 on 2009-04-04
...

---

### Post by logos34 on 2009-04-04
> **iconzero36 said:**
> okay so they are definitely drives.

how do i save to the other drive? like how in windows, when i choose to save to the other drive, it is indicated by a drive letter. am i able to do that in ubuntu?

As long as it's mounted, with the correct permissions and ownership, you should be able to drag and drop in Nautilus file browser (or konqueror, whatever).

what filesystem type is the larger partition (ext2/3? reiserfs?)

fdisk will show

---

### Post by Mark Phelps on 2009-04-06
> **iconzero36 said:**
> okay so they are definitely drives.

how do i save to the other drive? like how in windows, when i choose to save to the other drive, it is indicated by a drive letter. am i able to do that in ubuntu?

Ubuntu doesn't use drive letters.  To write to a drive, you first have to create a mount point in your filesystem, and then you have to mount the drive.

To provide a list of drives and partitions, do "fdisk -lu" (that's a lower-case L, not a one) in a terminal and post the results.

---

