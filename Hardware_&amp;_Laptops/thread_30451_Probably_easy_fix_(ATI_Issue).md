---
title: "Probably easy fix (ATI Issue)"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by xylicon on 2005-04-28
I have the fglrx driver installed and its currently working I just don't have 3d acceleration, I read the xorg log and heres the following errors I came up with, can someone please help me fix them? (Using ATI 9800 Pro)

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *

This might also help
[http://www.xylicon.com/exp/downloads/xorg.conf](http://www.xylicon.com/exp/downloads/xorg.conf)

---

### Post by gizmospc on 2005-04-30
This is what helped me get 3d acceleration through my ATI 9600:

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)

---

