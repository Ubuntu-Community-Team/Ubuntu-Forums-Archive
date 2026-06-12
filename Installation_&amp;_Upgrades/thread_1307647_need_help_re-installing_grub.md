---
title: "need help re-installing grub"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Cew27 on 2009-10-31
hey guys, got 2 hdd's in, installed 9.10 on  the second  one  (as  my first drive is failing) with the  intention to move all files from  hdd1 to  9.10 then format, so basically grub is on hdd1 and i  want it on  hdd2 with 9.10 
any help would be  greatly appretiated 
thanks

---

### Post by Herman on 2009-10-31
Try the same procedure as described in this thread, [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900"), but instead of installing GRUB to /dev/sda, install it to /dev/sdb, which should be the MBR of your second hard drive.

---

