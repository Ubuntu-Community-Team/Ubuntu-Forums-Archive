---
title: "new monitor -&gt; no mpeg video"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by mikeh123 on 2005-10-14
Hey all,
wonder if anyone can help us out, experiencing a very weird problem where I cannot see video in totem.

After attaching a new LCD monitor to my Dell Inspiron 4100 Laptop through the standard connection, then setting up to recommended resolution through xorg etc, everything seems to work fine and looks great!

however, when i go to play video through totem, the video only appears on the laptop monitor, and not the new attached LCD monitor.  The totem window is just blank.

is there a setting somewhere i need to change to display video to the monitor ?   do i need to somehow disable the laptop screen output ?

cheers,
mike.


for interests sake, this problem was fixed with /etc/X11/xorg.conf file tweaking.   I wanted to create a setup whereby the laptop screen was off, with the external LCD on, and displaying video correctly.  Not sure exactly which line(s) in xorg.conf fixed it, but it was one of these:

under device:
Option "MonitorLayout" "NONE, AUTO"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "DesktopSetup" "Clone"
Option "OverlayOnCRTC2" "on"

---

