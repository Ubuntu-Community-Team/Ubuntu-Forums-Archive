---
title: "can't create Linux bootable iso"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by [3w`Sparky] on 2009-09-29
OK I have been customizing CD's for a while however I always use to just extract the squashfs file and drop it into an already existing iso image - this way it was bootable and contained the boot infomation in the iso. 

however i have created a OS that will create a custom O/S

so i boot my admin PC and run my scripts it does all the editing i need and the fails at the following command

genisoimage -b isolinux.bin -no-emul-boot -o newcd.iso /cdimagesrc

i get the following error 

Uh oh, I can't find the boot image "isolinux.bin" (and yeah i checked its in my current folder)

theres lots of posts on the net with this problem none of them seem to have a conclusion tho

help !

PS my isolinux.bin is 14739 bytes in size "ls -l"

---

