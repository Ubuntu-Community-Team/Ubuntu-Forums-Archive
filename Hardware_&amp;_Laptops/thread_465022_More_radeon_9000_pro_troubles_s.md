---
title: "More radeon 9000 pro troubles :s"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Boris-- on 2007-06-05
Okay, so fglrx did't work. I found it that there are other drivers that can give me 3d acceleration. I used this guide (guide for using the 'radeon' driver): [https://help.ubuntu.com/community/Ra...d8667c8e0949c9](https://help.ubuntu.com/community/Ra...d8667c8e0949c9)
to install my new driver. Now the xserver crashes again and says there's no screens found.

//
Output:

(WW) RADEON: No matching Device section for instance (BusID PCI 1:0:1) found
(**) RADEON(0): PreInit
(EE) RADEON(0): No valid modes found
(**)RADEON(0): FreeScreens
(EE)Screens found, but none have an useable configuration.

Fatal server error:
no screens found
//

The interesting thing is, that radeon in my xorg.conf is on PCI 1:0:0. So what's messed up here? I did mess with the drivers alot, so i guess something else than xorg.conf is screwed up. I hope somebody can help.

---

### Post by trippinnik on 2007-06-05
Try this howto [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746) It's not your exact model, but it worked for me.  In many ways it's better to have an older model ATI card, the opensource drivers are pretty good.

---

