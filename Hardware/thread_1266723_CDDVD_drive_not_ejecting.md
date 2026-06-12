---
title: "CD/DVD drive not ejecting"
date: 2009-09-14
forum: Hardware
---

### Post by aatyler on 2009-09-14
I have ubuntu 9.04 installed. when I put in a CD or DVD after a fresh boot it mounts automatically like normal, but when I go to eject it either by right clicking on the icon and selecting umount or eject, pressing the physical eject button on the drive itself, or using the eject command from the terminal, the icon disapears and the drive does not eject. The only way that I can actually get the drive to eject is to use a paper clip, but, then it won't recognize any other CD/DVDs until I powerdown and reboot (a reset doesn't work). I have the ASUS M50VM-B1 laptop, i'm not sure exactly which drive is used on this model. On a final note, I didn't have this problem when I first installed 9.04 about a month ago, its a recent problem.

---

### Post by aatyler on 2009-09-15
UPDATE:

After doing some research on Debian 5.0, I came accross a posting that Debian had the same problem, the solution was to switch the SETA setting in the BIOS from Enhanced to Compatible. I did that and it solved the problem for me.

---

