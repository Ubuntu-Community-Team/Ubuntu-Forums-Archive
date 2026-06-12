---
title: "USB flash drive partitions without automount?"
date: 2008-11-16
forum: General Help
---

### Post by Trebaruna on 2008-11-16
I carry my flash drive with me all the time, so I decided I could stick /boot on a partition on the drive, to properly be able to encrypt my laptop's hard drive.
Anyway, I'd like that partition to not automount when I insert my flash drive into a random machine. Is there a flag I can raise somewhere on the partition or the filesystem that will tell Linux to leave it alone?
I've tried the "hidden" flag with GParted, but that doesn't make a difference.
(sidenote: in 8.10 gparted fails to get a hal-lock, meaning that partitions will be mounted all the time by GNOME when I'm working on them. Is this a known bug?)

---

