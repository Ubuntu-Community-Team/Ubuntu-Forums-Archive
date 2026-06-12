---
title: "Stealth access to ubuntu dual boot?"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by sailthesea on 2009-03-27
I've been finding my way around Intrepid on my old laptop for a few weeks and am seeing the many advantages So I thought I would install a dual boot on the family machine (XP media, good spec) but for the time being I would like to keep XP as the default OS, as in just loads without the boot option, and have some sort of boot up keystroke to load Ubuntu when I get a chance to use it. I'm not planning on depriving anyone of using Ubuntu, I'd just like to be confident of what I'm doing when I announce that we will be having a new OS on the computer!
 I'm sure this is going to involve some (to me) horrific grub/boot/bios trickery which I'll never figure out
 So maybe someone did this already?:confused:

---

### Post by sailthesea on 2009-03-27
I'm gonna get drunk and try to do it anyway!:P

---

### Post by daveg2 on 2009-03-27
Uncomment hiddenmenu in /boot/grub/menu.lst, set timeout to the number of seconds you want to allow before it boots into default.  Put your Windows stuff before 
### BEGIN AUTOMAGIC KERNELS LIST
so Windows is the default.

When you want to get to the menu, hit escape during the timeout number of seconds.

---

