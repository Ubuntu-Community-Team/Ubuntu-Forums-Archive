---
title: "Does the Install Recognise BSD Disklabels?"
date: 2004-10-18
forum: Installation &amp; Upgrades
---

### Post by EternalNewbie on 2004-10-18
Hi,
    Thinking of trying Ubuntu out but am wary of losing partitions after
trying the new Debian installer ; it would not recognise a BSD slice on
the disk and I could not call up cfdisk from the shell.
     Ended up installing Woody with the boot-floppies and upgrading
the system and kernel to unstable. This would't work with Ubuntu by the
look of things, hence my question.
                                                       All the best,
                                                             John Duncan

---

### Post by jhigz on 2004-10-20
Not in my experience it didn't. I have two HDD's on my machine. The primary drive has multiple Linux distros, Win2k and most recently Ubuntu. The secondary HDD consist of two primary partitions, one containing FreeBSD and the other OpenBSD. In both cases, the Ubuntu installer correctly identified the two primary partitions on the secondary HDD, but did not list any of the slices within the primary partitions.

Interestingly, the installer identifies the OpenBSD file system on it's respective partition as "sun-ufs", but sees no file system at all on the FreeBSD partition.

Also of note, I had to manually edit /boot/grub/menu.lst in order to boot the BSD's on the secondary HDD.

As both BSD's are installed on the secondary drive, I had no hesitations or problems installing Ubuntu on my primary drive as far as potentially damaging an "unseen" slice.

---

