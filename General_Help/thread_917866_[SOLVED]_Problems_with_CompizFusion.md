---
title: "[SOLVED] Problems with CompizFusion"
date: 2008-09-12
forum: General Help
---

### Post by mcfroger3 on 2008-09-12
Ok so i followed the directions on this site 
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

And when i get to the step

```
Run Compiz

To run Compiz for the current session, hold Alt, then press F2, then enter the following command, or for better trouble shooting, open up a Terminal window and use the following command.

compiz --replace


```

I get this error in the terminal
```

kyle@Spawnson:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.





```

Im running Ubuntu Hardy 8.04

---

### Post by Nepherte on 2008-09-12
Compiz Fusion is installed by default on Hardy so you shouldn't install compiz, cause it is installed already. You do have to install 3D drivers before compiz can work (system > administration > restricted hardware or install envyng-gtk)

---

### Post by tuxxy on 2008-09-12
Enable compiz at system > prefs > appearance > visual effects

---

### Post by mcfroger3 on 2008-09-12
Oh i didnt know, thanks.

---

