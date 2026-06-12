---
title: "USB Start Up Difficulty."
date: 2008-08-13
forum: General Help
---

### Post by Symbit on 2008-08-13
Hello.

I have recently installed FreeBSD to my Jump Drive and was wondering how I would go about adding it to GRUB. I have noticed that GRUB recognizes my HDD as "hd0", and was wonder if GRUB can detect my jump drive, and what it would be detected as. 

Thanks! :)

P.S. I am aware that I can boot from the USB drive from my BIOS menu, but would like to add it to grub also. :lolflag:

---

### Post by phidia on 2008-08-13
Perhaps the easy way to do this is to just reinstall grub with the usb drive plugged in and mounted-recognized. Grub should find the root fs on your external drive and add it to menu.lst. 
The ubuntu wiki has a great [grub howto]("https://help.ubuntu.com/community/GrubHowto").

---

