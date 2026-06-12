---
title: "fglrx install: Xorg.conf is blank?"
date: 2008-06-11
forum: Hardware
---

### Post by NinjaCodemonkey on 2008-06-11
I am following the instructions over at wiki.cchtml.com, on installing the fglrx drivers. I tried the bog standard repository install, but when I get to editing Xorg.conf, the file is empty; and when I close gedit it tells me to save changes (maybe it always does that, I don't use it much).

Ultimately I have 2 problems (well, there are more, but these 2 for now):
1) Why is Xorg.conf empty (permissions?)
2) Still can't get fglrx installed.

Basically I want OpenGL support. Mobo is a Foxconn (PoS, audio drivers are terrible even on Windows) with an ATI Chipset. Card is a 512MB Radeon 2600Pro made by Sapphire I believe. Running 8.04, upgraded from 7.10 which was the liveCD I had.
The default drivers work fine in that the display works, just without OpenGL.
The current install I have is probably unclean from so many half-installs, should I completely format and try again?

---

### Post by overdrank on 2008-06-11
> **NinjaCodemonkey said:**
> I am following the instructions over at wiki.cchtml.com, on installing the fglrx drivers. I tried the bog standard repository install, but when I get to editing Xorg.conf, the file is empty; and when I close gedit it tells me to save changes (maybe it always does that, I don't use it much).

Ultimately I have 2 problems (well, there are more, but these 2 for now):
1) Why is Xorg.conf empty (permissions?)
2) Still can't get fglrx installed.

Basically I want OpenGL support. Mobo is a Foxconn (PoS, audio drivers are terrible even on Windows) with an ATI Chipset. Card is a 512MB Radeon 2600Pro made by Sapphire I believe. Running 8.04, upgraded from 7.10 which was the liveCD I had.
The default drivers work fine in that the display works, just without OpenGL.
The current install I have is probably unclean from so many half-installs, should I completely format and try again?

HI and I believe it is xorg.conf not Xorg.conf
```
sudo gedit etc/X11/xorg.conf
```

---

### Post by NinjaCodemonkey on 2008-06-11
Just copied and pasted the exact line from the guide. Still the same problem, totally blank. It actually takes a second to load the file, but shows nothing.

Thanks for pointing that out though...

Edit: following the recent attempt I've just checked the directory. Shock horror: the file doesn't actually exist. I have a xorg.conf.original-0 and a xorg.conf.failsafe
I'd've checked this earlier but I thought gedit would report a file not found error rather than load nothing.

---

### Post by NinjaCodemonkey on 2008-06-14
Still got this problem...

Am I better off formatting to restore everything back to raw, and keep reinstalling until I get fglrx in properly and working?

Since I'm dualbooting with an ever slower XP install which I'm hoping to format at some point as well. I'm hoping I'll be able to get 2 birds in one stone here...

Is there any way to, say, reinstall relevant components (X server, for example) without having to reinstall the whole OS?

---

