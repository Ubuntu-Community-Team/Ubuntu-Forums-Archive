---
title: "boot problems inodes and corrupted orphans"
date: 2008-09-29
forum: General Help
---

### Post by engineer85 on 2008-09-29
Hi all,

I'm experiencing some strange problems with my ubuntu system.  Every time I boot, I log in to ubuntu, and all is good, for now.  Then at some random time, I notice that firefox stops working.  After a force quit on that, I discover that nothing else works either, I can move the mouse, and click menus in Gnome, but there are no icons next to the menu items, and I get an error message something about a child relationship.

When I reboot, my system checks my boot partition (/dev/sda1) automatically.  Every time, fsck fails with this error:
Inodes that were part of a corrupted orpan linked list found.
fsck dies with exit status 4.  run fsck manually.  

So I run fsck at the terminal, and fsck fixes the partition after me pressing "y" several thousand times (literally) due to more orphan type errors.  I have no idea what this means or what I did to cause this.  Any suggestions on how to fix it?

Thanks so much,

Steve

---

