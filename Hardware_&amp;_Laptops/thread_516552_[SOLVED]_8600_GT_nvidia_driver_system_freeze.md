---
title: "[SOLVED] 8600 GT nvidia driver system freeze"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by fox112 on 2007-08-03
Hi there,

I just bought a MSI 8600GT, and tried to install the nvidia driver.
When starting X my monitor shuts down and my system freezes completely! I tried NVIDIA 100.14.11 manually and using envy to install it. I read all feisty/8xxx series threads but nothing works. xorg nv driver works, but only in 1024x768, even though i manually added Modelines. Any idea? I'm running 64bit.

thx

---

### Post by Obor on 2007-08-06
I don't know if this will be any help... I just got myself a new pc with nvidia 8600gt card. [This is how I got it to work (I'm running 32 bit though)]("http://www.robdian.co.uk/content/view/56/27/")

---

### Post by fox112 on 2007-08-08
I allready tried all kinds of guides. The card just doesn't seem to work with the driver. Installing the drivers is not the problem.

---

### Post by z0mbie on 2007-08-09
The 8600 is a pretty new card, they're still developing the drivers at Nvidia. I'd do one more thing, try checking your refresh rates in **/etc/X11/xorg.conf** make sure they are the right ones for your display. 

```
Section "Monitor"
    Identifier     "Generic"
    HorizSync       28.0 - 80.0
    VertRefresh     48.0 - 75.0
    Option         "DPMS"
EndSection
```

---

### Post by fox112 on 2007-08-10
Wow, i can't believe it... it worked :) I can run 1280x1024 with the nv driver. You're my hero z0mbie. Solved!

---

