---
title: "Driver Support Question"
date: 2014-06-29
forum: Hardware
---

### Post by Kevin_Butler on 2014-06-29
[http://paste.ubuntu.com/7724408/](http://paste.ubuntu.com/7724408/)




ubuntu@CeruleanBlue:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV5 [Vanta / Vanta LT] [10de:002c] (rev 15)
	Subsystem: NVIDIA Corporation Device [10de:0072]
	Kernel driver in use: nouveau
    




                                                                                                                                                
GL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv05 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: no
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no


Unity 3D supported:       no

---

### Post by gordintoronto on 2014-06-30
You forgot the question. However, I'm not sure what you expect from a 14-year-old video card.

---

### Post by Yellow Pasque on 2014-07-01
You are already using the open-source nouveau driver, which is the best (and the only accelerated) driver available for that card.

Your card is so old that it's not even supported by the 96.xx nvidia proprietary driver, so don't try to install an nvidia proprietary driver.

---

