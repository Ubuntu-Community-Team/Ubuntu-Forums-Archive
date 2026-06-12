---
title: "reinstalling windows without losing Ubuntu 9.04"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by robfindlay on 2009-07-26
I have a dual boot system, XP went on first followed by Ubuntu, well now it seems that my XP install is hosed (no surprse there) so I need some help--a walk though perhaps on how to reinstall XP and then reinstall GRUB so I can dual boot again. 

Is there a how-to that covers this?

---

### Post by merlinus on 2009-07-26
You can try to repair xp by booting from its install cd and selecting restore (or perhaps it is repair).  Failing a fix, you should be able to reinstall it into the original partition.  Just do not select use entire disk.

Then you can reinstall grub by booting from the live cd, opening a terminal, and entering:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```and restart.  You may have to add an entry for xp in /boot/grub/menu.lst.

---

