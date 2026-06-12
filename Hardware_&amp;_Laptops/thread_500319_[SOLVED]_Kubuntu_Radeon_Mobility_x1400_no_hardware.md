---
title: "[SOLVED] Kubuntu Radeon Mobility x1400 no hardware acceleration"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by ninja_in_pajamas on 2007-07-13
I have been fumbling with this one for a while now. I am using Kubuntu on a Dell inspiron e1505.  The Video card is a radeon mobility x1400.  I had acceleration until a couple of weeks ago when an update killed it.  When I do fglrxinfo I I got Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Any ideas on how to fix all of this?

---

### Post by w4ett on 2007-07-13
Was this after a Kernel update???...if so you'll need to re-install the restricted driver for your chipset.

---

### Post by ninja_in_pajamas on 2007-07-14
Not completely sure if it was a kernel update.  How would I reinstall the restriced drivers?

---

### Post by w4ett on 2007-07-14
I use ENVY...it installs the restricted drivers and mods you xorg.conf:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by ninja_in_pajamas on 2007-07-16
In the words of Peter Griffin ' Frickin sweet!"  Envy fixed it and now I have full hardware accelerated 3d.

---

