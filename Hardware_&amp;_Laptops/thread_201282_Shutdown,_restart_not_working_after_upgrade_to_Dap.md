---
title: "Shutdown, restart not working after upgrade to Dapper"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by hillsh on 2006-06-21
I recently upgraded to Dapper - running Athlon 64.  Shutdown and restart used to work fine before the upgrade but now are not working.  Seems like the X window is not shutting down properly - screen goes dark, the "theme song" plays briefly, short pause, then plays briefly again, then screen just stays dark.  Previously the window closed, and various terminal messages were displayed.

Does anyone have any idea how to fix this?

---

### Post by rowanparker on 2006-06-21
Sounds like video drivers (correct me if i'm wrong).
Which ones did you have installed?

Rowan.

---

### Post by hillsh on 2006-06-22
fglrx, ATI Radeon card

---

### Post by rowanparker on 2006-06-22
I had problems with my video drivers when upgrading to dapper (I have ATI as well).
Try doing ```
dpkg-reconfigure xserver-xorg
``` as root, either from recovery mode or some other way. Choose the driver you used before fglrx.

It might work, hope it does.

Rowan.

---

