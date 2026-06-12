---
title: "Can't format USB as ext3/ext4"
date: 2011-06-15
forum: Hardware
---

### Post by linusnorton on 2011-06-15
Hi Guys,

I have a 32Gb USB drive it came formatted as fat32 and I tried to use the right-click->format option to set it to ext4. It appears to finish but when I try to double click it I get an error saying it cannot mount the system.

I reformatted back to fat32 and it worked, I could create files without problems.

Then I tried ext2 which also worked.

Then I installed gparted and tried ext3 which had the same problem as ext4.

The fdisk -l is as follows:


Disk /dev/sdb: 32.2 GB, 32233226240 bytes
255 heads, 63 sectors/track, 3918 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3919    31476736   83  Linux

I also tried mounting as root but that didn't help either.

Any ideas?

---

### Post by linusnorton on 2011-06-15
I fixed the issue by running this command:

e2fsck -b 32768 -B 4096 /dev/sdb1 -y

I believe it used a backup inode to rebuild the main inode

---

### Post by linusnorton on 2011-06-15
Oh no!

It has turned it into an ext2 partition!

---

