---
title: "Problems with Intel GMA 4500M"
date: 2018-09-03
forum: Hardware
---

### Post by seb.r on 2018-09-03
Fresh install of lubuntu 16.04.5 i386 desktop shows the following problem on a system with Intel GMA 4500M onboard chipset graphics adapter: after the boot process finishes the login screen is displayed normally and the mouse pointer moved to the left side of the screen, not in the center like normally. After I login the desktop is displayed with the icons but the taskbar is missing.
How to fix this?

EDIT: If i boot with the kernel parameter *nomodeset *or *i915.modeset=0 *the taskbar is back but any graphics acceleration is missing (as expected), so even watching a simple video on youtube becomes nearly impossible.

---

### Post by mörgæs on 2018-09-04
How does a fresh install of 18.04.1 work?

---

### Post by Yellow Pasque on 2018-09-05
I would try switching back to the old intel X driver. 
(L)ubuntu 16.04.5 is probably using the generic modesetting/glamor X driver since it comes with the kernel and Xserver found in Ubuntu 18.04.

(If you don't like vim, use whatever text editor you like)
```
sudo vim /etc/X11/xorg.conf.d/20-intel.conf
```

Copy/Paste:
```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
EndSection
```

Save. Quit. Reboot without i915.modeset=0

---

