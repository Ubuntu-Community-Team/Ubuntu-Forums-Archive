---
title: "[SOLVED] Reconfigure x?"
date: 2008-09-12
forum: General Help
---

### Post by DougieFresh4U on 2008-09-12
How do I reconfigure x? Every time I try, it only goes to the keyboard, then ends reconfiguring. It used to go through a whole bunch of other things.

---

### Post by whouseswindowsanyway on 2008-09-12
Try this in terminal

dpkg-reconfigure xserver-xorg
after config press ctrl+alt+backspace to restart X....

preferable make a backup first!

file is in : /etc/X11/xorg.conf

---

### Post by DougieFresh4U on 2008-09-12
> **whouseswindowsanyway said:**
> Try this in terminal

dpkg-reconfigure xserver-xorg
after config press ctrl+alt+backspace to restart X....

preferable make a backup first!

file is in : /etc/X11/xorg.conf

That is what I ran and it only reconfigures keyboard, Thanks

---

### Post by marufaberlin on 2008-09-12
what graphics card do you have?

---

### Post by cdtech on 2008-09-12
Add the -phigh flag:
sudo dpkg-reconfigure **-phigh** xserver-xorg

---

### Post by DougieFresh4U on 2008-09-12
> **cdtech said:**
> Add the -phigh flag:
sudo dpkg-reconfigure **-phigh** xserver-xorg
Did that, and nothing came back to reconfigure

> **marufaberlin said:**
> what graphics card do you have?
I have the onboard intel 865 chipset

This is output that I believe something is wrong:
[B]dougie@DougiesLeanMachine:~$ glxinfo | grep direct
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
dougie@DougiesLeanMachine:~$ glxinfo 
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
Segmentation fault (core dumped)
dougie@DougiesLeanMachine:~$[/B]

---

### Post by cdtech on 2008-09-12
I would rename the "/etc/X11/xorg.conf" to "xorg.conf.bak" - reboot in recovery mode then issue the command above. This will create a new config file detecting your hardware. You can always rename it back to the original if it doesn't work for you.

---

