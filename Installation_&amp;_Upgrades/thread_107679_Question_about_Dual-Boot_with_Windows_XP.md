---
title: "Question about Dual-Boot with Windows XP"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by pelon42004 on 2005-12-23
Hi

I have succesfully installed Ubuntu 5.10 dual-boot with windows xp. My questions is if  there is a way to modify the order of  the boot-loader. The way it is rite now is: Ubuntu is the first choice to boot and at the end is Windows XP I want to know if it is possible to put Windows xp as the first choice instead of Ubuntu because my other family members use windows .

Thanks in advanced.

---

### Post by Koybe on 2005-12-23
Look in the file /boot/grub/menu.lst, and set default line to the number of the title telling about windows and starting to count from zero.
```
sudo gedit /boot/grub/menu.lst
   default=2
```
(for example)

---

### Post by pelon42004 on 2005-12-23
Thank you so much this really solve my issue.

---

