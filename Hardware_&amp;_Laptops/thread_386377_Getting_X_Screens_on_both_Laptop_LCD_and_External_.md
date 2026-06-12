---
title: "Getting X Screens on both Laptop LCD and External Monitor"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by sciurus on 2007-03-16
I tried the following xorg.conf configuration in Ubuntu 6.10 to get video both on my Powerbook's internal LCD and on a InFocus LP530-A projector connected to the DVI port. What I expected with this configuration was to get two independent screens; I was then going to try merging them with Xinerama. If I comment the "Dual Layout", uncomment the "Single Layout", and then start X my laptop display is fine. However, when I started X (using startx from single user mode or restarting gdm at runlevel 5) using the settings below, my laptop's display went blank, and I couldn't switch to
any virtual consoles. Nothing appeared on the projector either, but it did say that it was receiving a 1024x768@85 signal. There wasn't another computer around for me to try ssh from, so I did a hard shutdown. I didn't start X on the next boot before grabbing its log, but the log mentions "Single Layout" which makes me think that something failed so badly that X didn't get to log anything.

Any thoughts on settings I need to change or other things I might be
doing wrong?

EDIT: Feel free to move this thread if you feel it better fits another category.

[PHP]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
   FontPath    "/usr/share/X11/fonts/misc"
   FontPath    "/usr/share/X11/fonts/cyrillic"
   FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
   FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
   FontPath    "/usr/share/X11/fonts/Type1"
   FontPath    "/usr/share/X11/fonts/100dpi"
   FontPath    "/usr/share/X11/fonts/75dpi"
   FontPath    "/usr/share/fonts/X11/misc"
   # path to defoma fonts
   FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
   Load    "i2c"
   Load    "bitmap"
   Load    "ddc"
   Load    "dri"
   Load    "extmod"
   Load    "freetype"
   Load    "glx"
   Load    "int10"
   Load    "type1"
   Load    "vbe"
EndSection

Section "InputDevice"
   Identifier    "Generic Keyboard"
   Driver        "kbd"
   Option        "CoreKeyboard"
   Option        "XkbRules"    "xorg"
   Option        "XkbModel"    "pc105"
   Option        "XkbLayout"    "us"
   Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
   Identifier    "Configured Mouse"
   Driver        "mouse"
   Option        "CorePointer"
   Option        "Device"        "/dev/input/mice"
   Option        "Protocol"        "ExplorerPS/2"
   Option        "ZAxisMapping"        "4 5"
   Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
   Identifier    "Synaptics Touchpad"
   Driver        "synaptics"
   Option        "SendCoreEvents"    "true"
   Option        "Device"        "/dev/psaux"
   Option        "Protocol"        "auto-dev"
   Option        "HorizScrollDelta"    "0"
EndSection


Section "Device"
   Identifier    "Internal Device"
   Driver        "ati"
   BusID        "PCI:0:16:0"
   Option        "UseFBDev"        "true"
   Screen 0
EndSection

Section "Device"
   Identifier    "External Device"
   Driver        "ati"
   BusID        "PCI:0:16:0"
   Option        "UseFBDev"        "false"
   Screen 1
EndSection

Section "Monitor"
   Identifier    "Internal Monitor"
   Option        "DPMS"
EndSection

Section "Monitor"
   Identifier    "External Monitor"
   Option        "DPMS"
EndSection

Section "Screen"
   Identifier    "Internal Screen"
   Device        "Internal Device"
   Monitor        "Internal Monitor"
   DefaultDepth    24
   SubSection "Display"
       Depth        16
       Modes        "1024x768"
       #Modes        "1280x854"
   EndSubSection
   SubSection "Display"
       Depth        24
       Modes        "1024x768"
       #Modes        "1280x854"
   EndSubSection
EndSection

Section "Screen"
   Identifier    "External Screen"
   Device        "External Device"
   Monitor        "External Monitor"
   DefaultDepth    24
   SubSection "Display"
       Depth        16
       Modes        "1024x768"
   EndSubSection
   SubSection "Display"
       Depth        24
       Modes        "1024x768"
   EndSubSection
EndSection

Section "ServerLayout"
   Identifier    "Dual Layout"
   Screen 0    "Internal Screen" 0 0
   Screen    1    "External Screen" RightOf "Internal Screen"
   InputDevice    "Generic Keyboard"
   InputDevice    "Configured Mouse"
   InputDevice    "Synaptics Touchpad"
#    Option          "Xinerama"
EndSection

#Section "ServerLayout"
#    Identifier    "Single Layout"
#    Screen 0    "Internal Screen" 0 0
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#    InputDevice    "Synaptics Touchpad"
#EndSection

Section "DRI"
   Mode    0666
EndSection
[/PHP]

---

