---
title: "Changing Screen Resolution in KDE"
date: 2008-10-18
forum: General Help
---

### Post by h3llh0l3 on 2008-10-18
Hello all,

Just installed ubuntu 8.04 with KDE. My screen resolution is set to 1280x1024 and I would like to reduce it a bit. I am unable to figure out how to modify the xorg.conf. This is how my xorg.conf looks like:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Could someone please tell me what needs to be modified in here to change the screen resolution.
Thanks

---

### Post by overdrank on 2008-10-18
Hi and have you tried using the command ```
kdesu displayconfig-gtk
```
I believe is the command for KDE

---

