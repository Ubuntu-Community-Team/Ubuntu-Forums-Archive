---
title: "GParted crashes in 7.10/8.04alpha"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by phinn on 2008-02-09
There are several crashes I get with 7.10 and they have not been addressed in the 8.04 alphas.

1) Xubuntu crashes completely during installation if I have an MSDOS drive. I have to unplug it to get it to install
2) Resizing some partitions with Ubuntu cause a crash (no they are not NTFS)
3) Resizing a raid volume on my work computer sometimes crashes it

There are 10+ bug reports on bugs.launchpad.net  but it might even be simpler than that.

The packages for GNU Parted are like 1 1/2 years old!  Updating them and the GParted packages could fix some of these bugs.  I have tried the update myself on only one computer (compiling from source) and it didn't do much.  But I'm sure it could fix some of the issues or at least be overall more stable for an "LTS" release.

---

