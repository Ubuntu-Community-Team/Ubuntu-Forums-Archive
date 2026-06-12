---
title: "bad superblock"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by Chemist on 2006-12-22
Hi guys

I've formatted my second hard drive as ext3 through the terminal and I'm having trouble mounting it. 

I get the following error 

> Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.

I've tried to run the following command 

> will@will-desktop:~$ sudo e2fsck /dev/hdb1 -c
e2fsck: No such file or directory while trying to open /dev/hdb1
/dev/hdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I'm a bit confused by it mentioning ext2 when the hard drive is definitely ext3.  I have tried to run it with a different superblock as mentioned but I get the same error. Can someone please help me????

---

### Post by kidders on 2006-12-22
Hi there,

Ext2 and Ext3 are the same filesystem ... except that one is journalised.

Are you sure you have the device path right? **"e2fsck: No such file or directory while trying to open /dev/hdb1"** seems to suggest that you haven't.

---

### Post by mrsudo on 2008-02-09
anyone have a solution to the problem.  i seem to be having the same problem but mine is my /home partition.

---

