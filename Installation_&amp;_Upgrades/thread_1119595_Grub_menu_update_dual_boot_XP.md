---
title: "Grub menu update dual boot XP"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2009-04-08
I just upgraded to ubuntu 9.04 and when prompted I kept the old grub as I didn't want to affect the dual-boot. However it appears this has kept the old kernel. How can I change this?

---

### Post by upchucky on 2009-04-08
get supergrub disk, then use it to make a new grub that includes the dual boot and new kernel, without using supergrub there are commands to repair the grub, but it is nice to have supergrub available and know how to use it when doing future upgrades.

Get Supergrub to set up/repair Grub here:

[http://www.cyberciti.biz/tips/super-...inux-boot.html](http://www.cyberciti.biz/tips/super-...inux-boot.html)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

---

### Post by eekfonky on 2009-04-08
Thanks that worked.

Cheers

---

