---
title: "Low resolution on ATI Radeon HD 3200"
date: 2010-05-05
forum: Hardware
---

### Post by eyerouge on 2010-05-05
I use a *HP 6735b* notebook with a *ATI Radeon HD 3200* graphics card in it. For some reason I can't use the maximum resolution (1280x800) in Ubuntu (same problem in both Karmic & now Lucid). Instead I'm stuck with the resolution one step below, as shown in screenshot below.

Problem is the max resolution doesn't even show up as an option to begin with.

[[img]http://www.ubuntu-pics.de/thumb/57004/skrivbord_1_001_PdocgE.png[/img]](http://www.ubuntu-pics.de/bild/57004/skrivbord_1_001_PdocgE.png)

I also have latest Catalyst Control Center from AMD/Lucid installed, but the very same problem can be found in there.

---

### Post by fedetxf on 2010-05-05
Try booting the Lucid LiveCD or with a bootable usb pendrive. Lucid has introduced 2D and 3D support for that hardware. If you get the correct resolution there, you might want to consider completely uninstalling catalyst and using the "radeon" driver.
With the radeon driver you can edit the /etc/X11/xorg.conf file and supply the resolution you want, if supported. With catalyst I don't think it actually reads that file.

---

