---
title: "Presario M2000 video card lock up"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by gsalinas on 2005-06-22
A week ago I got me a new presario M2000 laptop. As a longtime ubuntu fan I installed hoary 5.04 (before I had a presario 2500 along with hoary, worked flawlessly). 

Everything went OK, but after the installation was done, it tried to switch to graphic mode, but the screen just turned blank. I guess my X server config had a conflict with the video card (intel 915GM/910GML), so tried to edit my Xorg.conf without luck. 

Temporarily, I had to change the driver section in Xorg.conf from 'i810' to 'vesa' and could get into graphic mode. However the resolution is very poor.

Any suggestions how to get my video working properly??? :-?

---

