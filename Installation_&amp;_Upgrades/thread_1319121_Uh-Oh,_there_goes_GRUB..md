---
title: "Uh-Oh, there goes GRUB."
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by SilverSnakeEyes on 2009-11-08
After trying (and failing) to install Arch Linux side by side with ubuntu, it put itself ahead of GRUB. So having my handy dandy puppy linux livecd I tried to fix it. Now what I didn't realize at the time was that I should have been typing root (hd0,5) as my partition was /dev/sda6 but me, being stupid, got arch for putting in (hd0,6). I then proceeded to again go into the grub through puppy linux. This time I reinstalled grub completely, replacing all of ubuntu's /boot/grub files, when I could have just changed one number and not had all of this. stupid me.

Anyways, need to fix GRUB, but I can't use the livecd, as I encounter a still brown screen due to compiz and my crappy video card, and in safe graphics mode the screen stays completely black the whole time...
I tried just waiting until I heard the noise after entering safe graphics mode (the login music) and then doing ctrl-altf2 but that doesn't seem to work either, as my hard drive isn't detected, cant be mounted, and cant be added to /etc/fstab.

Wtf, some help please?

---

