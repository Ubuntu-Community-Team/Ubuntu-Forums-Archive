---
title: "Skype and Webcams"
date: 2008-10-27
forum: General Help
---

### Post by josemaster2228 on 2008-10-27
hey guys I need help with this i and my father just upgraded to 8.10 and we have the latest version of skype. the problem is that when my father fires up his web cam it starts to have some weired colors like when you watch tv and someone pulls the cable out and you get static when he was on 8.04 it had no problems and worked like a charm i don't know if this is a skype problem but it would be good if someone knew how to fix it thanks

---

### Post by josemaster2228 on 2008-10-27
Bump!

---

### Post by spiderbatdad on 2008-10-27
having the same problem. I have filed a request for support with launchpad...skype video support was fine on 8.04...the device does not function on 8.10, though it is detected in the config utility.

---

### Post by spiderbatdad on 2008-10-27
You may be able to use some of the current workarounds as posted in this bug report...until the problem is fixed.
[https://bugs.launchpad.net/kopete/+bug/260918](https://bugs.launchpad.net/kopete/+bug/260918)

You can try to use the :```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
or
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
I would not try to remove libv4l-0 via synaptic and compile the newer version, as this would remove critical system apps from your desktop installation.
You can also try installing gspca-source via synaptic, depending on your cam, and using LD_PRELOAD again...Good Luck.
P.S. you could always use the 2.6.24 kernel and install intrepid packages.

---

