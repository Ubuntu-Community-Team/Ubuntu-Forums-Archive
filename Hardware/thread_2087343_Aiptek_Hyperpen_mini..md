---
title: "Aiptek Hyperpen mini."
date: 2012-11-23
forum: Hardware
---

### Post by jaho22 on 2012-11-23
Does anyone have a working drawing tablet, Aiptek Hyperpen mini ?

It was a low priced table, 29 euros, it is working on win xp, now i want to use it with ubuntu, does anyone have any help or ideas, how to make it work on ubuntu ?

---

### Post by Favux on 2012-11-23
Hi jaho22,

What release of Ubuntu are you using?

These graphics tablets are often re-branded.  You need to run:
```
lsusb
```
in a terminal and post the output.  I believe it is a Waltop Q pad and should have 172F:0037 in the tablet line.

---

### Post by jaho22 on 2012-11-23
Thanks,

Here what i got with lsusb - Bus 002 Device 002: ID 172f:0037 Waltop International Corp.

It would be a super great thing to get it really working on ubuntu 12.04.

---

### Post by Favux on 2012-11-23
Alright it is the Q.  That model isn't supported until the 3.4 kernel:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  So Quantal.

But you can still get the tablet working in Precise.  What Nick has done is made backport patches for the older kernels and done some kernels too.  So you can add support doing that:
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches)
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages)

Unfortunately the HID drivers can't be loaded as separate modules due to some interdependence.  Nick is working on that with one of the HID section of the kernel maintainers, but I don't know where they are at.  Ubuntu instructions for applying the kernel patches are available here:  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

The final option would be to try the WizardPen driver:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)

---

