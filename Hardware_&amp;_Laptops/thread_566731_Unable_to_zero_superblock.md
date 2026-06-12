---
title: "Unable to zero superblock"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by tuckie on 2007-10-03
As a continuation of my fun [here]("http://ubuntuforums.org/showthread.php?t=560513"), I'm trying to try and zero the superblock on one of my hard drives to add it to the new array, when I try to do so (sudo mdadm --zero-superblock /dev/sdb), Reports that it it "Couldn't open /dev/sdb for write - not zeroing"  Running fuser /dev/sdb reports nothing accessing it, and I get the same error in single user mode.  I'm still able to format the disk, mount the disk, and write to it, but I cant remove the superblock so that I can add it to the array.  Does anyone have any ideas?

---

