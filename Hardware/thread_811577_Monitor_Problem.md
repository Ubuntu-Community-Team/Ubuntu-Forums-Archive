---
title: "Monitor Problem"
date: 2008-05-29
forum: Hardware
---

### Post by sidewinder89 on 2008-05-29
Hey! 

    I'm using Viewsonic VA1912wb 19 inch monitor which used to work best at 1440x900 resolution. I'm using vista ultimate as well as XP currently. Everything was fine until I made vista  hibernate for a short time. When I resumed, something upset the resolutions. Now, I'm not able to set to 1440x900 at all! That particular resolution seems to have disappeared! Instead, I'm able to see other new resolutions in the display settings menu. My mobo is Intel DG33FB, with no external graphics card. I tried reinstalling the video adapter drivers, but it didn't help. The same case when I tried logging into XP. My display looks terribly crappy! Also, when I try to set certain resolutions, I get an "out of range" message. Please help. I'm not able to figure out if its the fault of the monitor or the OS.

---

### Post by didac on 2008-05-29
If it happens both with Ubuntu and XP, the problem is either the monitor or the card. Plug your monitor in another computer. If it works, is the card. Bad news then.

In ubuntu you can redo the video configuration by typing in a terminal:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

