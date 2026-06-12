---
title: "Programs and NTFS"
date: 2013-06-01
forum: Hardware
---

### Post by Hg2013 on 2013-06-01
Is it possible to run Linux programs from an NTFS partition of any sort? If Ubuntu can't, are there any Linux distros that can?

It's mainly due to the arrangement of my computer using a small SSD and a large HDD, but the SSD is reserved for operating system and related stuff.

I'm running 13.04.

---

### Post by CatKiller on 2013-06-01
NTFS is insufficient for the task. It is unable to handle features that Linux makes use of. Resize the existing partition and put a proper filesystem in the free space.

EDIT: Also, you don't (generally) store programs on a separate partition. Files are sorted by purpose, not origin, so you won't have a Program Files equivalent if that's what you were thinking of.

---

### Post by Hg2013 on 2013-06-01
I guess it's viable to put them on the SDD for now since I don't plan on doing *too* much on Ubuntu.

In the off chance I do need more space and would like to keep symmetry with how I'm managing my Windows stuff, would it work for the programs if I created a partition of the required format?

---

### Post by CatKiller on 2013-06-01
Not really. I mean, you can, it's a flexible setup, but you need to not think of drive letters and the like. Installing Ubuntu on a partition of your SSD and having a partition on your HDD for /home is the sensible and pain-free approach. There's some stuff you can do with swap if you're really concerned about writes to your SSD, but the statistics say that your HDD will fail at about the same rate as running out of writable cells on an SSD under normal conditions these days.

You might want to read [this]("http://en.m.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") to see why having a drive for programs makes no sense in Linux.

---

### Post by Hg2013 on 2013-06-01
I guess I'll consider increasing the space allocated to Ubuntu or creating the partition for /home stuff.

Thanks for the replies.

---

