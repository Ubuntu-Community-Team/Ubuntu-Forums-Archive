---
title: "No Desktop Effects w/ KDE 4.1, compiz works ok?"
date: 2008-10-30
forum: General Help
---

### Post by mma8x on 2008-10-30
i admit that i'm not sure at this point what the difference is between beryl, compiz, kwin, etc at this point.  i upgraded to kde 4.1, and when i enable desktop effects, i get a black screen with my mouse on it.  the screen is responsive to mouse clicks (i can undo the damage by clicking where the enable/disable desktop effects taskbar widget should be).  lspci gives me:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```
if i go to a console and type "compiz", i get:
```
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

and the effects seem to work fine.  any suggestions?

---

