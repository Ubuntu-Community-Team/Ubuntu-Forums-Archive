---
title: "Error mounting /dev/sdb"
date: 2018-02-22
forum: Hardware
---

### Post by robertzito on 2018-02-22
I dont know where to begin, my FSTAB makes no mention of my third drive which wont mount.

---

### Post by TheFu on 2018-02-22
If you search for "ubuntu fstab", there is a how-to.  You'll have to manually edit the fstab and add a line for the new partitions.  
However, you probably do not want to mount the entire disk device - /dev/sdb.  You probably want to mount a file system that is inside a partition on the disk.  

To summarize:
/dev/sdb - whole disk
/dev/sdb1 - 1st partition which may or may not have a file system.
Use **mkfs** to create a file system (type you choose) on a partition, sdb1.
If you like, you can do most of these things using **gparted** or **parted**.

Then you can mount the partition inside the /etc/fstab file with the correct options for the file system type.  BTW, it would be best to use the UUID for mount, not the device (/dev/sdb1).  

If you have multiple partitions on the same drive, they are always numbered.  sdb1, sdb2, sdb3 ... often in the order of creation.  This works for GPT partition tables (required for 2TB and larger disks).  MBR/MSDOS partition tables are a little more complicated with extended, primary and logical partitions to work around some limitations.  It is much easier to use GPT on a new disk. There really aren't any downsides today for using GPT, even on smaller disks and many upsides.

And there are many reasons NOT to use the gdisks program.

---

