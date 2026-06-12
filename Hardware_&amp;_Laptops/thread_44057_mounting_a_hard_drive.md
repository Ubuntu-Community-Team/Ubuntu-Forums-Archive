---
title: "mounting a hard drive"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by lordmcdra on 2005-06-24
I removed this questions from the beginner's section due to this question being too advanced.  I have a question about mounting drives.  I used the command *sudo mount /dev/sda5 /mnt/Zero -t ntfs -o umask=000* to mount a particular hard drive but I have read only access as a basic user.  How do I change the drive from read-only access to write access.  The answer I received is that ntfs is unsupported by ubuntu for write access.  The most one can do with a mounted ntfs drive is read support.

---

### Post by frodon on 2005-06-24
ok
NTFS is a proprietary format (windows) that's why write feature is not really supported on linux for the moment, if you want a full support of your hard drive you must use the FAT32 format on your hard drive. However it's possible to write on NTFS partition using captive project but it's very slow and at your own risk, if you can store your datas temporarily on another hard drive, do it an format your partition using FAT32.
But if you really want to write on NTFS have a look here : [http://www.ubuntuforums.org/showthread.php?t=21195&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=21195&highlight=ntfs)

---

### Post by andlinux21 on 2005-06-25
well I have a 8Gig hard drive that i installed SuSE 9.0 on will Ubuntu be able to see that or do I have to mount it?

---

