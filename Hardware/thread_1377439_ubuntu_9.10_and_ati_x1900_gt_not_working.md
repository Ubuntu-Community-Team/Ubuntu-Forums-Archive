---
title: "ubuntu 9.10 and ati x1900 gt not working"
date: 2010-01-10
forum: Hardware
---

### Post by toyman on 2010-01-10
hello,


i have a fresh installation ubuntu 9.10 and i cannot install the driver for my video card:
**ati x1900 gt**. the card only works with device 'vesa'
not working: ati, radeon, radeonhd and fglrx


i attached my xorg.0.log, anyone can help me getting 3d enhancement working on ubuntu 9.10 ?


thanks
best regards
toyman

---

### Post by adam814 on 2010-01-10
Well, that card definitely won't work with fglrx.  ATI dropped support for r500 and older chipsets in Catalyst 9.4

Try changing the Driver option in /etc/X11/xorg.conf to "ati" instead of "fglrx" or "radeon".  Also make sure you have the xserver-xorg-video-ati package installed.  This should choose the open-source driver that best suits your hardware (probably radeon).

Also if you've installed fglrx you need to remove it before ati/radeon/radeonhd will work.  Catalyst overwrites parts of the Mesa GLX libraries to make it work with their proprietary driver, which breaks the open-source ones.

I believe there's a script to uninstall it under either /etc/ati or /usr/share/ati, it's been a while since I've used fglrx.

---

