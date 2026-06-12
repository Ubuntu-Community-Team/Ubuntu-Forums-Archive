---
title: "No sounds via headphones on Asus A6VM-A"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by plesset on 2007-11-27
Hallo,

I have been struggling for couple of now to get sound through the headphone jack on my Asus A6VM-A laptop. The sound works fine through the built in speaker, nothing comes out of the headphone. The machine is dual-booted, with XP at the front and there the sound works perfectly. I have been going through [http://ubuntuforums.org/showthread.php?p=3826881](http://ubuntuforums.org/showthread.php?p=3826881) , resulting in countless reboots and reinstall. I even tried installing 7.04 and then upgrading but nothing work. I'm running a fully up2date 7.10. 

I am an avid OSX-phile , but got exposed to Ubuntu at work. I have been 100% satisfied with my desktop there with everything working straight from the box, so I decided to try it on a laptop as well.  

Card: HDA Intel
Chip : Realtek ALC880
Asus A6VM-A

lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
00:1b.0 0403: 8086:2668 (rev 04)

Any help will be much appreciated!

---

### Post by plesset on 2007-11-28
Problem solved, thanks to [http://ubuntuforums.org/showthread.php?t=597575&highlight=ALC880](http://ubuntuforums.org/showthread.php?t=597575&highlight=ALC880)

---

