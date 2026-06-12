---
title: "Laptop LCD Display"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by moon2js on 2004-11-01
hi,

I'm a bit new to Linux and hardware configuration. I've just installed Ubuntu and for the most part it works great. But occasionally there seems to be some kind of distortion on the screen, along the horizontal lines. It's barely noticable and it happens occasionally.

I'm wondering if perhaps the system is configured for a CRT monitor, and I'm wondering how best to configure a Linux system for an LCD (if that's even necessary).

---

### Post by njreid on 2004-11-08
Hi moon,

I found a couple of points when configuring Ubuntu for use on an LCD useful:

1) Enable Subpixel Smoothing
Computer->Desktop Preferences->Fonts
Select 'Subpixel Smoothing'; Click Details and select your prefered level of smoothing/hinting.

2) Enable freetype Font Hinting (this may now be done automatically)
Open /etc/fonts/local.conf in your favourite editor with sudo (eg. sudo vi /etc/fonts/local.conf) and uncomment the freetype autohinter module by deleting the lines:
'<!--' before and '-->' after the '<match ...' entry relating to autohint. Ensure you leave the real 'Uncomment below to enable' comment commented! :)

Cheers,

Nic

---

### Post by aledin on 2004-11-08
[QUOTE=njreid]
2) Enable freetype Font Hinting (this may now be done automatically)
Open /etc/fonts/local.conf in your favourite editor with sudo (eg. sudo vi /etc/fonts/local.conf) and uncomment the freetype autohinter module by deleting the lines:
'<!--' before and '-->' after the '<match ...' entry relating to autohint. Ensure you leave the real 'Uncomment below to enable' comment commented! :)
[/QUOTE]

There is an easier way too: sudo dpkg-reconfigure fontconfig

These are the goodies of being debian inside. ;)

---

