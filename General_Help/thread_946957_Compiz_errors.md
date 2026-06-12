---
title: "Compiz errors"
date: 2008-10-13
forum: General Help
---

### Post by rehaby on 2008-10-13
i ran compiz in terminal and got this output.is it normal

```
ben@ben-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

---

### Post by tuxxy on 2008-10-13
Whats your video card

---

### Post by rehaby on 2008-10-14
its a Radeon Xpress 1100 IGP i think

---

