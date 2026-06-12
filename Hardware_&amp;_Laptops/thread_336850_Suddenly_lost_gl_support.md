---
title: "Suddenly lost gl support"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by rejser on 2007-01-12
Yesterday when booting my computer I found myself at my desktop with a 600x800 resolution, not being to found of this I checked out my xorg.conf to see what had happened, and it looked really strange. So strange that I did not even know where to start, so I did a dpkg-reconfigure xserver-xorg (you know that I mean) to get up and running quick.
Did it, activated my nvidia driver, restarted x-server, and 600x800.. 
the xorg.conf looked strange once again, dpkg-reconf...... (also reinstalled nvidia-driver for safety)
Up and running, now stable, with the nvidia driver, but no gl. (work a little blender among other things).
glxinfo | grep direct gives me
```

Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".

```

Don't know where to start, havn't installed anything new, updated or anything.

Tried with disabling composite just for the sake of it, did not work

Found the envy script usefull, everything works correct now.

Still have no idea what happened to begin with though....

---

### Post by super_psycko on 2007-01-18
how did you solve it?? i have the same problem..

---

