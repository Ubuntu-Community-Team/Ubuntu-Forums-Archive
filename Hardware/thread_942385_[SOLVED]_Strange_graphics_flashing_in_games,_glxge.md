---
title: "[SOLVED] Strange graphics flashing in games, glxgears"
date: 2008-10-09
forum: Hardware
---

### Post by andyjones_au on 2008-10-09
Hey there guys,

I have this really strange "flashing" problem that appears when I play games with 3d graphics (like supertuxkart, tremulous) and when I type "glxgears" into a terminal, I see it again.

Have you ever filmed a television screen and seen that interference pattern that looks like big stripes going downwards?  It looks like that.

My graphics card is a ATI radeon HD3470, and I'm using Ubuntu 8.04.

Thanks guys!!
Andy

---

### Post by andyjones_au on 2008-10-11
*bump* nobody?

**edit:** Okay I found the solution.  I have to turn off desktop effects, and the flashing stops.

---

### Post by mickster019 on 2009-02-15
Had same problem. First one I've found that actually works

---

### Post by perixx on 2009-02-15
Hi andijones,

look over here, we've been having the same problem, it's an incompatibility of X server (DRI) and Ati drivers (though Nvidia has problems too):
[http://ubuntuforums.org/showthread.php?t=895182](http://ubuntuforums.org/showthread.php?t=895182)

This way, you can keep all your desktop effects and temporarily switch to another window manager, xfwm4 in this case, for troubled OpenGL apps. 

For how to install the latest Ati 9.1 driver, look here:
[http://ubuntuforums.org/showthread.php?t=1031811](http://ubuntuforums.org/showthread.php?t=1031811)


perixx

---

