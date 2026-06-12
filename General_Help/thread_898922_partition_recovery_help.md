---
title: "partition recovery help"
date: 2008-08-23
forum: General Help
---

### Post by DaBomb on 2008-08-23
So I was going to increase the size of my Ubuntu partition but I made a mistake and messed up my WinXP partition.  This is what I did in GParted:

1. unmounted fat32 /dev/sda2 XP partition

2. realizing this is not what I wanted to do, I chose to format back to fat32

3. now it shows used space to be 22.04 MiB :(

I don't believe anything was erased or written over, and I hope I can restore my Windows partition to the way it was.

I've already ran PhotoRec to back up most of my files, but dealing with 175,000 files named with numbers is no fun.

I've decided to get some expert advice before making anymore mistakes

[IMG]http://c3d.dreamhosters.com/screenshots/partition08232008.jpg[/IMG]

sda1 is DellUtility
sda2 was my WinXP
sda3 is DellRestore

Hopefully someone has good news for me!

---

### Post by LateNiteTV on 2008-08-23
what do u mean when you say "format back to fat32"?

---

### Post by Diabolis on 2008-08-23
So what messed your partition up was to format it to fat?

Windows partitions are always NTFS, so maybe reformatting /dev/sda2 back to that file system will hopefully restore everything.

---

### Post by DaBomb on 2008-08-23
> **Diabolis said:**
> So what messed your partition up was to format it to fat?

Windows partitions are always NTFS, so maybe reformatting /dev/sda2 back to that file system will hopefully restore everything.
GParted won't allow me to format to NTFS, it will allow me to select ext2, ext3, fat16, fat32, linux-swap, and reiserfs

---

### Post by DaBomb on 2008-08-23
> **LateNiteTV said:**
> what do u mean when you say "format back to fat32"?
I guess that's probably a big part of my problem huh?
However now it will not let me format to NTFS as I specified in my reply to Diabolis.

---

### Post by Diabolis on 2008-08-23
How about deleting the partition and then creating it again with the NTFS format?

---

### Post by DaBomb on 2008-08-23
I will try it if you don't think I will lose my files.

---

### Post by Diabolis on 2008-08-23
Certainly it won't do more harm from what already has been done.

---

