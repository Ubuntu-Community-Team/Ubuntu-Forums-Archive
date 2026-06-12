---
title: "Dual monitor help... LCD TV only displays640x480"
date: 2008-11-21
forum: Hardware
---

### Post by rstellers on 2008-11-21
I have an NVIDIA geforce FX5200 running a Dell 21 inch LCD (works fine) and a second display which is my VIZIO 42" GV42L HDTV.  I can only get 640x480 on the TV which makes it in effect useless to me.  I am running the newest propriatery driver 173.14.12 and kubuntu 8.10.  Xconf is posted below.  Any help is appreciated as I am new and trying to learn.  Thanks!

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
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option          "UseEDID" "True"

EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
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
    BoardName      "GeForce FX 5200"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +640+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +520+0, DFP: nvidia-auto-select +0+868"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by SuperSonic4 on 2008-11-21
Have you tried using the nvidia settings?

In konsole typo sudo nvidia-settings or sudo su -c 'nvidia-settings'
whichever works :p

And then go from there?

If you don't have it install I recommend you install it ```
sudo apt-get nvidia-settings
```

---

### Post by rstellers on 2008-11-21
yeah.  It only lets me adjust the second monitor up to 640x480 at highest res..  In windows i get 1366x768... but then I have to use windows.  :(

---

