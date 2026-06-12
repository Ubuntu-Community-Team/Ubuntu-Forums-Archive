---
title: "How to get 3D capabilities working?"
date: 2011-12-06
forum: Hardware
---

### Post by tjfitz on 2011-12-06
Hi, I have a Thinkpad T42 which uses an ATI gpu.
```
$ sudo lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```With the out-of-the-box drivers, my video performance is sluggish and I want to speed things up.

According to _[Guide to Laptop Video Cards and 3D Options]("http://www.guide-to-laptops.com/guides/laptop-video-3d.html")_, this gpu is DirectX9 capable.  It would be nice not only to get faster 2D performance, but to get the 3D abilities going, too.

Doing some searching, I discovered that fglrx is the binary driver for this, but when I installed it and rebooted, the cpu was running at 100% nonstop, the window manager was freaking out (i.e. the focus on the top window was flashing on and off making it impossible to use the terminal), and when I tried to get out of X with cntrl-alt-F1, it just paused a second and kicked me right back to X.  Fortunately I was able to uninstall it, and apparently no harm was done.

I remember what a pain it was to get NVidia drivers working on my desktop years ago, so I'm just going to ask what to do before I break something!

---

### Post by Toz on 2011-12-07
The RV350 is no longer supported by ATI ([http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")) and as such, the proprietary drivers won't work (as you can tell). You are basically stuck with using the opensource radeon drivers (see here for the feature support matrix: [http://www.x.org/wiki/RadeonFeature]("http://www.x.org/wiki/RadeonFeature"))

---

### Post by tjfitz on 2011-12-07
Thanks for the heads-up Toz. :sad:

On that features website, would my gpu fall under the "R300" column?

Is there a free implementation of 3D that would work for this gpu?

---

### Post by Mark Phelps on 2011-12-07
> **tjfitz said:**
> Is there a free implementation of 3D that would work for this gpu?

Not since Ubuntu 9.04 -- when ATI dropped support.

The open-source drivers do 3D, they just don't do hardware acceleration.

---

### Post by tjfitz on 2011-12-07
Thanks Mark. :(:( I just can't get a break...

---

