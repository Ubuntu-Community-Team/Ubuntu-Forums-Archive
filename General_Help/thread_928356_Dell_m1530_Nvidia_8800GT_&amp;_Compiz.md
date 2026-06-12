---
title: "Dell m1530 Nvidia 8800GT &amp; Compiz"
date: 2008-09-23
forum: General Help
---

### Post by r1zen187 on 2008-09-23
I have searched multiple thread and tried multiple things, here is what happens.

If I try to install the nvidia-new drivers and restart, I get tons of vertical lines and I am forced to restore my config back to it's original. 

This is another good description of my problem:
[http://ubuntuforums.org/showthread.php?t=738305](http://ubuntuforums.org/showthread.php?t=738305)

"The proprietary drivers of the NVIDIA 8600GT on my Dell XPS m1530 do not work. I installed Hardy Heron from the live CD (everything worked perfectly) and immediately started the Restricted Drivers window to let the system install and configure the nvidia-glx-new package. All went well until I rebooted the system. Once the xserver was up I saw a white screen with random black lines. I heard the login-screen come up. I was able to log in. I started the alt + ctrl + f1 terminal, logged in, changed the xorg.conf driver section back to 'vesa' and rebooted."

---

### Post by Crafty Kisses on 2008-09-23
What are the results of this command:
```
glxinfo
```

---

### Post by r1zen187 on 2008-09-23
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
0x49 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by r1zen187 on 2008-09-24
Anyone?

---

