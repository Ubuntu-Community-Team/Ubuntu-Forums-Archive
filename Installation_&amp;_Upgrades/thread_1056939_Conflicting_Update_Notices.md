---
title: "Conflicting Update Notices"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by imag1narynumber on 2009-02-01
I'm running Ubuntu Studio (Intrepid). Running the apt-get update/upgrade deal on the command line, I'm notified that four packages are being held back.

linux-generic   linux-headers-generic   linux-image-generic   linux-restricted-modules-generic

However, the "update manager" shows the red exclamation point and lists eight packages to update

linux-generic (2KB)   linux-headers-2.6.27-11 (5MB)   linux-headers-2.6.27-11-generic (618KB)   linux-headers-generic (2KB)   linux-image-2.6.27-11-generic (22MB)   linux-image-generic (2KB)   linux-restricted-modules-2.6.27-11-generic (748KB)   linux-restricted-modules-generic (2KB)

I would normally trust the command line over the gui,but which is correct?  And can I get these two to agree again?  Thanks in advance!

---

### Post by lloyd_b on 2009-02-01
IIRC, some of those are "meta-packages", which simply point to other packages.  For instance:
```
linux-headers-generic -> linux-headers-2.6.27-11-generic -> linux-headers-2.6.27-11
```
I think the GUI is simply showing you a little more information regarding what's happening "under the hood" than the command line.  Regardless of which way you actually upgrade, you'll wind up installing the same stuff.

(BTW: you'll have to do a "sudo apt-get dist-upgrade" to get the command line to install those)

---

### Post by imag1narynumber on 2009-02-01
Excellent, thanks for the help and the quick reply!  I shall do so.

---

