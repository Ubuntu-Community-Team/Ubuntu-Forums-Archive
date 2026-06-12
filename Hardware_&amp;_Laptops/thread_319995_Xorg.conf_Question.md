---
title: "Xorg.conf Question"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by ccerinojr on 2006-12-16
Does the logon screen use a different xorg.conf file then the gnome sessions? When I am presented with the login screen my monitors have a funky resolution and the screen spans across the two monitors instead of just cloning my primary display.

When I log into my gnome session my resolution changes to my set 1600x1200 and my secondary monitor clones my primary monitor. 

If it is of any help I have a ATI x850 xt and I am running edgy.

---

### Post by Dave54 on 2006-12-16
First, open terminal and type
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down until you find the "screen" section. Mine looks like this:
```
Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV34 [GeForce FX 5200]"
 Monitor  "A90f+"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection
```
Note where it says "DefaultDepth 24". That means we're interested in this part:
```
 SubSection "Display"
  Depth  24
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
```
Finally, under modes, move the screen resolution you like best to the front of the list. It will be used as your default screen resolution when you log in. However, I don't know if it will fix the stretching over two screens part.

Good luck.
-Dave

---

