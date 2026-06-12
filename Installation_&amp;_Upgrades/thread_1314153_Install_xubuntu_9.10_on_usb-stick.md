---
title: "Install xubuntu 9.10 on usb-stick"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Hans Willemsen on 2009-11-04
Hello guys,
 
I've read a lot of difficult ways to install xubuntu on a usbstick, but it isn't really that hard.
 
First install dream linux on the usb-stick from the dream-live-cd to make the usb-stick bootable (or find a cleaner way)
 
Second: use the standard Xubuntu installation process from CD and choose the usb-medium to install to.
Be carefull that the drop-box in the partitioning-screen refers to the usb-stick or you'll end up, just like me, with reinstalling on hd.
The install-process requires that, just before the resume (I forgot which screen exactly), you MUST choose "advanced" and make very sure that GRUB is installed in the usb-stick also. The default installation is on your harddisk even for an install on usb. This makes your hard-disk unusable (grub on hd points to the usb-instalation). 
 
Xubuntu from a usb-stick works fine and on the office I can use Openoffice (on the xubuntu-usb-stick) to move some isolated open-office documents to Word.
 
regards, Hans

---

### Post by Mighty_Joe on 2009-11-04
Welcome to the club. We've got a post [over here]("http://ubuntuforums.org/showthread.php?t=1193680") that details pretty much every way to get Linux on a flash drive, including a some helpful hints on how to optimize a full install.

---

