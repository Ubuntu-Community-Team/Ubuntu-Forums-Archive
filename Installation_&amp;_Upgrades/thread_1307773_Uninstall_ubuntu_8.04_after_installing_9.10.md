---
title: "Uninstall ubuntu 8.04 after installing 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by nishanvincent on 2009-10-31
Hi Guys, I really need some help to uninstall ubuntu 8.04.
I wam using ubuntu 8.04 and windows vista with dual boot for long time now. I recently installed ubuntu 9.10 into my laptop using the CD. But now the ubuntu 8.04, 9.10 and windows vista, all 3 operating system are in the laptop. All I need is some advice how to uninstall ubuntu 8.04 from my laptop. I have triple booting currently and have access to all 3 o/s while booting. I want to remove the older ubuntu 8.04 version.
I would really appreciate if someone can help.
Thank You

---

### Post by 73ckn797 on 2009-10-31
Boot from Live CD and use gparted to delete the 8.04 partition. Then resize the other partitions to use the new space. I do not know how 9.10 will work, since it is so new, but I have used the procedure with other versions. I believe that the new Grub2 will take care of the boot list since it no longer uses the "menu.lst".

---

### Post by nishanvincent on 2009-10-31
Thanks dude, will try this and let u know if i need further help.

---

