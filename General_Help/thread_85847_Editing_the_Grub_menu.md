---
title: "Editing the Grub menu?"
date: 2005-11-03
forum: General Help
---

### Post by Terrik on 2005-11-03
Hi all,

I have a dual-boot running on my laptop with Windows and Ubuntu. When the Grub chooser comes up during startup, it shows Ubuntu first, then all the way at the bottom is Windows.

Since I need to use Windows for most of my schoolwork and will be booting into it most of the time, is there a way I can change the menu so that Windows is ontop and then Ubuntu is under it? Thanks!

---

### Post by metoo on 2005-11-03
Sure, the grub menu is located under /boot/grub/menu.lst .
Dive into it with an editor as root and change the order of the block of lines for each menu entry. Can't miss it.

---

