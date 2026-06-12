---
title: "Yet another &quot;Can't enable effects&quot;"
date: 2008-07-17
forum: General Help
---

### Post by Lecrow on 2008-07-17
So, I just installed Hardy for the first time, and don't have much of a clue as to what i'm doing. 

Of course, the problem is that when I go to enable visual effects I get the error "Desktop effects cannot be enabled."

After running compiz-check, I get the output

> ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Before it told me that my card wasn't necessarily whitelisted, but I think I turned that off somehow.

Any ideas? Or is compiz just a pipe-dream for me?

---

### Post by Morty007 on 2008-07-18
Can you give us more details on your system? (RAM, processor, video card, etc. )

---

### Post by Lecrow on 2008-07-18
Computer:
Processor: Intel Pentium 4 CPU 2.80GHz
Memory: 970MB
OS: Ubuntu 8.04.1
Display:
Resolution 1280x1024 pixels
OpenGL Renderer: Mesa GLX indirect 1.4
X11 Vendor: The X.Org Foundation
Multimedia:
Audio Adapter: ICH - SIS SI7012
Graphics info:
Silicon Integratedystems [SiS] 65x/M650/74- PCI/AGP

---

### Post by overdrank on 2008-07-18
> **Lecrow said:**
> Computer:
Processor: Intel Pentium 4 CPU 2.80GHz
Memory: 970MB
OS: Ubuntu 8.04.1
Display:
Resolution 1280x1024 pixels
OpenGL Renderer: Mesa GLX indirect 1.4
X11 Vendor: The X.Org Foundation
Multimedia:
Audio Adapter: ICH - SIS SI7012
Graphics info:
Silicon Integratedystems [SiS] 65x/M650/74- PCI/AGP

HI and if you look through this thread you can see that SIS chipsets are not well supported
[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)

---

