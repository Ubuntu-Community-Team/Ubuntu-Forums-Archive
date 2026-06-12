---
title: "Dual boot XP and ubuntu 9.04 problems"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by chufflar on 2009-10-21
i am a bit of a newbie to ubuntu!
so far i have only really had problems i have overcome most through forum searching but now im really stuck.

i attempted to dual boot windows xp and unbuntu 9.04 putting ubuntu on to an extrenal usb hard disk.

intially i had GRUB error 21 every time i booted and was forced to use my linux live disk to fix the problem.

i ended up installing supergrub which worked and i can now boot into ubuntu without a disk but i still cannot boot into windows.

i get to the grub menu and when i select windows it says GRUB loading stage 2....
and then the boot menu reappears.

any help will be much appreciated!

---

### Post by stlsaint on 2009-10-21
post here the output of this cmd in terminal:

```
cat /boot/grub/menu.lst
```

---

### Post by chufflar on 2009-11-09
The output to that command gave me the following.

cat: /boot/grub/menu.lst: No such file or directory

---

