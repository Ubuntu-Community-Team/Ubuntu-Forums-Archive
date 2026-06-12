---
title: "Disable tap-to-click"
date: 2009-10-09
forum: Hardware
---

### Post by RubenTheGreat on 2009-10-09
I'm using Ubuntu Karmic UNR on an ASUS K50IN. No, it's not a netbook; I just prefer the interface to the ubuntu default.

After some searching I found various things to stop the tap to click, such as in the mouse option page, where I find no option to disable it, and editing the xorg.conf file. The things that people are told to edit simply do not exist in my xorg.conf file.

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```That is my entire xorg.conf file. I have tried gsynaptics, but that won't initialize. Naturally.

On a lighter note I am impressed with the out-of-the-box functionality of Karmic. My wireless worked for a change.

Suggestions and help would be greatly appreciated

---

### Post by the4thamigo_uk on 2009-11-07
Its simple. Open the System->Preferences->Mouse application. Select the Touchpad page and deselect 'Enable mouse clicks with touchpad'

---

