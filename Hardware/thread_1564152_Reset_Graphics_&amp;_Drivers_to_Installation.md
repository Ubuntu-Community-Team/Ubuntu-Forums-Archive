---
title: "Reset Graphics &amp; Drivers to Installation?"
date: 2010-08-30
forum: Hardware
---

### Post by Ruairi on 2010-08-30
My child-like curiosity has led me to fiddle with my drivers and graphics settings and, surprise surprise, I've now hit a problem or six. I could do all these things when I first installed Ubuntu but now they don't work.

If I try and play Warsow, it doesn't start and starting it from the terminal gives me this error:
```
----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
********************
ERROR: Received signal 11

********************
Error: Received signal 11
```

If I try to open Google Earth:

```
Google Earth is unable to identify your graphics card. this is most likely because the driver for your graphics card has not been installed.
```

If I try to run:

```
aticonfig
```

I get:

```
aticonfig: No supported adapters detected
```

Under Visual Effects in Appearance, only None can be selected, and I have used Normal and Extra in the past (I know so because I remember squealing with joy at the effect distorting the shape of a window when it was dragged. Good times...:D

Hardware Driver also says there are 'No Proprietary Drivers Are In Use On This System'. Synaptic says that xorg-driver-fglrx and fglrx-kernel source are installed, as are xserver-xorg-video-radeon and xserver-xorg-video-ati.

Any help would be appreciated. Remember, I *could *do these things once, I just can't do them now.

Cheers, Ruairi

Oh, and I'm using 9.10 Karmic.

---

### Post by akoskm on 2010-08-30
If the Hardware Drivers says that there are no proprietary drivers installed, why don't you install the recommended one > Reboot and try again?

---

### Post by Ruairi on 2010-08-30
> **akoskm said:**
> If the Hardware Drivers says that there are no proprietary drivers installed, why don't you install the recommended one > Reboot and try again?

If you mean fglrx, all the necessary packages are already installed. However, ATI claims my graphics card (Xpress) isn't supported. So how was I using 3D before...?

---

### Post by Ruairi on 2010-08-30
Fixed it. I uninstalled every trace of fglrx and went with the standard ati/radeon driver and it worked a charm. I was acting like a spoilt teenage girl who wants the more expensive brand of fake tan/closed-source driver.

Anyway, that's all sorted. Radeon is the way forward. Thanks for the help!

---

### Post by akoskm on 2010-08-30
> **Ruairi said:**
> Fixed it. I uninstalled every trace of fglrx and went with the standard ati/radeon driver and it worked a charm. I was acting like a spoilt teenage girl who wants the more expensive brand of fake tan/closed-source driver.

Anyway, that's all sorted. Radeon is the way forward. Thanks for the help!

Oh, then I'm late with the answer. :o
Anyway, good to hear, happy hacking!

---

