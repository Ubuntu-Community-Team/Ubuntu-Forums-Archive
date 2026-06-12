---
title: "nvidia9600GT,ACER V203H cannot set to 1600x900"
date: 2009-07-16
forum: Hardware
---

### Post by halida on 2009-07-16
I'm using acer V203H,9600GT,VGA.
first time I use livecd install, It can support 1600x900,
after I install nvidia driver, It failed to 1024x768,
and livecd cannot support 1600x900 too,
I set the HorizSync and VertRefresh, followed by V203H manual,
and it still only support 1440x900 ,and cannot support 1600x900
here is the xorg.conf:

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Module"
Load "glx"
EndSection

Section "ServerFlags"
Option "DontZap" "True"
Option "Xinerama" "0"
EndSection

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "keyboard"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "CRT-1"
HorizSync 31.5 - 80.0
VertRefresh 56.0 - 75.0
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 9600 GT"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
Option "NoLogo" "True"
SubSection "Display"
Depth 24
Modes "nvidia-auto-select" "1600x900"
EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "1360x768 +0+0"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "1440x900_60 +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

---

