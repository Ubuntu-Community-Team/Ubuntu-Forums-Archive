---
title: "No windows boot"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by alz5280 on 2009-04-04
Help after loading Ubuntu disk and trying it out and removing it now when trying to boot windows I get disk read error. After trying to boot from windows xp install disk computer starts inspecting setup then goes blank. Wont even allow a repair boot. what will fix my windows boot up? DESPERATE

---

### Post by tommcd on 2009-04-05
Sorry you are having these problems....

Just booting from and running the Ubuntu live CD should not make *any* changes to your hard drive. Did you click the **install** icon on the desktop while you were running the live CD at any point?
Try this:
Boot the Ubuntu live CD. Open a terminal (applications > accessories > terminal) and run:
```
sudo fdisk -l
```
This will list your partitions and will at least verify that Windows is still on your hard drive.

And welcome to the Ubuntu forums!

---

