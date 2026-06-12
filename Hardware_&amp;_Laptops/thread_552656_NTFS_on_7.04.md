---
title: "NTFS on 7.04"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by And1945 on 2007-09-16
Hello

Im sitting on my dads laptop, and he wants ubuntu since he's fed up with windows. 

Anywho. It installs no problem, but there is a huge problem though.

He has 2 partitions on his harddrive, plus an external drive. The primary partition on his laptop is now ext3 running ubuntu 7.04 x64 amd. But the others are NTFS. The problem is, how to make folders and such on that. That I do not understand. I have tried the HOWTO with ntfs-3g, all I got was this error:

> (gedit:10947): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


What to do?

An automated setup with mounting the ntfs drives would be prefered since I dont really want to move all his data to my computer and then make his drives into ext3.

Thanks.

---

### Post by pay on 2007-09-16
If you only want to read the partitions, then you can mount them with this```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```Change hda1 to what the xp partition is. Or use this guide for read/write support [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by And1945 on 2007-09-16
Nice! So there was no point in reading all those guides with ntfs-3g and fuse?

Thanks :)

---

### Post by justin whitaker on 2007-09-16
> **And1945 said:**
> Nice! So there was no point in reading all those guides with ntfs-3g and fuse?

Thanks :)

Well, you learned something, right? :)

---

### Post by And1945 on 2007-11-30
> **justin whitaker said:**
> Well, you learned something, right? :)

I did... I _am_ trying.

I really want to learn this. Way better than windows.

---

