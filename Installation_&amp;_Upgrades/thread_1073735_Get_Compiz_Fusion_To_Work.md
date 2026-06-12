---
title: "Get Compiz Fusion To Work"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by latheesan on 2009-02-18
Hello,

I am trying to get Compiz Fusion working on my latest ubuntu. So, I downloaded Envy and then had nVidia drivers installed.

Then I followed this guide [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) and i got the following error:

> latheesan@Desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault


I thought there was something wrong with my compiz installation or the nVidia graphic card/driver it self, so i found [this]("http://forlong.blogage.de/entries/pages/Compiz-Check") and tried the compiz-check my self. This is the result:

> latheesan@Desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GTS 512 (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

So... where did i go wrong here? Any idea how i can get compiz fusion on my ubuntu?

---

