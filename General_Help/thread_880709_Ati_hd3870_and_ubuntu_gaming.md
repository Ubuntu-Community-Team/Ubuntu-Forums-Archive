---
title: "Ati hd3870 and ubuntu gaming"
date: 2008-08-05
forum: General Help
---

### Post by Papas228 on 2008-08-05
hi everyone! basically i've installed the ati drivers manually after downloading it from ati's website. i know that i've installed them correctly since i have compiz working just fine with all the effects that i like. now when i try to play games such as Guild Wars my screen just pixelizes and i can't make anything out. now i've tried hit alt-f2 and disabling compiz by changing it to metacity. but that still hasn't worked. i just wanna know if this is a driver issue or has anyone really got the hd3xxx series to work properly with games? thanks

---

### Post by gobbles414 on 2008-08-05
First, you should tweak your graphics settings in Wine. You may also wish to change the version of Windows that your Wine is emulating. In Ubuntu, go *Applications => Wine => Configure Wine*. If there is not a Wine menu, open a terminal window and type *winecfg*.

If that doesn't work, do a fresh install of Ubuntu. But instead of installing the video drivers from the ATI website, install them by going *System => Administration => Hardware Drivers* (or Restricted Drivers Manager). I own an ATI HD 3870, and that's how I installed my video drivers.

---

### Post by gobbles414 on 2008-08-05
I forgot to mention that my native Linux 3D accelerated games work beautifully with my ATI HD 3870 in Ubuntu -- using the graphics driver that Ubuntu provides.

The only problem that I've had with my graphics is Ubuntu 8.04 used to crash a lot when I used Firefox to visit websites with Flash content (e.g. YouTube). Choosing "None" in *System => Preferences => Appearance => Visual Effects* fixed this crashing problem.

---

### Post by tuxxy on 2008-08-05
I had all sorts of issues with ATI drivers, I never got my systems working perfect with them in use.

---

### Post by rbmorse on 2008-08-05
WINE support seems to be especially problematic. I don't know if anyone really knows exactly where the problem lies.

---

### Post by Papas228 on 2008-08-05
well thanks for the quick replies but i guess i'm not gonna be doin any games, i tried fooling around with the settings in wine but to no avail. but everything else works just fine thanks again

---

### Post by gobbles414 on 2008-08-06
> **Papas228 said:**
> well thanks for the quick replies but i guess i'm not gonna be doin any games, i tried fooling around with the settings in wine but to no avail. but everything else works just fine thanks again It might be worth your time to experiment with Crossover Office and/or Cedega. Both are very similar to Wine, but with optimizations for gaming.

---

