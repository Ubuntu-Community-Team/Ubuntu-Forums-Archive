---
title: "Need help with xorg.conf"
date: 2008-06-15
forum: Hardware
---

### Post by k420 on 2008-06-15
just got a new tv a vizio 37" and am using it as a monitor but i want to use the native resolution of the monitor which is *1366x768 60hz
this is what vizio says it will do 
Resolution Refresh (Hz) H.Freq (kHz) V.Freq (Hz) H.Sync V.Sync Pixel Freq (MHz)
640x480 60 31.5 59.94 N N 25.175
640x480 75 37.5 75.00 N N 31.500
720x400 70 31.46 70.08 N P 28.320
800x600 60 37.9 60.317 P P 40.000
800x600 75 46.9 75 P P 49.500
800x600 85 53.7 85.06 P P 56.250
1024x768 60 48.4 60.01 N N 65.000
1024x768 75 60.0 75.03 P P 78.750
*1366x768 60 47.7 60.00 P N 85.500
NOTES: N = Negative, P = Positive, * = Primary (Native) Mode

and this is what my xorg.conf is 
> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection



---

### Post by overdrank on 2008-06-15
HI and have you tried the nvidia settings ```
gksu displayconfig-gtk
```

---

### Post by k420 on 2008-06-15
yeah this doesnt show the correct resolution or refresh rate.  only goes up to 1024x768

---

### Post by overdrank on 2008-06-15
> **k420 said:**
> yeah this doesnt show the correct resolution or refresh rate.  only goes up to 1024x768

Ok you may have to edit your xorg by hand and add it. This is a example of my system with dual monitors
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by k420 on 2008-06-15
what would i do if i wanted to only use one monitor(vizio 37") and make the screensize correct 1366x768 60hz

---

