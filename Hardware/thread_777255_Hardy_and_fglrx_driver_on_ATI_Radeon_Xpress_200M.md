---
title: "Hardy and fglrx driver on ATI Radeon Xpress 200M"
date: 2008-05-01
forum: Hardware
---

### Post by hanspb on 2008-05-01
Ok, I have tried to search the net and find a solution, but I have not been able to find a satisfactory one.

I upgraded my laptop to Hardy yesterday, and now I can't get the fglrx driver to work. The ATI card is not listed in the Hardware Drivers dialog like it used to be. According to Synaptic, xorg-driver-fglrx version 1:7.1.0-8-3+2.6.24.12-16.34 is installed. Fglrxinfo gives me:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```
like it always will do when the fglrx driver is not in use. Also, fglrx is in my xorg.conf file. But how to activate it? I need it among other things to use Google Earth.

---

### Post by chek2fire on 2008-05-01
have you try to use envyng-gtk to install the driver? You can find it from synaptic.

---

### Post by hanspb on 2008-05-01
I had not, but I have now. No change at all.:(

---

