---
title: "Three Monitors With Twinview"
date: 2011-01-05
forum: Hardware
---

### Post by nova47 on 2011-01-05
I was wondering how you set up three monitors using Nvidia's X server drivers. I've got SLI enabled with AFR (used [http://www.techpowerup.com/forums/showthread.php?t=52953](http://www.techpowerup.com/forums/showthread.php?t=52953)) but I don't see a way to activate my third monitor unless I use it as a duplicate display. How do I extend the desktop to the third monitor using Nvidia's driver? Or for that matter how do I use twinview on two and do an xscreen on the other?

---

### Post by nova47 on 2011-01-10
bump*

---

### Post by nova47 on 2011-01-23
bump*

---

### Post by nova47 on 2011-02-02
So does no variant of linux support three monitors in any way? Given the number of people I know with this kind've setup I just find that very surprising.

---

### Post by Gasmart on 2012-03-24
I have exactly the same problem here... tree monitors in Kubuntu 11.10. I can't activate any effect in Xinerama, if i disable it i can't drag windows between screens.

Thanks in advance and greetings from Argentina! 
Gaston.

---

### Post by BicyclerBoy on 2012-03-24
nVidia's linux driver only lets you have 2 monitors in twinview because it would otherwise have to be called triplet or multi-view.
nVidia makes you pay for multi-monitor support.

To get 3 or more you have to have:
- a quadro card
- use mosaic mosaic-sli
- separate X screens
 OR use AMD eyefinity

separate X screens are usable albeit a little awkward.
You launch apps to a specific screen; very good for full screen video etc.

Xorg Xinerama breaks openGL/GLX; it is not really an option any more.

---

### Post by BicyclerBoy on 2012-03-29
Read this on nVidia linux forums..
nVidia 295 driver now supports 4 monitors in "twinview" on consumer cards.

May be it will renamed quadoview or foreview or whaview..

This feature may be in response to AMD eyefinity..

The sceptic or cynic in me thinks that 4-view may only work on the new kepler 600 series..

---

