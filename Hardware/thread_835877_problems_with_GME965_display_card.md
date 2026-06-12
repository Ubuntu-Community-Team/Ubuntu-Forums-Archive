---
title: "problems with GME965 display card"
date: 2008-06-20
forum: Hardware
---

### Post by suanhwee on 2008-06-20
Hi, i have a system with intel GME965 as its video display chip.
This is an embedded version. No matter what i try i still cant get the display working properly it only displays with VESA drivers but the image is a bit fuzzy.

I looked around and saw that the IEGD drivers from intel will help to solve this problem. Has any one tried using it or is there any package in the ubuntu repositories that can solve this problem or any loadable modules that are already done that i can load in?

This problem have been bugging me for the past 2 months and i still cant find the solution.

Thanks for your help

---

### Post by Kubunteando on 2008-08-08
I have the same chipset which means that the Graphic card is an Intel X3100.

In my case also tells that uses the VESA driver but it loads the Intel driver. It work perfectly with a resolution 1680x1050.
I have OpenGL working fine out of the box in Hardy.

Maybe your monitor resolution is not detected fine? You can try to update it manually.

Some monitors may not be detected correctly when set as Plug and Play.

---

