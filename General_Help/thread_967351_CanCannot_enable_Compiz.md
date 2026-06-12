---
title: "Can/Cannot enable Compiz"
date: 2008-11-01
forum: General Help
---

### Post by eitreach on 2008-11-01
I can't seem to enable Compiz without fusion-icon in Intrepid, and even with that, it only works the second time. This is constant with no change.

Strange thing is, it appears to be running, but only with shadows. When I try to enable Compiz in this state via Visual effects, it fails. 

But, when I try to run it without any window manager running, Compiz is enabled instantly, all enabled effects.

I have an Nvidia Geforce 8600GT, that have always worked. 

Output from compiz --replace (with window manager):

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

And compiz --replace (without window manager)

hecking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


What do I do to fix it?

---

### Post by ad_267 on 2008-11-02
Do you have compositing in metacity enabled? That can cause this problem. You can check by pressing Alt+F2 and running gconf-editor and browsing to apps - metacity - general and unchecking "compositing_manager"

---

### Post by eitreach on 2008-11-02
Spot on. Worked perfectly after disabling metacity compositing.  

My sincere thanks.

---

### Post by ad_267 on 2008-11-02
There a bug here if you want to keep up to date with this issue:
[https://bugs.launchpad.net/metacity/+bug/178953](https://bugs.launchpad.net/metacity/+bug/178953)

This seems to be the same thing but hasn't been marked as a duplicate:
[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/231904](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/231904)

---

