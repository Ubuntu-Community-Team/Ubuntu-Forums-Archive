---
title: "grub problems"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-07-07
Hi, last week I upgraded my hd from a 20gb to 120gb.  Things moved around abit

windows ->sda1
swap    ->sdb1
Ubuntu  ->sdb2

where as it was, I think 
windows   ->sda1
/home/ftp ->sdb1
ubuntu    ->sdc1
swap      ->sdc2

After reinstalling grub I get error 2
How can I update it, like we used to under lilo

Using the grub super disk to boot at the moment. I can't find a way to
rewright the config.

---

### Post by buckrodgers on 2009-07-15
Edit ```
/boot/grub/menu.lst
``` and put your new set-up there

Cheers

---

