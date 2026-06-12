---
title: "NOOB Question: How to format and mount secondary data drive?"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by kapkorn on 2005-05-16
I am setting up my file server, drive 1 has ubuntu on it and drive 2 will be a secondary drtive that all my data goes onto.


How do I format that and Mount it for use within Ubuntu, then I will set up samba.


Help would be great! Thank You.

---

### Post by Xerampelinae on 2005-05-17
Assume you're second drive is called /dev/hdb

fdisk /dev/hdb    # sets up partitions
mkfs.ext3 /dev/hdb1  # formats first partition on second drive as ext3.  mkfs.reiserfs and other options exist too..
mkdir /mnt/data
mount /dev/hdb1 /mnt/data

Your drive is now accessible at /mnt/data.  To have it automatically mount the drive when you start, you have to add an entry in /etc/fstab for that drive.

---

### Post by camp on 2005-05-17
Hi,

Short list:
-run fdisk on the "new" disk and partition it as you wish.
-run mkfs or mkfs.ext3, mkfs.reiserfs... (depending on wich filesystem you want).
-make a directory to have as a mount point (e.g. /mnt/data)
-mount the new disk...

If the "new" drive is the second one on your PC, it's probably called "hdb". If you have a only one big partition on the whole drive, it will be "hdb1". And if you also formated it as a "ext3", your mount command should look something like this:

mount -t ext3 /dev/hdb1 /mnt/data

Your entry in /etc/fstab (if you want to have it automatically mounted) should look like this:

/dev/hdb1       /mnt/data           ext3    defaults        0       2

Hope this help!
/JC

---

