---
title: "Set 60-line in full-screen terminal (and boot)?"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-05-09
Is there a way to tell Ubuntu to use 60-line mode when a terminal is running full-screen, instead of the default 25-line mode?

I'd like to have the same effect when booting also, if possible. Can this be done?

Many thanks for any help.

---

### Post by emendelson on 2005-05-10
To answer my own question (which should have asked about 50-line, not 60-line):

Edit /boot/grub/menu.lst so that the kernel line includes this string:

vga=0x318

A full list of suitable video modes is here:

[http://www.antlinux.com/staticwiki/VgaModes.html](http://www.antlinux.com/staticwiki/VgaModes.html)

---

