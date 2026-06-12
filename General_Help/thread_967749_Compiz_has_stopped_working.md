---
title: "Compiz has stopped working"
date: 2008-11-02
forum: General Help
---

### Post by matthedane on 2008-11-02
Hi

I can't enable desktop effects. I would appreciate if someone had a solution, but since compiz isn't essential I don't wont anyone to go through too much trouble solving this issue.

The strange thing is, that after the Intrepid installation compiz worked fine. It stopped working when I added another (dual) screen to my laptop, and still didn't work when I went back to the original laptop screen. I have of course tried reenabeling it using the "appearance preferences" settings.

When I type "compiz" in the terminal this is what I get:

```

Checking for Xgl: not present.  Detected PCI ID for VGA:  Checking for texture_from_pixmap: not present.  Trying again with indirect rendering: Checking for texture_from_pixmap: present.  Checking for non power of two support: present.  Checking for Composite extension: present.  Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed. Checking for Software Rasterizer: present.  Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

When I run compiz-check this is what I get:

[CODE]
mat@PINGU:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

[CODE/]

This output doesn't get me any closer to finding - and hopefully solving - the problem...

What do I do from here?

Matt

---

### Post by matthedane on 2008-11-02
I have found a solution. Apparently it is a problem with the xorg.conf file. In order to restore the original (installation) settings simply type


 sudo dpkg-reconfigure -phigh xserver-xorg


in the terminal

I still do not understand why this problem occurs, but now have a solution...


Matt

---

### Post by pcanderson on 2008-11-21
Wow.  I have this exact same problem.  I tried your solution, though, and its still not letting me activate the effects.

---

### Post by rcoconnell on 2008-12-16
This got compiz back working again for me.  I wish I knew what about running multiple monitors had borked it.

---

