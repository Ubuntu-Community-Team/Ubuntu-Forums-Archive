---
title: "8800gt =&gt; glxgears: 6k fps"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by funder on 2008-01-30
Hi
I'm running a 8800gt card with the 169.09 nvidia driver. When running glxgears in windowed mode I get about 6k (5k with compiz turned on) fps. As far as I can see from googleing I should be getting 3 times that.
Also, the cpu(one of them) is running at 100% while running glxgears.
I also feel compiz fusion running slow sometimes.

After alot of problems I finally got my 8800gt and panasonic 42pz70 to agree on running X in 1080p, which is why I've set alot of variables in the xorg.conf file.

I've attached the xorg.conf and environment file (cant add Xorg.0.log because the forum thinks it's too big).
It runs at full speed in windows.
Any ideas what could be slowing it down?

---

### Post by Daelyn on 2008-01-31
This might be a stupid question, but, when looking in your Xorg, I think I'm seeing your 
```
 screen 0 
``` in the wrong section?

It is to identify the screen and then should not be in the "device" section, if I'm not entirely wrong??

Also, I think it should be ```
 screen "0" 
```.

Question is, do you need that option? 
Could someone knowing please have a look at this guys xorg? I'm too newbie for this.

---

### Post by funder on 2008-01-31
Good question.I have no idea. My config file is really a bit of a frankenstein of alot of config files around the net - in an attempt to get it to run in 1080p.
I'll try to clean it up when I get home and attach a cleaner version.

Does anyone know what it means that one of the cores is running at 100% when running glxgears? The card must be doing some kind of 3d acceleration to get 6k in glxgears, right?

---

### Post by funder on 2008-01-31
Must settings are actually needed to run full hd. 

Anyways, does anyone have an idea of what could be the problem or how I could find out?

---

