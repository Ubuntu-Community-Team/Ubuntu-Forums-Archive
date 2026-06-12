---
title: "small screen size when using nvidia driver"
date: 2005-01-28
forum: Hardware &amp; Laptops
---

### Post by BigCdaAnswer3 on 2005-01-28
Hey everyone, I'm still pretty new at Ubuntu and I am very happy I can get 3d support at all for my nvidia card. The thing is, I have a brand new laptop with a GeForce 440 Go Nvidia card for graphics. The standard "nv" driver worked perfectly, but whenever I used apt-get to get the "nvidia" driver and put that in my xorg.conf file, It works, but the screen shows up on the left hand side at about 1024x768 (my screen size is actually 1200x800) and it is filled with black space on the right. I really don't think I'm doing anything wrong in the config file but if someone could just check it out I would appreciate it. I think it's just a problem with the driver.

I attached two screenshots to give a visual of what I am talking about.

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/Speedo"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
# Load "GLcore"
Load "bitmap"
Load "dbe"
Load "ddc"
# Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "speedo"
Load "type1"
Load "v4l"
Load "vbe"
Load "xtt"
Load "synaptics"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xfree86"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1700"
Option "RightEdge" "5300"
Option "TopEdge" "1700"
Option "BottomEdge" "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.06"
Option "MaxSpeed" "0.12"
Option "AccelFactor" "0.0010"
Option "SHMConfig" "on"
# Option "Repeater" "/dev/ps2mouse"
EndSection

#Section "InputDevice"
# Identifier "Synaptics Touchpad"
# Driver "synaptics"
# Option "SendCoreEvents" "true"
# Option "Device" "/dev/psaux"
# Option "Protocol" "auto-dev"
#EndSection

Section "Device"
Identifier "NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "NvAGP" "1"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28-64
VertRefresh 43-60
Option "DPMS"
# Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
Modeline "1280x800_60.00" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
# Depth 1
# Modes "1280x800"
Modes "1280x960"
EndSubSection
SubSection "Display"
Depth 4
# Modes "1280x800"
Modes "1280x960"
EndSubSection
SubSection "Display"
Depth 8
# Modes "1280x800"
Modes "1280x960"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960"
# Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960"
# Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
# Modes "1280x800"
Modes "1280x960"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

#Section "DRI"
# Mode 0666
#EndSection

---

### Post by BigCdaAnswer3 on 2005-01-28
I'm running the 2.6.10-2 kernel with hoary if this helps at all

---

### Post by ba747heavy on 2005-01-28
A suggestion that might or might not work, in your screen section try changing Modes "1280x960" to Modes "1280x800_60.00"

---

### Post by BigCdaAnswer3 on 2005-01-28
hey its worth a shot, gimme a sec to reboot and i'll let you know!

---

### Post by BigCdaAnswer3 on 2005-01-28
nope no luck...i really don't know if there is anything else i can try  :-(

---

