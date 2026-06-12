---
title: "Stoping Hardware acceleration for video card"
date: 2016-07-06
forum: Hardware
---

### Post by rkendron2 on 2016-07-06
I have an older machine (Intel x3000) video card that is giving sporadic reboots every time hardware acceleration kick in.  At least that is the way it seems.  I would like to turn off "direct rendering" which it appears Ubuntu 14.04 has turned on by default.  Any help hear?

---

### Post by Frogs Hair on 2016-07-06
Hello and Welcome

Post the output of the following.```
echo $XDG_CURRENT_DESKTOP
``` If it is unity you could reduce the graphics load by installing gnome-session-flashback and selecting the metacity session during login. Keep in mind that Chromium based web-browsers often have a setting to enable hardware acceleration when needed.

---

