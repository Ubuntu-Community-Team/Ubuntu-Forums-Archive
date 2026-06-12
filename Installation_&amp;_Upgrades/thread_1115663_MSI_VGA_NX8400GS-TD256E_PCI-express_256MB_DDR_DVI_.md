---
title: "MSI VGA NX8400GS-TD256E PCI-express 256MB DDR DVI TVO"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by copycat on 2009-04-04
Hi,

shorthly after my old card gave up I bought this one.
After installing the drivers it only runs in low graphic mode.
(Mythbuntu 8.10)

Can someone help me with my xorg.conf? I'm not very good in it.
It seems to be that it can not find the right monitor settings. (It's S-VHS to TV) Pls. advise!

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

---

