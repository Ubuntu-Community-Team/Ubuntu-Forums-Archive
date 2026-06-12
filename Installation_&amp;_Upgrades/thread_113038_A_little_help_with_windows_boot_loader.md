---
title: "A little help with windows boot loader"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by rdking on 2006-01-05
hey all,

I can't believe I did it!  I just installed windows for my girlfriend on a free partition I was using for an old BSD release.  Problem was that unlike previous installs, this partition was on the first disk, and hence I no longer get the grub boot loader, and the choice of my operating system.  My guess is a simple run of usr/bin/grub, and put it in the MBR again will suffice....is that correct? Do I need to mark this windows partition as bootable as well?

cheers in advance

---

### Post by Sutekh on 2006-01-25
Try having a look at these links to re-install GRUB

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") (re-installs GRUB again)

[HOWO: Restore GRUB if you MBR is messed up]("http://ubuntuforums.org/showthread.php?t=24113")

---

