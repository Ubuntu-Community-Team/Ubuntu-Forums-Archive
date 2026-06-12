---
title: "Re-install Grub? Win7 Wiped it."
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by zeealpal on 2009-07-10
I had dual boot of XP and Ubuntu, on 2 diff HDD's, then i installed win7 over xp, but forgot it would destroy grub. How can i install grub again from the live cd? Cos ubuntu is still there just cant boot. BTW grub was on the ubuntu partition.

Thanks

---

### Post by geenux on 2009-07-10
From the liveCD:
```
grub
root (hd0,0)  # Position of the ubuntu partition
setup (hd0)  # Write in the mbr of the first disk
```
I'm assuming you've ubuntu on /dev/sda1 (first partition of the first disk).

---

### Post by drs305 on 2009-07-10
Here's the wiki:
[RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by frogotronic on 2009-07-10
Or, you can download [SUPERGRUB]("http://www.supergrubdisk.org/") and make a CD and use that.  I keep a copy of SUPERGRUB on hand for the many times I've baked my GRUB.

- CH   :guitar:

---

### Post by csabo2 on 2009-07-10
> **cement_head said:**
> Or, you can download [SUPERGRUB]("http://www.supergrubdisk.org/") and make a CD and use that.  I keep a copy of SUPERGRUB on hand for the many times I've baked my GRUB.

- CH   :guitar:

grats! that'll come in handy :D

---

### Post by zeealpal on 2009-07-11
yeah ty 4 the help. its good.

---

