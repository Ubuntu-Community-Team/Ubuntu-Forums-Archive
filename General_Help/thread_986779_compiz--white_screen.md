---
title: "compiz--white screen"
date: 2008-11-18
forum: General Help
---

### Post by thehellboy on 2008-11-18
when i enable compiz in my acer 5052 laptop screen becomes white.. and not returning back and i ve to restart it.. more over the resolution of login screen is low how to configure it..but desktop resolution is good.. please help me to solve these problems.. thx in advance

---

### Post by ciscophoneguy on 2008-11-19
This is what is on the CompizFusion website:

> White Screen

A white screen can be a symptom of different problems depending on your video card. For nVidia cards, it usually means that the nvidia driver is not enabled or operational.

This problem is characterised by a completely white screen where desktop effects (such as rotating the cube with <Ctrl><Alt>Left or <Ctrl><Alt>Left) continue to work, but no window contents are visible. It means that there is a bug with binding pixmaps to textures. This usually means that for whatever rendering method you are using, the GLX_EXT_texture_from_pixmap extension is broken. Please upgrade your driver, X server, and/or Xgl if you are using it. 

Here is the direct link:
> [http://wiki.compiz-fusion.org/Troubleshooting#head-2325ff64f5d986394639f6c077217b505a09d02f](http://wiki.compiz-fusion.org/Troubleshooting#head-2325ff64f5d986394639f6c077217b505a09d02f)

---

