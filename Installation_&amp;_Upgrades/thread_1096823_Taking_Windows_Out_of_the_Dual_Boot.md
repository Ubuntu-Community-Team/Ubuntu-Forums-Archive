---
title: "Taking Windows Out of the Dual Boot"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by ZachMitchell on 2009-03-15
Greetings,

Well, I'm finally ready to make the big switch to Ubuntu only. I originally installed it as a dual boot with Windows XP installed first, just so I could play around with it.

I've come to love Ubuntu and would like to get rid of Windows XP now. I'm wondering how I would go about removing Windows XP from my hard drive, combining the two partitions into one and having my computer boot right into Ubuntu.

It's possible that this is something really simple, but again I'm new two Ubuntu. Your support is appreciated. :)

---

### Post by upchucky on 2009-03-15
gparted to remove windows partition and grow linux partition, I have to ask, did you create a separate home partition for your linux install, this is a great time to do that, if not, it can still be done. with out losing anything or having to re-install. check these forums for a how to.

remember to only do one partition task at a time, back up your important stuff, or image the linux drive with partimage.

will need to edit the grub boot file to get rid of the chainloader for windows.

---

### Post by ZachMitchell on 2009-03-15
Ok, thank you for your help. ;)

---

