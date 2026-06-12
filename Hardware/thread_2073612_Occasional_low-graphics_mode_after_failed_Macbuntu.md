---
title: "Occasional low-graphics mode after failed Macbuntu install"
date: 2012-10-20
forum: Hardware
---

### Post by BARupert92 on 2012-10-20
I have a dell-inspiron n5110 and I just upgraded to Ubuntu 12.10, I tried to install Macbuntu 10.10, previously I had gnome-fallback installed. The installation didn't completely work or seemed to be done, I logged out and back on and all was fine, and I uninstalled Macbuntu. Now occasionally I can log on perfectly ubuntu with full graphics (with an occasional system problem detected), but just as often, sometimes after having the successful login screen, I am forced into low-graphics mode, can't use mouse or anything, and am told I'll have to configure the graphics. 

I would like to know how to fix this problem so that I no longer am forced into low-graphics mode ever. This is kind of urgent, I appreciate any help.

---

### Post by 2F4U on 2012-10-20
What graphics drivers are you using? Is there maybe anything left from MacBuntu 10.10, which is, as far as I know, not designed to be run on 12.10?

---

### Post by moTaro on 2012-12-30
> **BARupert92 said:**
> I have a dell-inspiron n5110 and I just upgraded to Ubuntu 12.10, I tried to install Macbuntu 10.10, previously I had gnome-fallback installed. The installation didn't completely work or seemed to be done, I logged out and back on and all was fine, and I uninstalled Macbuntu. Now occasionally I can log on perfectly ubuntu with full graphics (with an occasional system problem detected), but just as often, sometimes after having the successful login screen, I am forced into low-graphics mode, can't use mouse or anything, and am told I'll have to configure the graphics. 

I would like to know how to fix this problem so that I no longer am forced into low-graphics mode ever. This is kind of urgent, I appreciate any help.

I am experiencing the exact same thing on my Dell Inspirion 5110 and Ubuntu 12.10. Please advise, have you found a solution to this problem already.

Thank you

---

### Post by fraktalek on 2013-01-12
Same problem here. Ubuntu 12.10 ThinkPad T420 without NVidia optimus, i.e. only Intel HD graphics. 

In Xorg.log I see

```
[     4.852] (II) VESA: driver for VESA chipsets: vesa
[     4.852] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.852] (II) FBDEV: driver for framebuffer: fbdev
[     4.852] (++) using VT number 7

[     4.852] (II) intel(0): using device path '/dev/dri/card0'
[     4.852] (WW) Falling back to old probe method for vesa
[     4.852] (WW) Falling back to old probe method for modesetting
[     4.852] (WW) Falling back to old probe method for fbdev
[     4.852] (II) Loading sub module "fbdevhw"
[     4.852] (II) LoadModule: "fbdevhw"
[     4.852] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.852] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.852] 	compiled for 1.13.0, module version = 0.0.2
[     4.852] 	ABI class: X.Org Video Driver, version 13.0
[     4.907] (EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
[     4.907] (EE) intel(0): Failed to become DRM master.
[     4.908] (II) UnloadModule: "intel"
[     4.908] (EE) Screen(s) found, but none have a usable configuration.

```

Then in Xorg.failsafe.log I see:
```

5.613] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

```

---

### Post by fraktalek on 2013-01-12
Hmm, there's another thread about this problem: [http://ubuntuforums.org/showthread.php?t=2073483](http://ubuntuforums.org/showthread.php?t=2073483)

it seems like the solution might be:

```

sudo apt-get install gdm

```

or if you already have gdm installed:

```

sudo dpkg-reconfigure gdm

```

---

