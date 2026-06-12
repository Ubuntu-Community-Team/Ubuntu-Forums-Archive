---
title: "Is there a way to recover from doing 'disklabel'"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by GeneM on 2007-10-23
I have mistakenly used disklabel on a hard disk I did not want to wipe.  There are three partitions on the drive.  I do not care about the first but I would like to recover the last two.  Is there some way to recover them?

Gene

---

### Post by tobiasz.cudnik on 2008-05-08
You have to mount them directly. Like this:
```
sudo mount -o loop,offset=16384 file mnt
```
This mounts FAT32 partition which is on whole drive.
From: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Refer to document above for details, particularly "Mounting partitions on the image".

It worked for me, but i had only 1 fat.

---

