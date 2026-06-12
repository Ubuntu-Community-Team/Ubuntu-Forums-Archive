---
title: "Nvidia TV out is black and white :("
date: 2009-01-09
forum: Hardware
---

### Post by jamin_melville on 2009-01-09
Hey I've got an NVidia Go 6150 graphics card in a compaq presario v3000 laptop. My issue is that the display on my TV appears black and white. It is not a cable issue because I use the same cable to plug into my DVD player and that has colour. Any suggestions? Thanks

---

### Post by ModelM on 2009-01-09
I think Australia uses the PAL television standard. Make sure the video output is set to PAL, not NTSC.

---

### Post by jamin_melville on 2009-01-09
Ok so I changed my the screen section of my xorg.conf file to:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option          "TVStandard" "PAL-G"
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, TV: nvidia-auto-select +128+16"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Picture on the TV is still black and white...

---

