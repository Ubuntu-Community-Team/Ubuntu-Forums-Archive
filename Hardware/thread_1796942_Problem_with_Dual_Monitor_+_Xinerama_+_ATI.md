---
title: "Problem with Dual Monitor + Xinerama + ATI"
date: 2011-07-04
forum: Hardware
---

### Post by seidler on 2011-07-04
Hi

I'm facing problems when using Xinerama with Ubuntu 11.04 64 bits (and 10.10, 10.04 and 9.10). The only version that Xinerama works was 9.04...When i activate the Xinerama, the X crashes after i login.

I'm using two differents video cards:
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]


xorg.conf:
```
Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 768 422
        Screen         "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection

Section "Monitor"
        Identifier   "0-CRT1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1360x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "1-DFP1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1360x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "left"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[2]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP1" "1-DFP1"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-CRT1" "0-CRT1"
        BusID       "PCI:1:5:0"
EndSection
Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[2]-0"
        Device     "amdcccle-Device[2]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

Anyone can help?

Thanks,
Seidler

---

