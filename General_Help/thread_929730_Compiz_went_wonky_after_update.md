---
title: "Compiz went wonky after update"
date: 2008-09-25
forum: General Help
---

### Post by lardandweed on 2008-09-25
Hi all.

Compiz failed today after i did a system update. i did "compiz --replace" and it seems to work fine now ... tried some stuff like rotate cube, scale and expo. works just like before.

thing is, the log gives me this...
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Is everything good or do i need to do something about it?

---

