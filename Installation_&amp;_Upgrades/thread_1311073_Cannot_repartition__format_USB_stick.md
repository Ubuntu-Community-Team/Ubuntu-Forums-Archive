---
title: "Cannot repartition / format USB stick"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by craftbrewer on 2009-11-02
It seems that when I unmount my USB stick to repartition/format it, it is no longer recognized:

The drive was recognized as /dev/sde1 and mounted accordingly.  I unmount it and tried the following:

$ fdisk /dev/sde

Unable to open /dev/sde

$ mkfs.vfat -F 32 /dev/sde1
mkfs.vfat 3.0.3 (18 May 2009)
/dev/sde1: No such file or directory

What gives?

Solved, kinda. I was using the File Browser to unmount, as this always worked in 9.04.  I just tried umount on the commandline and everything works as expected.

---

### Post by skotos on 2009-11-02
I have noticed [a few problems]("http://http://ubuntuforums.org/showthread.php?t=1305924") with USB support after upgrading as well as after installing Karmic from scratch (FYI you may look at [page1, comment #19]("http://ubuntuforums.org/showthread.php?t=1305924")).

I would thus suggest you to check that after a reboot.
I mean: unmount, reboot and check again; if in this way it works fine, you may have found a way to survive at least up to a definitive solution you may find in the next days/posts.

HTH

---

