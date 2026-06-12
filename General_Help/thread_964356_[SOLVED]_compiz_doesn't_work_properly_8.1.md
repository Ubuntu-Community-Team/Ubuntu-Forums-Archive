---
title: "[SOLVED] compiz doesn't work properly 8.1"
date: 2008-10-30
forum: General Help
---

### Post by zhenka11230 on 2008-10-30
hi : )

I am using ubuntu 8.1 
Ati x700 256mb 

Comiz works with some things like wobble effect but features such as cube does no start at all! ; (

someone please help!

---

### Post by LowSky on 2008-10-30
which ATI driver are you using?

---

### Post by zhenka11230 on 2008-10-30
How do i check?

---

### Post by zhenka11230 on 2008-10-30
P.S. this is what i get when i type compiz in the terminal:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by zhenka11230 on 2008-10-31
bump

---

### Post by zhenka11230 on 2008-10-31
Fixed it myself by following the advice here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/82957](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/82957)

changed the following settins in gconf-editor to:

/apps/compiz/general/screen0/options/hsize: 4

and

/apps/compiz/general/screen0/options/number_of_desktops: 1

works fine now! : )))

---

