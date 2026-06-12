---
title: "RAM not recognized"
date: 2010-09-11
forum: Hardware
---

### Post by AlbertCarlosEggs on 2010-09-11
Hi, I've a Toshiba Qosmio G45 notebook and Lucid Lynx 10.04.1 does not recognize 4 GBy RAM, only detects 3 GBy. How can I fix this mismatch? Should I modify any file? Thanks.

---

### Post by sikander3786 on 2010-09-11
You would have installed 32-bit Ubuntu. Maximum 3 GB RAM is allowed. You can get more that 3 GB RAM supported in 32-bit by using the PAE Kernel. Alternatively install 64-bit version.


[COLOR="DarkRed"]**EDIT:**[/COLOR]

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

It says "Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

If you need to enable PAE manually, follow the instructions for Karmic below."

Also see this one.

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by AlbertCarlosEggs on 2010-09-11
Hi, Thanks a lot! I used Synaptic Package Manager loading almost everything regarding "linux-*-server" and it works now! Lucid Lynx detects 3.9 GBy.

---

