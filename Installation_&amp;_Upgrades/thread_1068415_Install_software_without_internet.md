---
title: "Install software without internet?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by HngGstr on 2009-02-12
Lets say, that I have software I want to install on my ubuntu machine, but I don't have internet configured yet (too lazy). I have the software on my usb. How can I install via usb?

---

### Post by lswb on 2009-02-13
If the software is in .deb packages it can be installed by double clicking on the icon, or from the command line use "dpkg -i packagename" or, "gdebi packagename" If the packages have dependencies that are alos on the USB drive gdebi will install them as well.

---

