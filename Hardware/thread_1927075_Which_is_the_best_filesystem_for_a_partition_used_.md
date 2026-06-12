---
title: "Which is the best filesystem for a partition used for storing files?"
date: 2012-02-17
forum: Hardware
---

### Post by Uewd on 2012-02-17
Hello,
When I used to have dual of Windows and Linux, the storage partition was set to be NTFS, which may get fragmented over time, but it will be accessible by both Windows and Linux. But now after switching to Xubuntu and removing Windows, there is a partition on which Xubuntu is installed and the other on which I want to store my files and I don't know which filesystem to use for it.

Any ideas?
Thank you. :)

---

### Post by ahallubuntu on 2012-02-17
If you EVER plan to use Windows again with your data, stick with NTFS.  If not, or you feel you'll always be able to boot a Linux CD or something to access your files, I'd go with ext4.

On my laptop, I'm using Truecrypt to encrypt my big data partition and have NTFS on top of that.  I'm definitely losing some performance, but I still occasionally use Windows, so I live with that to have universal access.  I have tried the ext2 driver for Windows but found it lacking.  By contrast, NTFS access in Ubuntu has proven to be extremely reliable.

One issue with NTFS in Linux: slow write times for huge files.  Also, NTFS access will load your CPU a little.

---

### Post by JRV on 2012-02-17
I use FAT32, it works good unless you have a file over 4 gig.

---

### Post by ahallubuntu on 2012-02-17
Yes, and since I have lots of files larger than 4GB (try partition backups), FAT32 is useless to me.  I don't want ever to be in a position where a filesystem can't be used because the file is too big.

I don't think Linux does any journaling with NTFS partitions, but Windows does, and in that regard, if  you use Windows at all, NTFS is a far superior filesystem to FAT32, which has no jouraling.  (Journaling helps you recover from crashes without data loss.)

---

### Post by CivilizationII on 2012-02-17
If you don't want to access your partition directly from windows, i recommend EXT4, really fast and secure. A real success from Linux.

Otherwise, but rather more complicated, FreeNAS and a ZFS partition (secured against physical damages on the disk) is a big temptation. Of course, this is implying a virtualized os from your Linux box, not that hard, but also not the simplest solution.

---

### Post by Uewd on 2012-02-18
Thank to all of you for replying.
I now have that partition as EXT4, I think I'm not planning to use Windows again, and if I wanted to do, I will backup my files and change it into NTFS. I'm now feeling comfortable when using EXT4.

---

