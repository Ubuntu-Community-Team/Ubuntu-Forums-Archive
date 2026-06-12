---
title: "1360x768 modeline for a Samsung LE32R3"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by zen_guerrilla on 2007-01-31
Hello all,
Yesterday I installed Edgy on a friend's system and I have a problem. His system has a GeForce4MX400 video card (works OK with nvidia-legacy) and it's connected to a Samsung LE32R3 LCD TV with a 'VGA' cable.
The TV's native resolution, 1360x768 is not supported by default so I've tried to create a modeline for it using this modeline generator ([http://xtiming.sourceforge.net](http://xtiming.sourceforge.net)) but I don't know how. On the TV's manual I've found these specs:
Horizontal Frequency (kHz): 47.712
Vertical Frequency (Hz): 60.015
Pixel Clock Frequency (MHz): 85.800
Sync Polarity (H/V): +/+

TIA,
zen

---

### Post by mobrien118 on 2008-03-06
I am also interested in solving this problem as I have a nVidia 8500GT hooked up to a Dell W3201C which is very much similar to the monitor you describe.

Ive seen modelines with all 0's. I will try that and see what happens.

P.S. before I installed the nVidia drivers a few hours ago, it was working perfectly on the integrated Intel 950 card, but watching 720p wasn't smooth enough for me so I had to go get this card and mess everything up :-P

--mobrien118

---

### Post by wretchedmage on 2008-03-06
I'm using a TV.   SAMSUNG LN3251DX.  It defaults to 1360x768.  But if I select a monitor , it gets stuck at 1024x768 and I have to restore again.

---

### Post by mobrien118 on 2008-03-11
OK, so I installed the nVidia driver using the restricted drivers thing, THEN I used "envy" to get the latest nVidia drivers (nice tool BTW). THEN I used this modeline:

 ModeLine       "1360x768@60" 85.5 1360 1440 1552 1792 768 771 777 795 +hsync +vsync

and it seems to be working. It doesn't seem like it is ACTUALLY using this modeline, but what do I know, it's the only one in xorg.conf bigger than 1024x768 so it must be it.

Aside, I discovered that the problems I was having with the picture being smooth (while playing 720p video) were NOT caused by insufficient video hardware. It was because of some issues with the fancy video effects in ubuntu. I discovered this because video looked fine in kubuntu and xubuntu and KDE4, which I installed to try this (and also just to mess around with). So basically the video card was a waste of $$$ for what I want the box to do. Oh well.

--mobrien118

> **mobrien118 said:**
> I am also interested in solving this problem as I have a nVidia 8500GT hooked up to a Dell W3201C which is very much similar to the monitor you describe.

Ive seen modelines with all 0's. I will try that and see what happens.

P.S. before I installed the nVidia drivers a few hours ago, it was working perfectly on the integrated Intel 950 card, but watching 720p wasn't smooth enough for me so I had to go get this card and mess everything up :-P

--mobrien118

---

### Post by mobrien118 on 2008-03-11
Also, it looks like you have enough information to use this tool:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

I don't know my pixel clock rate so I am not sure it will work for me.

Good luck.


> **zen_guerrilla said:**
> Hello all,
Yesterday I installed Edgy on a friend's system and I have a problem. His system has a GeForce4MX400 video card (works OK with nvidia-legacy) and it's connected to a Samsung LE32R3 LCD TV with a 'VGA' cable.
The TV's native resolution, 1360x768 is not supported by default so I've tried to create a modeline for it using this modeline generator ([http://xtiming.sourceforge.net](http://xtiming.sourceforge.net)) but I don't know how. On the TV's manual I've found these specs:
Horizontal Frequency (kHz): 47.712
Vertical Frequency (Hz): 60.015
Pixel Clock Frequency (MHz): 85.800
Sync Polarity (H/V): +/+

TIA,
zen

---

