---
title: "Bootloader Trouble"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Taggobob on 2008-12-03
I installed Ubuntu on a machine with Vista on it already. I didn't want GRUB to default into Ubuntu, but rather Vista. I popped in my Vista Install Disk and repaired the master boot record, but now it just boots to vista regardless. The windows boot loader doesn't seem to recognize Ubuntu. Should I reinstall GRUB (if so, what do I do to make Vista the default), or is there a way to just use the windows boot loader somehow.

\\Thanks

---

### Post by Partyboi2 on 2008-12-03
Boot a ubuntu live cd and follow [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub. Then reboot into ubuntu and follow [[COLOR=Blue]this[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") to set windows as the default. If you get stuck post your /boot/grub/menu.lst by opening a terminal (Applications>Accessoires>Terminal)
```
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-12-03
OK, first to reinstall Grub, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Reboot, and you should be able to boot into Ubuntu. If that works, then please post the output of:
```
sudo fdisk -lu
```
And also post your menu.lst as Partyboi2 asked for. We can help you set your Grub menu so that Vista boots by default.

---

### Post by Taggobob on 2008-12-04
Sweet that worked! Thanks a bunch.

---

