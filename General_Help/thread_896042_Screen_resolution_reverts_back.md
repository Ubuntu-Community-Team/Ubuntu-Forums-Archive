---
title: "Screen resolution reverts back"
date: 2008-08-20
forum: General Help
---

### Post by farmdve on 2008-08-20
When i turn off/restart pc i always have to adjust the resolution to 1024x768.
How do i make it permanent so i dont have to do that every time ubuntu loads?

---

### Post by cdtech on 2008-08-20
Be sure your desired resolution is the first in the list "/etc/X11/xorg.conf":
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      [COLOR="DarkRed"]**"1440x900"**[/COLOR] "1920x1440" "1920x1200" "1856x1392" "1680x1050"
    EndSubSection
EndSection
```

**Update::.**
Forgot to give the file to edit. lol
I have it listed above......

---

### Post by farmdve on 2008-08-20
Couldnt save the file cause i dont have permissions :(

---

### Post by cdtech on 2008-08-20
You have to use "sudo" an in "sudo gedit /etc/X11/xorg.conf"

---

### Post by farmdve on 2008-08-21
Okay i edited the file but no change :(

---

