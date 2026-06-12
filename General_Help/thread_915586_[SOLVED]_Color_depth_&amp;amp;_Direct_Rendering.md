---
title: "[SOLVED] Color depth &amp;amp; Direct Rendering"
date: 2008-09-10
forum: General Help
---

### Post by DougieFresh4U on 2008-09-10
I am trying to figure out why my machine has:
[B]8 bit
16 bit
24 bit[/B]
listed and **WAS** set at **8 bit**
I changed it in the Start Up Manager to 16 bit.
Then I was checking via terminal for Direct rendering and came up with this
```
dougie@DougiesLeanMachine:~$ glxinfo | grep direct
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
dougie@DougiesLeanMachine:~$ 
```
Some thing is not right. Can some one enlighten me please?

---

### Post by Ptero-4 on 2008-09-10
the bitdepth set at startupmanager is for the framebuffer which is used by usplash. You need to set your bitdepth with displayconfig-gtk.

---

### Post by DougieFresh4U on 2008-09-10
Please, some one please explain why the posted terminal out put saying all that missing stuff. I would really like to fix that. And would reconfiguring x fix it?

---

### Post by DougieFresh4U on 2008-09-10
Sorry for the 'bump'
Please some one shed some light on this.
Would reconfiguring x help and if so, 'code' please

---

### Post by DougieFresh4U on 2008-09-10
I really need a 'guru' this morning, please.
Don't want to bork the box, as I might start fixing till it's broke :(

---

### Post by Ptero-4 on 2008-09-10
displayconfig-gtk is a X11 app. If your X won't run you might want to boot into the recovery mode (press esc to bring the grub menu and choose the entry that says "recovery") and when the blue menu dialog appears choose the option xfix. That fixes X11 when it can't even start.

---

### Post by DougieFresh4U on 2008-09-10
> **Ptero-4 said:**
> displayconfig-gtk is a X11 app. If your X won't run you might want to boot into the recovery mode (press esc to bring the grub menu and choose the entry that says "recovery") and when the blue menu dialog appears choose the option xfix. That fixes X11 when it can't even start.

x runs and I can restart with no problems.
My concern is what does the output that I posted mean? and if reconfiguring x will fix it.
It's like every line says missing and it doesn't say yes or no for Direct Rendering

---

### Post by DougieFresh4U on 2008-09-11
sorry for the bump, but need the help please :confused:

---

### Post by DougieFresh4U on 2008-09-11
I am really sorry to keep bumping. 
Please, I really need some answers:
Will reconfiguring x fix the posted terminal output? 
Why is it saying all those things are missing?
How can I get Direct Rendering back?

---

### Post by Ptero-4 on 2008-09-13
Then I guess the problem is that you´re missing some of the glx libraries (look for libglu and libgl in aptitude).

---

