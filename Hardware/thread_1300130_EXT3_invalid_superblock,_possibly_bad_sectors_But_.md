---
title: "EXT3 invalid superblock, possibly bad sectors? But the data seems to be OK"
date: 2009-10-24
forum: Hardware
---

### Post by vcppp_p on 2009-10-24
Hi,
 I'm experiencing big problems with my HDD, SATA 500GB, with few ext3 partitions. Recently Ubuntu started throwing some errors while trying to mount the filesystem, ending up with "initramfs" console and lot's of "STATUS: DRDY ERR" messages... anyway, finally I found a kind of solution... using testdisk from LiveCD I was able to find out superblock backups. Later, I found this blog entry: [http://blogs.sans.org/computer-forensics/2009/10/05/mounting-images-using-alternate-superblocks-follow-up/](http://blogs.sans.org/computer-forensics/2009/10/05/mounting-images-using-alternate-superblocks-follow-up/) thanks to whitch I was able to mount the filesystem (in readonly mode however) and browse it from LiveCD... (The command I used was "sudo mount -t ext2 -o loop,ro,sb=131072 /dev/sda1 /media/abc") ... now, is that possible to repair the "first" (most important) superblock to make the HDD work fine again, or do I really have to buy new HDD, copy all the data there and use the new one? I don't like that idea, especially the "broken" HDD is no older than a year and a half, or so ...

thanks in advance

---

### Post by lensman3 on 2009-10-24
Will the sda1 drive mount if you do:

su mount -t ext2 -o sb=131072 /dev/sda1 /media/abc"

You don't want to mount it one the loop interface.  You should be able to pass the -o options to the mount command.


If it does work, then put the working line (without the sudo) in the file "/etc/fstab".  And reboot.  Tje fstab file is used by the kernel to mount the partitions.  

Take a look at tune2fs.  It has some superblock "features".  "mkfs" might have the ability to move the first superblock, but would probably require a reformat.

---

### Post by vcppp_p on 2009-10-24
Hi, are you sure is that safe to mount my EXT3 filesystem as EXT2 in non-readonly mode? I wouldn't like to damage my data which is all there!! I'll have a look at tune2fs, thanks

---

