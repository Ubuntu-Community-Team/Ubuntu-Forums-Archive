---
title: "NVIDIA GeForce Go 7600 driver install"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by Catalonian on 2007-02-21
Hey all, 
I'm having problems installing drivers for gforce go 7600 on my laptop. I have installed the nvidia-glx drivers but it doesnt seem to work out. If I put sudo nvidia-glx-config enable on the terminal I get as response: 

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

I'm pretty sure that I have it installed (just directly form the add/remove.)

If I put glxinfo | grep rendering on the terminal I get as response:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Any pro that could help me out? thx in advance :)

---

### Post by Rinias on 2007-02-21
[http://www.ubuntuforums.org/showthread.php?t=235220](http://www.ubuntuforums.org/showthread.php?t=235220)

Might be worth a shot trying what is suggested in this thread ;) Let us know if you still have problems :)

Rinias

---

