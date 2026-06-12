---
title: "problem with compiz after upgrade from 0.74 to 0.76"
date: 2008-11-29
forum: General Help
---

### Post by sjpritch25 on 2008-11-29
I no longer can go do any other workspaces, i loose the composite manager.  Here is the following error i receive running compiz from the terminal

stefan@stefan-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

not sure what the issue is.   Thanks for any help.

---

### Post by binbash on 2008-11-29
I guess your edges at previos compiz is the problem

open gconf-editor (if not installed, install it)

go to  : (via gconf-editor )

/apps/compiz/plugins/scale/allscreens/options/initiate_edge

try to disable edges there (you have to play a little with there since i dont have gnome installed :) )

---

### Post by sjpritch25 on 2008-11-29
Thanks for your reply.  but i fixed it by re-installing the following from synaptic packet manager

compiz-bcop and compizcoinfig-backend-gconf

Everything is back to normal.  I have to say the sphere and cylinder are pretty cool

---

