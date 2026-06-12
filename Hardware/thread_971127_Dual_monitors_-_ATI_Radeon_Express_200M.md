---
title: "Dual monitors - ATI Radeon Express 200M"
date: 2008-11-04
forum: Hardware
---

### Post by pmsumner on 2008-11-04
Hi, first I apologise for posting a question which I know has been posted before but I've searched and tried this for a while with no joy.

I'm trying to get a bog-standard 1024x768 external monitor working on my Fujitsu Siemens Li1718 alongside the inbuilt LCD.  On boot, everything is duplicated on the VGA output, so I know the card can do it.  In the past I have managed to get the output mirrored to the display but haven't yet managed to get a completely separate display on it.

I'm running Intrepid and have tried the "Just get rid of xorg.conf and restart X" thing, but I get no output at all on the monitor.

> phil@home-laptop:~$ sudo aticonfig --enable-monitor=lvds,crt1
ati_dm: FGLRX_EnableDisplays failed when try to enable display: 3.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0

phil@home-laptop:~$ sudo aticonfig --query-monitor
  Connected monitors: none
  Enabled monitors: none

phil@home-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

Basically all this is telling me that it doesn't think there is a second monitor connected yet it darned well knows there is on boot... can you help?

---

### Post by jazzyjoe on 2008-11-04
Are you using the restricted drivers? I have a ATI x300 on my toshiba laptop and found that i get extended desktop working perfectly if I disable the restricted ati drivers. However, I can't run compiz anymore which is alright with me. I'm still trying to get AWM to work though.

Hope this helps.

---

### Post by pmsumner on 2008-11-05
I'm using fglrx as I believe that's the only sane way to play Warcraft in Wine.  I'll give the OSS drivers a shot and see if they work any better...

---

