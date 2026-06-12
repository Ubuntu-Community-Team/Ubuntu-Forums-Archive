---
title: "problem : screenresolution on ati mobility rage"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by gruadp on 2007-05-01
I just set up ubuntu feisty 7.04 on a dell inspiron 4000 with a ati mobility rage-card.

Now I've the problem that the maximum screenresolution is 800x600.  There is only this and 640x400 available under system->preferences->screen resolution.

The odd thing is that in xorg.conf 1024x768 is well defined, so I dont have any clue whats going on here. I reinstalled gdm, but it didnt help.

800x600 is a resolution simply unusable under ubuntu cause most dialog-windows are bigger and you dont see the  OK/CANCEL/APPLY-buttons :confused: 

I put the output of  

xorg.conf
lspci
lspci -n
hwinfo --gfxcard

to the following webpage : [http://http://www.goldfisch.at/archive/20070501_ubuntu_xorg_screenresolution]("http://www.goldfisch.at/archive/20070501_ubuntu_xorg_screenresolution")

thnx for your help

peter

---

### Post by gruadp on 2007-05-02
the solution for my problem can be found at:

[http://ubuntuforums.org/showthread.php?t=167670#5]("http://ubuntuforums.org/showthread.php?t=167670#5")

The first code-snip  is the relevant part. the second didnt harm either, so I implemented it, cause I always had troubles switching to console with alt-Fn.

thnx to user sensei_V to put me to the above link and therefore to the solution.

---

