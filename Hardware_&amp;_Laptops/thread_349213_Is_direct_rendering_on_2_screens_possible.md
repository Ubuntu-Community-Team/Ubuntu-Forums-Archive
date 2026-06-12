---
title: "Is direct rendering on 2 screens possible?"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by grahams on 2007-01-29
I have added dual screen support using MergedFB (xorg.conf attached). I noticed direct rendering stops working when 2 screens are used, but still works fine when only 1 screen (main laptop screen) is used.

If I run  'glxinfo |grep rendering' with both screens attached i get 
direct rendering: No and 3d test like glxgears run slowly.
with just the laptop screen direct rendering:yes and glxgears runs quickly.

My graphics chip is an ATI controller built into my Compaq n610c laptop

lspci 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

My question is, can I have direct rendering and dual screens or is this a limit of my system. 

I also attached my Xorg.0.log.

---

### Post by grahams on 2007-01-31
I think I've answered my own question. Looks like MergedFB can only accelerate 3D when the combined resolution of both heads is =<  2048x2048.

---

