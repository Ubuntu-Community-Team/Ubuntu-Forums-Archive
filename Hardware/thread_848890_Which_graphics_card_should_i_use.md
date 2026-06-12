---
title: "Which graphics card should i use"
date: 2008-07-03
forum: Hardware
---

### Post by CameronCalver on 2008-07-03
Hello one of my old computers graphics cards recently died and i have 2 cards i can put in. One is a Nvidia Gefore MX 2 /400 32mb card and my other one is a asus AGP V7700/32mb TVR just wondering which one would be the best?

---

### Post by ProbablyX on 2008-07-04
The V7700 is a GeForce2 Ultra, if Google tells me right.
The MX card is a cheap version and Ultra is way better,

Go for the 7700

---

### Post by Sef on 2008-07-04
> Go for the 7700 

Second that.

---

### Post by CameronCalver on 2008-07-04
ok thanks guys for that but now i think im gunna have to stick with this incredibly low res for some reasons and i cant reconfigure xserver because im on hardy?

---

### Post by CameronCalver on 2008-07-04
SOLVED i downloaded the nvidia legacy drivers and everything is sweet just one thing is there an app to test for graphic card performance and to check if the all the graphic drivers are working?

---

### Post by paulisdead on 2008-07-04
glxinfo should spew out a bunch of info about what opengl features your card and drivers support.  You can use glxgears to get an idea of performance, but I don't remember at all, what a decent frame rate in glxgears would be for cards that old, plus with different quality settings.  You can always read the xorg logs if you really want to.

---

### Post by CameronCalver on 2008-07-04
well with glxinfo i get
```
cameron@ubuntu:~$ glxinfo
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
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

and with glxgears i get 
```
cameron@ubuntu:~$ glxinfo
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
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

i really need some noob help installing the graphics drivers if i do it threw the installer in ubuntu i cant get my 1400x900 res i like

---

### Post by ProbablyX on 2008-07-04
What does 
```
 cat /etc/X11/xorg.conf | grep Driver   
```

tell you?

If you get a line saying Driver "nv"

try opening /etc/X11/xorg.conf as root (sudo) and change the line that says 
```
 Driver "nv"
```  
     to 
```
 Driver "nvidia"
``` 

The Driver part should be under 
```
 Section "Device"
``` 

 Note that you must restart the X server after saving by pressing ctrl+alt+backspace

If you dont get neither "nv" or "nvidia" at the first command, try adding:
```
 Driver "nvidia"
``` 

under  Section "Device"  in the xorg.conf file. If there is already a "Driver" line followed by something else than nv or nvidia, change it to nvidia.

Running
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```  
can be a good idea first, that is creating a backup of the file

---

