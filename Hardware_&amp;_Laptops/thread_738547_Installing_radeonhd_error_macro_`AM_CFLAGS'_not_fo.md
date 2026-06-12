---
title: "Installing radeonhd error: macro `AM_CFLAGS' not found in library"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by soccerdog8 on 2008-03-28
Hey guys, i'm trying to install the open-source driver, radeonhd for my ATI mobility radeon x1400. I'm doing this hoping to get the suspend and hibernate features to work. I realize that this driver doesn't support 3D graphics acceleration, but i have windows for games, so who cares?

So here's the problem. When I run the commands I found in [this howto]("http://www.phoronix.com/scan.php?page=article&item=843&num=1"), i get this error after running "./autogen.sh --prefix=/usr" :
```
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
dautoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.ac: 254: macro `AM_CFLAGS' not found in library
autoreconf: aclocal failed with exit status: 1

```
Then, there's no makefile to make, which is a problem. :confused:

So, I'd appreciate somebody linking me to any thread where i can find out how to make the close-source driver, "fglrx," enable 3D graphics and do suspend / hibernate features for my *specific* graphics card. Or, maybe you can help me install this radeonHD driver. I'm open to whatever you guys have found that works. It'd be nice if somebody helped me that actually has this graphics card and has gotten it to work.

---

### Post by soccerdog8 on 2008-04-01
Alright, since no one's replying, maybe i should refine my question:

I don't care about enabling 3D acceleration: I'm not going to play games on ubuntu. I just want to be able to put my computer to sleep when i want to. How do i do it? 

Computer: Dell E1505
Graphics card: Mobility Radeon X1400
OS: Ubuntu Gutsy 7.10

Should i try this radeonHD driver? I get the problem i mentioned. How do i get around it?

Should i stick with the fglrx driver? How do i fix the suspend / hibernate mode?

---

