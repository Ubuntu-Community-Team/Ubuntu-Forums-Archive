---
title: "Visial Effects stopped working, after recent upgrade"
date: 2008-09-13
forum: General Help
---

### Post by sarmadzhiev on 2008-09-13
Hi, 

I had compiz that worked just before my recent upgrade. Then it stopped with the compiz --replace giving the follow:

 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
present. 
Checking for Xgl: not present. 
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


I have Intel 
VGA compatible controller: Intel Corporation 82865G Integrated Graphics 

Thx
Nikolay

---

### Post by sarmadzhiev on 2008-09-13
When running glxgear I am getting this as well:

libGL error: drmMap of framebuffer failed

Thx
Nikolay

---

### Post by sarmadzhiev on 2008-09-13
I have changed the Xorg.conf driver to i810 and now the compiz is working again, 

any ideas what is wrong?

---

### Post by cyclobs on 2008-09-14
my idea was that it was having troubles finding the display device

---

