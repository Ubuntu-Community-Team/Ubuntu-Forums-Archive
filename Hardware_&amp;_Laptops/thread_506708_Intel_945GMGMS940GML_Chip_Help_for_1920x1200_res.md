---
title: "Intel 945GM/GMS/940GML Chip Help for 1920x1200 res"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by cjsstables on 2007-07-22
Hi all,  I'm trying to configure Ubuntu to allow me to display 1920x1200 res.  I have a 945GM/GMS/940GML (intel) Express Integrated Graphics processor on my motherboard.  I am also using a 24" Dell 2405FPW LCD Monitor.  I am able to achieve only 1600x1200 res.  I have tried dpkg-reconfigure xserver-xorg but when I select the 1920 x 1200 I can no longer get the monitor to display.  There is an issue with the monior...  Its specs say that 1920x1200 has to run at 60hz sync rate.  I'm fustrated with this as I would really like to have the extended graphics...

Any help would be appreciated.

---

### Post by tgm4883 on 2007-07-22
The max resolution for the intel 945GM is 1600x1200

---

### Post by cjsstables on 2007-07-22
That's funny because windows 2000 on the same pc can run 1920x1200 just fine.  I also have a mac mini equiped with the same graphics processor and it displays 1920x1200 as well.  Could it be that the i810 driver in Ubuntu is maxed at 1600x1200?

Anyone else help in this matter?

---

### Post by tgm4883 on 2007-07-22
Hmm, strange.  I just got that off the datasheet.  You can try installing 915resolution, which is how I had to get widescreen on my 945gm

---

