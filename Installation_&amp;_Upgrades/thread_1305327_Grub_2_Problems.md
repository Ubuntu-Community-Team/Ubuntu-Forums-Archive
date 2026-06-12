---
title: "Grub 2 Problems"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by dksite on 2009-10-29
Hi guys-so i am on 9.10 karmic now, and have been for the past few weeks using the betas. Now that the update was official today, I decided to update my grub to grub2 using one of the many tutorials.  Somehow, the part about chain-loading from the old grub didn't work because grub was removed when I install grub2, so I just went along and finished the grub2 installation.  When I rebooted, it said "GRUB Loading", went to the white Ubuntu logo for a few seconds, then to a screen with a blinking cursor then no cursor at all.  When I hold down shift and boot the recovery kernel, everything works fine.  I have gone through the various steps, like grub-update and grub-install, etc. with no luck.  Anyone have any idea how to solve this?

---

### Post by autocrosser on 2009-10-29
Take a look in the closed Karmic development forum & search for Grub2--you are going to do some edit work & there are several good info threads there--Plus there is a very good Grub2 tutorial in Tutorials & Tips forum.....

---

### Post by Blackylol on 2009-10-29
i had some problems with grub2... i'm a newbie in linux and I like to play with it doing things i dont know....

i wasnt able to load my OS with grub2 after i did upgrade of both (i updated my OS beta to release and grub to grub2 at same time), so I used the recovery mode in one of older kernels, selected netroot (or something like that)  uninstalled grub2 installing grub with sudo apt-get install grub... then restarted and same problem, I tried once more, and did a sudo apt-get install grub2 then grub-update or grub2-update cant remember.... restarted pc and All worked fine again. (all what I did was install and reinstall grub many times)

If you can understand what I wrote :P good luck.

---

### Post by dksite on 2009-10-29
I appreciate the help-and I have continued to search and look for answers, and while I haven't tried the uninstall-reinstall stuff yet, I can't find any other way to fix this problem. It seems odd that grub2 will boot the recovery kernel just fine, but the normal kernel hangs. Do you have any more specific suggestions that I try?

---

### Post by Blackylol on 2009-10-29
idk, what about run the dpkg, and a sudo apt-update and upgrade, i also used that in recovery terminal before the unistall reinstall thing... i bet your problem is in the menu.lst or grub.cfg, my problem was there, so after many times reinstalling it, it wrote the fille correctly hehe

---

