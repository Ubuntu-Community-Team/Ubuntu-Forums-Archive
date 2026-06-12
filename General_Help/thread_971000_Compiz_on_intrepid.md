---
title: "Compiz on intrepid"
date: 2008-11-04
forum: General Help
---

### Post by YSH on 2008-11-04
Hey,

since i've upgraded to intrepid i can't get compiz working on my computer anymore. I always used Xgl to get compiz running, but it can't be found in the repo anymore, so i'm guessing there is a reason that someone doesn't like it anymore.

Output of fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8087 Release
```
Output of compiz --replace
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
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

