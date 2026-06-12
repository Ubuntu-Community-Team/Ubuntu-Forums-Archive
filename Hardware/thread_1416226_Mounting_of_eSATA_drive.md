---
title: "Mounting of eSATA drive"
date: 2010-02-25
forum: Hardware
---

### Post by Infil on 2010-02-25
First and foremost: I have searched the forum here and have not found answers to these questions.

I have an external hard drive (a normal hard drive in separate housing connected to the eSATA if it matters) and I have two partitions. One of the ext4, and an on NTFS. The ext4 partition I am interested in mounting.

If I normally add it in /etc/fstab with umask and fmask and all that:

1) If I put other permissions (eg. +x) to a file on the external drive, will they be reset at the next reboot?

2) When the disk is not connected (eg. when I'm on the go), will the system produce error messages?

3) Can I do something so that the disk is still listed in the sidebar in Nautilus, and it still gets an icon on the desktop?

Alternatively, I have seen that it is possible to set up rules in HAL. Should I do it instead? How do I do it in that case?

Initially, I wouldn't have to do anything, but for some reason I don't get write access to the disk when the system mounts it automatically. Thanks for any help.

---

