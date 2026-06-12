---
title: "tv out flickering help!!!!!"
date: 2009-05-16
forum: Hardware
---

### Post by superalanliu on 2009-05-16
Ubuntu 9.04 or Dell Latitude D620

I try to tv out to a SD CRT tv, and the screen flickers to no end. How do I get it to update its refresh rate? Stupid Nvidia X-Server won't let me change the refresh rate and sets my CRT refresh rate to unknown. I think my TV resolution is 640x480. Help please.

Thanks in Advance.

# Removed Option "metamodes" "CRT: NULL, DFP: nvidia-auto-select +0+0; CRT: 640x480 +0+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 640x480_80 +0+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

I think thats the Xserver information for the thing, I might have copied the wrong file. My Screen is messed!

---

