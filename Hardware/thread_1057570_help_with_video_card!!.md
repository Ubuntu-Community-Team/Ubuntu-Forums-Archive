---
title: "help with video card!!"
date: 2009-02-01
forum: Hardware
---

### Post by Bacha on 2009-02-01
Not sure i'm at the right place. I just installed Ubuntu 8.10 Desktop Edition and I can't get my nVidia GeForce4 MX 440 with AGP8X to go bigger than 800x600. I tried installing drivers and all that kinda stuff I saw on forums but it doesn't solve my problem: still stuck in  800x600 and it's so small :(
can anybody help me please? :)

---

### Post by damagedigital on 2009-02-02
dude...I'm also new here..but I'll try my best to help u out...
1)have tried downloading the driver from NVIDIA website?
2)if you have u need to install the driver from the terminal not x window..just do a killinit 1 on the terminal and u will enter the cmd line after the reboot.

3)from there sudo sh ./<packagename>.run 

example ::
sudo sh ./NVIDIA-Linux-x86-180.22-pkg1.run

4)follow the instruction on your screen

5)reboot ie:killinit 0

viola!!ur new driver has been successfully install

p/s::to all the seniors out there..pls correct me if my steps are wrong...thanks...

---

### Post by Divider on 2009-02-02
Post glxinfo.


```
sudo glxinfo
```

---

### Post by Bacha on 2009-02-02
alex@livingroo:~$ sudo glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

---

### Post by Divider on 2009-02-02
your xconfig isnt correct thats why, post your xorg.conf and i'll see what i can do for you.

---

