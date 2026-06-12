---
title: "How do I install ati drivers on Ubuntu 9.10?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by ROUBOS on 2009-11-02
Hi,
I just downloaded the ATI drivers from the official site and the installation failed.

under System>Administration>Hardware Drives, my ATI x1950 pro AGP card is not listed.

I also notice that there is no /etc/X11/xorg.conf file.

Looking for a way to install the drivers for ubuntu 9.10 and I cannot.

Are there issues with ATI cards and Ubuntu 9.10?

I had it all working fine on ubuntu 8.10

---

### Post by antiram on 2009-11-02
fglrx has no longer support for R500 and lower. Use opensource driver instead
[http://ubuntuforums.org/showthread.php?p=8221775#post8221775](http://ubuntuforums.org/showthread.php?p=8221775#post8221775)

---

### Post by Niels R on 2009-11-02
Perhaps you could try this in the terminal "sudo ./ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic", this worked for me.

---

### Post by ghostborg on 2009-11-02
Did you use remember to use sudo ? I forgot.
I downloaded from the ATI site and followed their installation instructions.
I have an ATI HD3200 integrated.
Everything seems to work so far.

---

### Post by antiram on 2009-11-02
fglrx for R600 and newer is in repository. package "xorg-driver-fglrx"
or click System->Administration->Hardware driver to install

open source driver works also, but only 2D for R600 and newer

---

### Post by ROUBOS on 2009-11-02
well I just forgot all about it... went back to Debian.
Debian Lenny is awesome. Very stable. Have been using it since it came out. Thought to give Ubuntu 9.10 a look but no.. back to Debian.
Was using Ubuntu for a long time, up to version 8.10. 
Looks likes I'm not going to bother with any other distro anymore.
Debian might not have the latest packages, but it's bug free...

thanks for the help

---

### Post by ghostborg on 2009-11-03
Once you get used to something its hard to change.

---

