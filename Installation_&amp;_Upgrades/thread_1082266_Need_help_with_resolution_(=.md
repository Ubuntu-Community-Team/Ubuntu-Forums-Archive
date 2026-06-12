---
title: "Need help with resolution (="
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by Doxe on 2009-02-27
ello (= i installed ubuntu 8.10 yesterday, its my first time using it.
I googled around alot to get everything to work (= anyway, i can't get my screen resolution to where i want it..

at the moment i use TwinView with 1152x864 on both screens
my main screen is a LG W2241S and my 2nd screen is a EIZO L550
My 2nd screen can use most resolutions, including 1280x1024 (wich i want to use on both screens)

on my main screen i can't choose that resolution, and i think that is coz i don't have drivers installed for it,
and i've been looking around for those, but i can't find any =( and those on the CD i got with my screen, i can't get those to install =/

i have also been trying out alot of ways to change the resolution by using the terminal. but without success

My graphic card is a EVGA GeForce 8800 GTS 512

and.. if its to any help: in my nvidia X server settings it says something about:
"Display Devices: EIZO L550 (CRT-1), CRT-0 (CRT-0)"
That looks a bit wierd to me, so i though i should mention it (=

---

### Post by khelben1979 on 2009-02-27
Attach this file: /etc/X11/xorg.conf to this thread so it'll be possible to see how it looks like.

[xorg.conf on Wiki]("http://en.wikipedia.org/wiki/Xorg.conf")..

---

### Post by kspncr on 2009-02-27
You can try [Envy]("http://albertomilone.com/nvidia_scripts1.html") to help install the driver and that should let you change the resolution to what you want.

---

### Post by Doxe on 2009-02-27
Okay, here is my /etc/X11/xorg.conf
its a bit edited, coz i've been trying things out.. but i think i have a backup of the original one.
um.. the [COLOR="Blue"]blue[/COLOR] text is things that i have added, so you know what's new and what was there since be4 ( ;

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
[COLOR="Blue"]    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"[/COLOR]
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
[COLOR="Blue"]    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection[/COLOR]

EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1152x864 +0+0, CRT-1: 1152x864 +1152+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

