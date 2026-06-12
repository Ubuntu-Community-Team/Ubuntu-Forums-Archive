---
title: "xp resize. Need help with fdisk"
date: 2008-08-12
forum: General Help
---

### Post by agim on 2008-08-12
Just resized a friends XP hard drive with ntfsresize, due to some bad sectors. Need to use fdisk to resize the partition. 

Two questions:

1) Can I just use GParted?
2) If not, how do I resize it with fdisk.


The original size of the partition was 66.68. With ntfsresize, we changed it to 47GB. I know the partition has to be a little larger, something like 47.2GB. And I "also need to "set the bootable flag for the partition if it existed before", which I assume it did.

Any help would be great.

thanks

---

### Post by sandysandy on 2008-08-12
first defragment the windows partition.

here is the gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by agim on 2008-08-12
I am familiar with GParted. My only concern is, if I use GParted, will the partition have the bootable flag set.

Here is the output after ntfsresize (which I used because of bad sectors).

Successfully resized NTFS on device '/dev/sda2'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.

---

### Post by agim on 2008-08-13
bump

---

