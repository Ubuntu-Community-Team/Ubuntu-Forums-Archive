---
title: "hardy heron nvidia gets hot, fan on, drains battery"
date: 2008-04-29
forum: Hardware
---

### Post by vdbijl on 2008-04-29
Dear ubuntuists,

After my upgrade to the hardy heron, things are getting kinda hot here ;)

After some research it looks like my nvidia graphix card is the culprit, it keeps running on performance level 2 (powermizer tab in nvidia-settings). The temperature stays around 50C, but when I force my fans off, it quickly increases to 60C and higher.

I read on a forum that twinview might be the problem, this fixes the powermizer level apparently.

Any ideas how to proceed? Any other people out there with the same symptoms? Should I upgrade/downgrade the nvidia driver?

Some info:
nvidia glx driver: 169.12
laptop: Dell Latitude D620 with nvidia Quadro NVS 110M w 256 MB

snippet from xorg.conf
```
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "NoLogo" "True"
    Option         "NvAgp" "1"
    Option         "OnDemandVBlankInterrupts" "True"
    Option         "Coolbits" "1"
    Option         "HWcursor" "1"
    Option         "DPMS" "1"
    Option         "AllowGLXWithComposite" "True"
    Option         "DynamicTwinView" "True"
    Option         "NoFlip" "False"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+0"
```

---

### Post by TenPlus1 on 2008-04-29
It may help take some strain off your gfx card and reduce power, but try turnong ON vsync in your nvidia-settings for 3d performance...

---

### Post by vdbijl on 2008-04-29
Thanx TenPlus1. Yeah I forgot to mention that I have the sync to vblank on.

Especially setting the OnDemandVBlankInterrupts to true makes powertop very happy. However the gpu keeps on burning, although it now has less to do ;)

---

### Post by vdbijl on 2008-04-30
bump

/me getting frustrated ](*,)

Anywayz, all help appreciated

---

