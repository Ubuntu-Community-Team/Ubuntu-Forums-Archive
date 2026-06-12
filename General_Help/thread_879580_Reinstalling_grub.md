---
title: "Reinstalling grub"
date: 2008-08-04
forum: General Help
---

### Post by shp on 2008-08-04
I dual boot xp and ubuntu. However i get two bootloaders when i start up. The first is grub which lets me choose between Ubuntu and XP. If i choose XP it goes to a vista bootloader that was installed when my machine had vista.

Anyway i think i know how to remove the vista one (running fixboot). Although i think this while also destroy grub. So how do i restore grub?

---

### Post by caljohnsmith on 2008-08-04
If you overwrote Grub in the Master Boot Record (MBR) when you tried fixing Windows, you can reinstall Grub to the MBR by first booting up a Live CD, going to a terminal, and doing the following:
```
sudo grub
grub> find /boot/grub/stage1
[should return a partition (hd0,X)]
grub> root (hd0,X)
grub> setup (hd0)
grub> quit
```
That overwrites the MBR with Grub, and then grub will look in partition (hd0,X) for all its configuration files.

---

