---
title: "Some troubles with newer ATI cards"
date: 2008-11-18
forum: Hardware
---

### Post by houn2000 on 2008-11-18
Just thought I would post some of the things i've learned during my two week battle with the proprietary ATI video drivers.

The first install of Intrepid, and the drivers installed without a hitch.  Too bad this trend didn't continue.

1. After reinstall, fgl_glxgears seg faults.

I checked the visual effects settings and noticed that none of the check boxes were highlighted.  So I checked none, and presto, the driver seems to be working.

2. With visual effects enabled, the gnome-terminal report the wrong version of opengl.

After getting the driver to work, I re-enabled visual effects, and running fglrxinfognome-terminal reports:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 1.4 (2.1.8087 Release)

And xterm reports:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release

Also, fglrx_glxgears seg faults in gnome-terminal but works perfectly in xterm.  This seems like a gnome/compiz issue.

If I come across anything else strange I will try to remember to post it here and hopefully save someone else the headache.  If anyone knows how to get around this, any response would be welcome!

---

