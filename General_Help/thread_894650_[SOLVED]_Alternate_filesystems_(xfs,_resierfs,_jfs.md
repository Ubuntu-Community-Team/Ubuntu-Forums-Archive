---
title: "[SOLVED] Alternate filesystems (xfs, resierfs, jfs) causing kernel panics?"
date: 2008-08-19
forum: General Help
---

### Post by jerome1232 on 2008-08-19
Due to a goof up with DD recently I decided to reinstall Ubuntu. Generally I partion as so:

sda 250 GB
sda 5 logical / ext3 ~15-20 GB
sda 6 locical swap   ~512 MB - 2 GB depends if I want to try hibernate
sda 7 logical /home ext3 ~200 GB (the rest)

but this go around I thought I'd have a data partition where I mostly store my DVD iso images and other large files (videos, large tar archives) and I've heard xfs is great with large files. I've also heard jfs is fast in general so why not try it.

sda 250 GB
sda 1 / resierfs 20 GB
sda 2 swap 2 GB
sda 3 /home jfs 30 GB
sda 4 /mnt/data xfs the rest of the drive

sdb 160 GB(a usb drive for backups)
sdb1 xfs 160 GB

My new system would just kernel panic after kernel panic after I boot into it(usually not enough time to do a apt-get update && apt-get upgrade)

So I figured the only thing different I did was the file systems and I went back to ext3 on everything but sdb. It fixed it.

Now here I am running photrec from a live cd, copying to sdb (xfs) and I kept getting hit with kernel panics until I formated it to ext3.

Is this a common problem, should I try testing see if my system works with purely xfs and file a bug report if it continues to crash my system?

---

### Post by prince_niceguy on 2008-08-19
I am using xfs as my home directory with reiserfs as root. On another I have ext3 as root and xfs as home dir. I do not think it is common problem.

The only problem I have got is that grub cannot be installed on xfs and it creates kernel panic.

---

### Post by jerome1232 on 2008-08-19
I guess it was a fluke.


Reinstalled using
/ jfs
swap
/home jfs
/mnt/data xfs
 and all is well. *shrugs shoulders*

Time to do some massive file copying and see if there's a human noticeable difference.

---

