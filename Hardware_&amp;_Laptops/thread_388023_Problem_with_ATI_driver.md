---
title: "Problem with ATI driver"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by mario8723 on 2007-03-19
Why am I getting this? My 3D acceleration is not working, and I'm not sure how to fix it....

mario8723@mario8723-desktop:/usr/X11R6/lib$ fglrxinfoXlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by adam.tropics on 2007-03-19
If you're on feisty, i don't know which guides you have used but [this one works]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") for me every time. Also, If you are on Dapper or Edgy, there are relevant guides there also.

---

### Post by mario8723 on 2007-03-19
Worked like a charm! Now I get:

mario8723@mario8723-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro
OpenGL version string: 2.0.6334 (8.34.8)

I think I never disabled compositing...Anyway, thanks very much for the assist!

---

