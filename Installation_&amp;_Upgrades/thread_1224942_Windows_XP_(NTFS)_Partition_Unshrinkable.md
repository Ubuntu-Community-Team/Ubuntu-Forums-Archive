---
title: "Windows XP (NTFS) Partition Unshrinkable"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Slaskie on 2009-07-28
I am trying to set up a dual boot between Windows XP and Kubuntu 9.04, but when I try to shrink the windows partition using gparted, the "down" arrow for the grow/shrink box on the resize/move menu is grayed out. I am sure I have more than enough free space on my NTFS windows partition to shrink it, the option to do so is simply not there. How can I fix this?  Thanks.

---

### Post by lykwydchykyn on 2009-07-28
- has the NTFS partition been defragged?
 - Did Windows shut down cleanly?  Try opening a command prompt in the liveCD and running "ntfsfix /dev/xxx" where "xxx" is the NTFS partition (e.g., sda1, sda2, etc -- you should see a label like this in gparted).
 - If neither of these is the issue, you can try running the command-line version and see what error output you get.  The command is ntfsresize; you can run it with the -n option and it will just simulate the resize.  So try something like this (with parameters adjusted to your needs):
```

ntfsresize --no-action --size 40G --verbose /dev/sda1

```

---

### Post by merlinus on 2009-07-28
Delete temp files, disable paging, reboot and delete pagefile.sys, and defrag several times.  Then you should be able to shrink the xp partition.

Also you might try gparted live, which is a later version than the one on the ubuntu live cd.

---

### Post by Slaskie on 2009-07-29
I did all of the above except delete pagefile.sys, because I couldn't find it on my computer. I also used gparted live but there was still no difference: the shrink option for my xp partition was still grayed out. :(

---

### Post by lykwydchykyn on 2009-07-29
> **Slaskie said:**
> I did all of the above except delete pagefile.sys, because I couldn't find it on my computer. I also used gparted live but there was still no difference: the shrink option for my xp partition was still grayed out. :(

What output did you get from ntfsresize?

---

