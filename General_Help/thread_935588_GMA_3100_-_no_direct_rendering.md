---
title: "GMA 3100 - no direct rendering"
date: 2008-10-01
forum: General Help
---

### Post by sakul07 on 2008-10-01
I'm using Ubuntu 8.04 on a PC, with an G31PR motherboard, that has an GMA 3100 intergrated, but i couldn't get DIRECT RENDERING to work... Nevertheless, the system works perfectly! i'm running compiz, on a 1680x1050 resolution and everything works, but gOOGLE Earth... i haven't tried any 3d games yet... and i've never edited my xorg file.. it is just as it came by default...

how can i get Direct Rendering to work?

here some more info:

glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

glxgears
6716 frames in 5.0 seconds = 1341.708 FPS

---

### Post by sakul07 on 2008-10-02
anyone?

---

### Post by fragos on 2008-10-02
My Dell 1420n has the Intel chip as well and runs well but also reports no direct rendering. glxgears will give you an unscientific frame rate but it indicates that the Intel chip is achieving frame rates as high as the Nvidia card on my desktop. I don't see anytrhing to be concerned about.

---

### Post by IusedTObeSOMEONEelse on 2008-10-02
> **sakul07 said:**
> anyone?

What worked for ME was changing depth from 24 to 16

---

### Post by sakul07 on 2008-10-02
> **MustangSallydd said:**
> What worked for ME was changing depth from 24 to 16

and how can i do that??

---

