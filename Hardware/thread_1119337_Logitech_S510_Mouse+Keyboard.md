---
title: "Logitech S510 Mouse+Keyboard"
date: 2009-04-07
forum: Hardware
---

### Post by Lucky75 on 2009-04-07
Hi.


I've been trying to get my tilt wheel working on my S510 mouse, but I'm unsure of how to do it. I've looked around, but there doesn't seem to be anything specifically for the S510 mouse with the tilt wheel. Everyone keeps saying that you need to find someone with the same mouse and see what they did, but I can't ;)

Would someone be able to tell me what I need to do to get it working? 

Thanks!


xorg.conf: 

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Option          "AddARGBGLXVisuals"     "True"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
EndSection


Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Screen  0
        BusID   "PCI:1:0:0"
EndSection

```

---

### Post by Lucky75 on 2009-04-13
Anyone?

---

### Post by Dr Mac 24 on 2009-06-13
I have a S510 but can't get the keypad to work. Even using the Keyboard Preference setup can't get it to work. ANy suggestions?

---

