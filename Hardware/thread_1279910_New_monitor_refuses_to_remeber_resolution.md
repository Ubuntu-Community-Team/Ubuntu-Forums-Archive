---
title: "New monitor refuses to remeber resolution"
date: 2009-10-01
forum: Hardware
---

### Post by ezekiel000 on 2009-10-01
I just got a new monitor a Samsung T220 and it's optimum resolution is 1680x1050 but everytime I log out or restart my computer the resolution is reset to 1400x1050. I've checked the xorg.conf file and it says:
Section "Screen"

# Removed Option "metamodes" "1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

Can anyone help me fix this?

I'm running Ubuntu 9.04 64bit, a nVidia 8200 card with the official nVidia drivers 180.44.

Also is there any widescreen resolutions for the boot screens it doesn't have to be 1680x1050 but something with a widescreen aspect ratio so that usplash doesn't look squashed?

---

