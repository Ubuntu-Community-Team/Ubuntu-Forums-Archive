---
title: "Solution: restore GRUB after Windows (re)installation or other MBR problem"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by Swiss2K on 2006-01-08
Looking into this forum there seem to be quit a few people that struggle with Grub after windows (re)installation or other MBR problem

Here is a simple solution that will fix the problem in most cases:

First you need to gain root access.

1# boot-up computer with Ubuntu Installation CD
2# At "boot:" prompt, add "rescue" to the argument
**boot: rescue**
3# Follow the instructions on screen

4# Now, Assumed that /dev/hda is the location of /boot partition type:
**grub-install /dev/hda**

If all goes well Grub-menu is back. Just reboot and enjoy Ubuntu agian...

---

### Post by aysiu on 2006-01-08
Maybe add it to this thread...

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by three_sixteen on 2006-01-18
Bumping :D

---

