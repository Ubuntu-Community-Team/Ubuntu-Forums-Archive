---
title: "Remove only 1 of 3 Ubuntu installs"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by studavis on 2009-07-02
Due to messing about with intel video drivers, I completely broke xserver-org (9.04) and could not re-install from home using wireless. In desperation, I installed another 9.04, so I now have 3 Ubuntu versions (I kept my old 8.04) plus XP so of course am running out of space. I've now recovered the broken install (which I want to keep).

I've found instructions to remove Ubuntu from a dual boot, but that removes it completely and gives back all the space to XP.

Is there a way I can remove the 2 versions I'm not using, leaving XP and 9.04 intact?

Word of warning to Intel users, tread carefully when trying to solve the graphics problems!

Thanks for any help.

---

### Post by snakt on 2009-07-02
The information that grub (you boot loader) is likely on the old install but you can look for a "Boot" directory "/boot" in either or both of your linux drives.

I'm not an expert but i would in this situation find out how to install Grub via ubuntu 9.04. Remove the old linux partition. Then install Grub. all while booted into 9.04.

---

### Post by snakt on 2009-07-02
You mite find this usefull (i havent looked too far) [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by studavis on 2009-07-02
Thanks, I'll go thru that lot but first glance suggests it's all about restoring GRUB. I did have that problem few days back and had it neatly solved thru this forum.

---

### Post by studavis on 2009-07-02
Ah, strange, I got your second message before I got the first... Make sense now!
thanks

---

