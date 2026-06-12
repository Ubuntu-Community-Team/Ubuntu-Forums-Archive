---
title: "ATI Mobility Radeon X1350"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by paulo_ on 2007-12-21
Hello.

I have an LG Z1 Pro Express Dual. Everything was detected and (supposedly) running ok. I say "supposedly" because when i type "glxinfo | grep render" it says "direct rendering: No". My graphic card is an ATI Mobility Radeon X1350.

Can someone help?...


paulo@paulo-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1350
OpenGL version string: 2.0.6473 (8.37.6)

paulo@paulo-laptop:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Mobility Radeon X1350
paulo@paulo-laptop:~$

---

### Post by paulo_ on 2007-12-21
hello? :(

---

### Post by paulo_ on 2007-12-21
Ok...

If I type "export DISPLAY=:0.0", I get:

paulo@paulo-laptop:~$ glxinfo | grep render
direct rendering: Yes
GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Mobility Radeon X1350

Found the answer [here]("http://ubuntuforums.org/showthread.php?t=590894").

:)

---

