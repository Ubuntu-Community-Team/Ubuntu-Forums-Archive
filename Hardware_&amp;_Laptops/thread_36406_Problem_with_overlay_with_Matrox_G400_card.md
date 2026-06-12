---
title: "Problem with overlay with Matrox G400 card"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by Dolboeb on 2005-05-23
Hi all,

I have Matrox G400 video card and seems like I can't get xv working. The problem is very strange one though: if a movie is small (like when playing a VCD) everything works, but when it's larger, like when playing DVD - then some players like mplayer and vlc crash with "BadAlloc() error", and some like xine - just do not show any video. Switching off xv output in mplayer helps, but then fullscreen mode becomes not available.

I have a feeling the problem is somehow related to the video card/driver, but I can't find any sure answer: some websites claim xv works for this card, and some (xinehq.de) refer to [xorg bug 474](http://lists.freedesktop.org/archives/xorg-bugzilla-noise/2004-June/000841.html).

What I'd like to know however is whether it is possible to watch DVDs in fullscreen mode with this card? :)

Any help would be nice!

---

### Post by JonahRowley on 2005-05-23
Which drivers are you using?  I use a G450 and I've had better luck with the binary drivers from Matrox.  The X versions don't match up 100%, but they still work fine.

---

### Post by Dolboeb on 2005-05-23
[QUOTE=JonahRowley]Which drivers are you using?  I use a G450 and I've had better luck with the binary drivers from Matrox.  The X versions don't match up 100%, but they still work fine.[/QUOTE]

I use mga driver which comes in Hoary distro...

---

### Post by JonahRowley on 2005-05-23
Try the accelerated drivers from Matrox.  I've had better luck with them, and they're quite a bit faster.

---

### Post by Heart on 2005-06-14
[QUOTE=JonahRowley]Try the accelerated drivers from Matrox.  I've had better luck with them, and they're quite a bit faster.[/QUOTE]
So, you choosed "6.8.2" in the install process of this driver for X version although the  proposed list goes only til "6.8.1"?

---

### Post by mindhaq on 2005-06-16
I use the Matrox Binary drivers for my G400, and selected the 6.8.1 version during install. This seems to work okay, although there are a couple of warnings during X startup:

```
Symbol xf86I2CProbeAddress from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CProbeAddress from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
```

---

