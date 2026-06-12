---
title: "Filesystem Question"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by mitsuo on 2007-04-19
I have used ubuntu before, but stuff happened and i had to migrate to windows, now with the coming of 7.04, i'd like to do back, the thing is that my data partition is NTFS, and i want it a linux partition, is there anyway to convert the filesystem without losing the data?
another question is, what filesystem should i use? ext2? ext3? reiserfs? anything else?
oh, and does 7.04 64bit version support intel cpus?

---

### Post by az on 2007-04-19
No, you cannot convert a patition to EXT3 while preserving the data.

Use the default, ext3.

Yes, the 64 bit version supports intel.

---

### Post by Gromit83 on 2007-04-19
You can use a shrinking program to shrink your NTFS partition to create enough space to accompany a dualboot of Ubuntu and Windows. Ubuntu can read and write to NTFS with the right software configured without any problems.

As for 64 bit Ubuntu. It will work for all AMD64 CPUs and Intel CPUs with EM64T

---

### Post by az on 2007-04-19
> **Gromit83 said:**
> You can use a shrinking program to shrink your NTFS partition to create enough space to accompany a dualboot of Ubuntu and Windows.

The Ubuntu installer can do that for you.  It will do that by deafault.

---

