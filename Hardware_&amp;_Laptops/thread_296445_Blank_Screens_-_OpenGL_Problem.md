---
title: "Blank Screens - OpenGL Problem?"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by jessebs on 2006-11-09
I have everything in Ubuntu working on my Dell 600m laptop except programs that use opengl. 

When one of these programs is launched, I get a blank screen using "ati" drivers, or very slow response using "fglrx" drivers.  Additionally, the ati drivers cause my system to lock up regularly.

The laptop has an ATI Radeon Mobility 9000, and the games I am testing work fine under XP.

After searching the forum, I could not find any solutions to the problem.

EDIT:

I added the following to the end of xorg.conf:

Section "Extensions"
Option "Composite" "0"
EndSection

---

