---
title: "3d-accelaration on my Fujitsu Amilo V3205, intel 950"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Ole Eivind on 2007-06-04
I have a Fujitsu siemens Amilo Pro V3205 laptop, running kubuntu. If I'm not mistaken the graphics card is Intel Graphics Media Accelerator 950.

I have the correct drivers, and the resolution (1280x800) was fixed with 915resolution, but I have no 3d-acceleration. "glxinfo | grep direct" gives me this:
```
glxinfo |grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

---

### Post by veloce on 2007-06-05
> **Ole Eivind said:**
> I have a Fujitsu siemens Amilo Pro V3205 laptop, running kubuntu. If I'm not mistaken the graphics card is Intel Graphics Media Accelerator 950.

I have the correct drivers, and the resolution (1280x800) was fixed with 915resolution, but I have no 3d-acceleration. "glxinfo | grep direct" gives me this:
```
glxinfo |grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

If you are not using dual monitors, upgrade your driver to "intel":

```
sudo apt-get -install xserver-xorg-video-intel

```

and change the reference to "i810" in xorg.conf to "intel".

You can then uninstall 915resolution and you are more likely to have 3d acceleration working.

DON'T do this if you are using dual monitors, for some reason it just doesn't work.

---

### Post by Ole Eivind on 2007-06-05
> **veloce said:**
> DON'T do this if you are using dual monitors, for some reason it just doesn't work.

Does that go for tv-out as well?

---

### Post by veloce on 2007-06-05
> **Ole Eivind said:**
> Does that go for tv-out as well?

No it doesn't.  I've not done it, but apparently Feisty plus the "intel" driver is plug and play for tv-out.  There are some issues with people only getting B/W - conjecture on this is NTSC vs PAL (which doesn't quite make sense to me).

---

### Post by Ole Eivind on 2007-06-06
Great! Thanks a bunch for your help!

I have a couple exams on fri/sat, and will try this when I'm finished with them. I'll post my results then.

---

