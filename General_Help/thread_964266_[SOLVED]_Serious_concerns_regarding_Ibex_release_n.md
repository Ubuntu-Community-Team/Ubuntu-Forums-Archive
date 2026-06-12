---
title: "[SOLVED] Serious concerns regarding Ibex release notes"
date: 2008-10-30
forum: General Help
---

### Post by kerryhall on 2008-10-30
Has anyone read the Ibex release notes yet?

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

I would like to draw attention to this issue:
==========
nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 
============

I find this to be a serious concern. I have several machines that use these video cards, and need 3d acceleration for them. Of course the problem is not on Ubuntu's end, but rather X.org's end. I have been acquiring old hardware in order to build complete systems that I can simply give to people who need a computer. This is definitely a roadblock and seems to go against what I thought was or what seemed to be part of the philosophy of Linux: reviving old hardware and keeping it usable through new versions.

I will not be upgrading those machines to Ibex.

So there seems to be two possibilities here:

1. X.org enables support for nVidia's legacy driver in a future version.
2. nv driver has 3d acceleration coded into it.

At any rate, this seems to be a horrible development. Will I be able to upgrade to a future version of Ubuntu (and thus the newer versions of X.org) with those machines ever again? Opinions?

edit:
Is this a problem on nVidia's end? Why would the new version of X.org break compatibility with the legacy driver? Mod, please move this thread if it's in the wrong place.

---

### Post by lfaraone on 2008-10-30
I'm not too sure, you might want to bug the guys at xorg about that (or search their tracker, someone's prolly complained already).

---

### Post by GuitarRocker2562 on 2008-10-30
I think it is a lack of nVidia's support for the new kernel with their old hardware.

---

