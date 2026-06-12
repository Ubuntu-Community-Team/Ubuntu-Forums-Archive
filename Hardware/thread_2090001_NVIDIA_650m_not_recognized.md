---
title: "NVIDIA 650m not recognized?"
date: 2012-11-30
forum: Hardware
---

### Post by carnivroar on 2012-11-30
I successfully followed the tutorial on this page 

[http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

and got my 650m to work.

However my GPU is now listed as:

-OpenGL-
Vendor		: Intel Open Source Technology Center
Renderer		: Mesa DRI Intel(R) Ivybridge Mobile 
Version		: 3.0 Mesa 9.0
Direct Rendering		: Yes

Is this correct?

Also is there a simple way to check if my 650m is enabled to CUDA programming? I need it ASAP for an assignment so I need to know if it's working.

Thanks!

screenshot: [http://img.photobucket.com/albums/v253/Hatsuharu1399/Screenshotfrom2012-11-30220632.png](http://img.photobucket.com/albums/v253/Hatsuharu1399/Screenshotfrom2012-11-30220632.png)

also:

raphael@raphael-N56VZ:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd1 (rev ff)

---

### Post by gnusci on 2012-11-30
Did you try:

$ nvidia-settings

---

### Post by carnivroar on 2012-12-01
Okay I finally got it work but now compiz stopped working?

And my intel GPU is no longer listed.

:confused:

---

### Post by carnivroar on 2012-12-01
Now my Intel GPU is not working

$ glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".


compiz no longer works.

---

### Post by carnivroar on 2012-12-01
Bump.

Need to know if I can fix this, or else I'll have to return this laptop.

---

### Post by carnivroar on 2012-12-01
My solution

[http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

plus my comment on the bottom (the one posted at 2012-12-01 20:57:27 EST)

---

