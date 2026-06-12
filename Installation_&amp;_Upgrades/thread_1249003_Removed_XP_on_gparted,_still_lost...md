---
title: "Removed XP on gparted, still lost.."
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by KMSMD on 2009-08-24
Hey guys,
I ran the live disk, gparted and deleted windows xp.  Now it says in gparted that the part is unallocated and also in my boot list, it still lists XP.  Anything I may have done wrong here?

---

### Post by Arand on 2009-08-24
No, gparted will not touch the grub list, although at this point, the grub entry for windows XP will just fail since the partition is gone.

You should be able to update the grub menu (and thus remove the XP entry) by using the command```
sudo update-grub
```- Arand

---

### Post by KMSMD on 2009-08-24
Cool, is there anything I can do with the "unallocated" part now?

---

### Post by tuxxy on 2009-08-24
> **KMSMD said:**
> Cool, is there anything I can do with the "unallocated" part now?

Indeed you could now expand the size of your Ubuntu partition with this new free space, or save it for other distros you may like to test in future.

---

### Post by KMSMD on 2009-08-24
I have gparted up now, and I can't move anything like a "click n drag" to put the unallocated for Ubuntu.

---

### Post by tuxxy on 2009-08-24
> **KMSMD said:**
> I have gparted up now, and I can't move anything like a "click n drag" to put the unallocated for Ubuntu.

Heres a good explanation of how to resize a partition - [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by KMSMD on 2009-08-24
Only thing it would let me do is copy and paste one of the "linux-swap" ones, so lets see where that goes lol.  Thanks for the help.

---

