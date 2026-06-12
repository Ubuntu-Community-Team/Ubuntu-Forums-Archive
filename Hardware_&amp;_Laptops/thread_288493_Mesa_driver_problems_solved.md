---
title: "Mesa driver problems solved"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Nythain on 2006-10-29
This is for anyone having problems installing the ati drivers. More specifically getting the ati drivers instead of mesa and enabling that pesky direct rendering turned on.

There are many great guides out there for installing the drivers many different ways... i cant find the bookmark to the one i used the most so im just gonna say google it, or search the ubuntu/kubuntu forums and start from there.

Unfortunately none of them were very helpfull for getting the ati drivers instead of the mesa to run. Then i stumbled upon one out of like 50 xorg.conf examples that showed me ONE very vital thing...

Section "Device"
    Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
    Driver      "fglrx" <---- no one mentioned changing driver from "ati" or "radeon"  or whatever it might say to "fglrx" (such a simple solution in hindsight)
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"<----- not sure what your xorg.conf looks like, or if i really needed to change that twice, but better safe than sorry and it works
    Option        "VideoOverlay" "off"
    Option        "OpenGLOverlay" "on"
EndSection


try changing those drivers there from and rebooting, not sure if it works as well just reloading x or not, i always reboot so everything gets reset and all that jazz. Hope this helps at least ONE person who has had them pesky mesa blues lately.

now if only i can fix my cdrom problems i might keep this os long enough to enjoy it

---

