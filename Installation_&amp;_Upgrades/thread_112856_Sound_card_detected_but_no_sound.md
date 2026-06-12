---
title: "Sound card detected but no sound:"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by Mcjensen on 2006-01-05
After I installed Ubuntu, and got a few other things working I discovered that my sound was not working...any suggestions, Mcjensen



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
[CENTER]
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "dk"
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

Section "Device"
Identifier "Trident Microsystems CyberBlade/i7"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "HP D8905"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems CyberBlade/i7"
Monitor "HP D8905"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection[/CENTER]

---

### Post by sharke on 2006-01-05
1st thing to check is make sure all the volumes are up in yor mixer. It should be in multimedia.
The file you posted is your xorg config which looks like it should be okay this has nothing to do with sound.
what type of sound card do you have
Regards
Sharke

---

### Post by Ptero-4 on 2006-01-05
Also if your card is something like ATI, it may be a configuration issue. (I say that b/c there are some soundcard/modem combos out there in which you have to set it in a special way to get both parts to work properly both individually and simultaneously).

---

### Post by truthfatal on 2006-01-05
I had a similar problem with my pentium machine.
I have two sound devices on it, onboard SiS, and SB Audigy, Ubuntu made the first one (the SiS) default even though it didn't work correctly.

I went into [System >> Preferences >> Sound] and selected the Audigy (I forget if it was the driver or the card in the menu...) Sound started working instantly.

---

### Post by Mcjensen on 2006-01-05
Ok Thanks, :cool: 
I got it working now, havent got a clue exactly how, excpet I was busy tinkering, McJensen

---

