---
title: "ATI Drivers Kubuntu 6.10"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by phil_steele on 2007-02-25
I've just installed Kubuntu and am having trouble installing the ATI graphics drivers. I've followed the manual installation guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
to install the latest drivers, but when running fglrxinfo the out put reads:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I've tried adding:
> Section "Extensions"
Option "Composite" "false"
EndSection
To my xorg.conf file but that actually makes it worse, so bad infact it won't startx. It just displays a blank screen when trying to.

---

### Post by UltraMathMan on 2007-02-25
I believe it's supposed to be [CODE]Section "Extensions"
Option "Composite" "0"
EndSection

Any reason you didn't follow method 1 in the guide?

---

### Post by phil_steele on 2007-02-25
Unfortunately I've tried that as well. It seems there's several ways to turn off Composite.
```
Section "Extensions"
Option  "Composite" "Disable"
EndSection
```
Has the same effect. By the way I'm using the 64bit version of Kubuntu on a radeon X1600.

Method 1 would install the older ATI which have a known problem when running a 64bit version of Xorg.

---

### Post by r4ik on 2007-02-25
Try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by phil_steele on 2007-02-25
Thanks for the help but again I'm getting the same problem. Black screen when loading Xorg. I can however log in without disabling composite in my xorg.conf file, but of course then still without DRI.

fglrxinfo:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

