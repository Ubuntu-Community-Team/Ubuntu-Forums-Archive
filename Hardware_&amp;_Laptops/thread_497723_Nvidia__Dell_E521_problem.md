---
title: "Nvidia / Dell E521 problem"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by matsgd on 2007-07-10
Hey,

I'm new to this forum and Ubuntu in general so be patient with my ignorance.

I installed Kubuntu 7.04 on my Dell E521 (which I totally regret buying, but that's another story). I can't seem to get OpenGL working on the machine. I used Automatix to install the Nvidia drivers, and I see the Nvidia logo when X is restarted. But if I try glxgears, i get:

mats@supernova:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
mats@supernova:~$

and when I do glxinfo, I get:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x7a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
mats@supernova:~$

What is the problem here?

Thanks.

---

### Post by Psychobudgie on 2007-07-10
I also have an E521 but I'm running with a 8600GT. Haven't had any bother with the machine to be honest, but I'm using the latest nvidia binary driver from the nvidia website. Try installing the nvidia driver using Envy which others have suggested as it seems to provide the best results judging by comments on here.

---

### Post by matsgd on 2007-08-05
Okay, so I can get OpenGL to work using Envy as the installer. However, the machine hangs every 30 minutes or so. Total hang -- not just X. The power button is the only option... I'm getting tired of this. Does anyone have suggestions what could be the problem?

thanks.

---

### Post by matsgd on 2008-01-13
Ok, so an update here. After installing 7.10 and having BIOS version 1.1.4, the machine still hung every five minutes or so. Then I used ENVY to install the latest NVIDIA driver, and now the machine works like a charm. It's been up for a day without crashing, and I've been testing a lot of OpenGL stuff that previously was a recipe for crashing. I should mention that I am running the 64 bit version.

At the moment, I am happy - the machine finally seems stable.

---

