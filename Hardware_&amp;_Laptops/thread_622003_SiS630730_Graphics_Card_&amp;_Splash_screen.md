---
title: "SiS630/730 Graphics Card &amp; Splash screen"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by johnaaronrose on 2007-11-24
Booting up (to Login screen display) on Durion desktop with SiS630/730 graphics card used to take about 2 minutes on Feisty. Now it takes about 6 minutes. Seems to be mainly due to splash screen display attempt (which doesn't succeed) as changing /boot/grub/menu.lst to nosplash in kernel line much improves to 3+ minutes.

I've tried putting in vga=775 but says that mode is undefined for VESA VGA and modes available are various text modes e.g. 0 for 80x25 but doesn't show splash screen.

I've tried  enabling fbcon, sisfb, vesafb, vga16fb modules for framebuffers (sisfb, vesafb &vga16fb in various combinations (as shown in Launchpad bugs).

Anybody have any ideas for displaying the splash screen?

---

