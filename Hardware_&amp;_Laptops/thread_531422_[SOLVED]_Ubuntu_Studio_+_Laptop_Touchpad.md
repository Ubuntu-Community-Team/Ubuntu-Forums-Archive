---
title: "[SOLVED] Ubuntu Studio + Laptop Touchpad"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by captainstarbucs on 2007-08-21
Hi, i was wondering how i can install the GSynaptics on my Studio Distro. My problem is that when i try to edit xorg.conf, its completely empty, and when i had the regular ubuntu distro, there was alot of stuff to edit, all you had to do was add an "option" and configure it on, then install the package...but i dont seem to know what to do when xorg.conf is empty.


[EDIT]

I realized that i have the xorg.conf file, but its read only, and if i try to use sudo gedit /ect/X11/xorg.conf, it opens up as nothing, and if i try to copy and paste the code from the read only file to there, and save it...It will say the file is not found. I'm not exactly sure what to do, because i cant edit it and my laptop's touchpad is very sensitive and its hard to control. Anyone?

---

### Post by rainwalker on 2007-08-21
It's in "/etc/X11/", not "/ect/X11"
You switched the "t" and the "c"

---

### Post by loserboy on 2007-08-21
you're just spelling the path wrong


"/ect/X11/xorg.conf"

should be

/etc/X11/xorg.conf


Edit:  oh wow guess i should refresh the page before i post

---

### Post by captainstarbucs on 2007-08-21
hahaha! im such a noob. Thanks guys..ill try it now!:lolflag:

---

### Post by rainwalker on 2007-08-21
No problem :)

Don't forget to mark the thread "Solved"

---

