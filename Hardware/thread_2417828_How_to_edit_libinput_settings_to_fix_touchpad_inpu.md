---
title: "How to edit libinput settings to fix touchpad input"
date: 2019-04-27
forum: Hardware
---

### Post by yoshiki2 on 2019-04-27
Hello, I am trying to fix my touchpad settings  
libinput:name:*CyPS/2 Cypress Trackpad:dmi:*svnDell:*pnXPSL322X*
 LIBINPUT_ATTR_PRESSURE_RANGE=105:60
 LIBINPUT_ATTR_PALM_PRESSURE_THRESHOLD=230
I am supposed to edit file 
/sys/class/dmi/id/modalias and adjust the dmi bit accordingly, make sure the svn and pn bits match.
But[SIZE=3] this is a virtual file? 
Any ideas how to do this?
Thanks

[https://bugs.freedesktop.org/show_bug.cgi?id=104990#](https://bugs.freedesktop.org/show_bug.cgi?id=104990#)[/SIZE]

---

### Post by Frogs Hair on 2019-04-27
Closed duplicate post.

---

