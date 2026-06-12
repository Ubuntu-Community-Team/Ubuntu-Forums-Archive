---
title: "Ubuntu 8.04 No menu.lst!!!!!"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by w1av on 2009-01-15
Hi, I recently got a NEW COMPUTER and it has WinXP and Ubuntu on separate hard drives. I just installed Ubuntu and everything seems cool but I can't find my menu.lst!!!! If I go into /boot/grub there is no menu/lst in there! I want to edit out some kernel choices and change the color of boot loader screen like I did on my other Ubuntu installation on my old computer. PLEASE HELP!!! I am confused because I used the same setup Ubuntu 8.04 disk on new computer as I used on my older computer. I did update the system after installation. Do you think the updates changed where menu.lst lives now????:(

---

### Post by cdtech on 2009-01-15
The file is "/boot/grub/menu.lst":
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by w1av on 2009-01-15
OK I will try that when I get home today. It just seems weird that it is not where it should be. Bob

---

