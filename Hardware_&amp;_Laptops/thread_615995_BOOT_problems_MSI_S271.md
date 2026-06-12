---
title: "BOOT problems MSI S271"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by sintroge on 2007-11-17
Hello,
My MSI S271 AMD 3400+  laptop doesn't seem to like any linux boot loader. I've tried to install Ubuntu 7.10 from the live-cd, but it turns black after restarting, immediately when trying to boot. The same thing happens when I install it with Wubi: after I select Ubuntu in the Vista BootLoader, the screen turns black immediately and there seems to be no activity at all (I tried things like ctrl+alt+F1, and esc right after I selected the linux OS, but that doesn't work). By the way, same things happen with PCLinuxOS, both in LILO as in graphical and non-graphical GRUB. Linux boot loaders don't seem to work on this particular machine.

Any suggestions?

Thanks

---

### Post by tater5749 on 2007-11-18
I have the same problem on my wife's MS-16331 with Gutsy.  Everything worked fine from the live CD, but after install and reboot, I only get a black screen.  Probably some incorrect resolution or refresh rate detection.  Can't get to a terminal or anything to rectify the situation.  It does the same thing with any OS disk in the drive so no chance of rolling back or installing anything else.  Any help would be greatly appreciated.

---

### Post by sintroge on 2007-11-19
I've heard things about adding acpi=off in the boot for MSI Megabook laptops, but that doesn't work for me so far, just a black screen without any sign of activity...

grub's menu.lst now

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro acpi=off
initrd /wubi/boot/initrd
boot

---

### Post by sintroge on 2007-11-19
Fixed it. Use NeoGrub with hpet=disable for the 32bit kernel (> nohpet for 64bit). everything seems to work fine, except for the card-reader and hibernation.

---

### Post by tater5749 on 2007-11-20
I can't get even get to GRUB, just the black screen.  Will NeoGrub help me out if I have no Windows partition ?

---

### Post by sintroge on 2007-11-27
I tried single boot with ubuntu and the standard grub too, and, as you said, that provides me with a nice black screen right after the boot initiates. NeoGrub works fine for me (with hpet=disable).

Good luck!

---

