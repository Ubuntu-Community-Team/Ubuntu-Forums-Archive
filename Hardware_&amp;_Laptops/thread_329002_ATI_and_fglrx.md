---
title: "ATI and fglrx"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by TannerLD on 2006-12-31
Hi all,

I recently got my ATI driver to work, but when I do fglrxinfo I get this:

```
display:  :0.0 screen: 0
Open GL vendor string: ATI Technologies Inc.
OpenGL renderer string: Generic
OpenGL version string; 2.0.6234 (8.32.5)
```

I *think* the opengl renderer is supposed to be something different?

Glxgears doesn't work or any other 3d game (ex: bzflag). All I get is a pixelized section of my desktop background.

Any help?

Thanks
-Tanner

---

### Post by grahams on 2006-12-31
Are you using the ati or fglrx driver? I think the fglrx is required for 3d support. 

See [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html)

---

### Post by TannerLD on 2006-12-31
> **grahams said:**
> Are you using the ati or fglrx driver? I think the fglrx is required for 3d support. 

See [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html)

ATI Drivers.

I'll take a look at that in the morning.

Thanks
-Tanner

---

### Post by mbobak on 2007-01-01
ATI driver or the fglrx driver?

As far as I know, there are two options, the fglrx driver, which is a proprietary, binary-only driver supplied by ATI, and the open-source radeon driver, included with X.Org's xserver.

From the output listed above, it looks like he's using the fglrx driver, but it doesn't look quite right.

My fglrxinfo output looks like this:

```
mjb@mars:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

What video card/chipset do you have installed?
(Check lspci output, if you're not sure.)

-Mark

---

### Post by TannerLD on 2007-01-01
I'm using a ATI Radeon X1300 Pro.

And I do have direct rendering.

Thanks
-Tanner

---

### Post by grahams on 2007-01-01
What does 'glxinfo | grep rendering' report ?

To find which driver you're using you can check xorg.conf and look at the Device section. I'm using the ati driver.

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

---

### Post by TannerLD on 2007-01-01
It says:

Direct rendering: yes

In xorg config it says "vesa".

Thanks
-Tanner

---

### Post by grahams on 2007-01-04
I think you may need to edit /etc/X11/xorg.conf (make a copy of it 1st) and change the driver to fglrx rather than vesa in the Device section.

restart X (ctrl+alt+backspace) and cross your fingers. If X restarts, try 3d again. If it fails, copy the backup of xorg.conf back to /etc/X11/xorg.conf and restart X again to recover. 

Who may want try changing vesa to 'ati' and use the open source driver which I find to be more stable on 6.10

---

### Post by xavier_martinez on 2007-10-31
I run  Ubuntu 7.10 on an Acer 1694 with an ATI Radeon X700. I've solved the pixelized movies changing 'fglrx' for 'ati' in /etc/X11/xorg.conf. Now, movies in totem look great. 
Thanks graham

---

