---
title: "Problem to configure X1400 whit edgy"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by meditolafuga on 2007-01-23
>  dpkg -l | grep fglrx
rc  fglrx-6-8-0                            8.32.5-2                             X Window display driver for the ATI graphics
ii  xorg-driver-fglrx                      7.1.0-8.28.8+2.6.17.7-10.1           Video driver for ATI graphics accelerators

After installed fglrx package and 

 > # aticonfig --initial

I receive this error :

> ~# fgl_glxgears 
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30



I have installed fglrx from normal ubuntu package.

I need help for configure 3D, I am a Blender users :)
 
Thanks

---

