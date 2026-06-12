---
title: "Issues with dual-head config with Matrox G450"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by dilyard on 2007-11-15
I have a Lenovo Thinkcentre  M55p which I've had three versions of Kubuntu installed on: Edgy, Feisty and now Gutsy. I put a Matrox G450 PCI in it while running Edgy and enjoyed a nice dual-head desktop after some grief. The biggest problem with the install of the card is that Ubuntu seems to detect the onboard Intel video while the BIOS is defaulting to the PCI card. In Edgy, I was able to disable the Intel video adapter in the System Settings. 

When I installed Feisty (beta, then Prod), I could never get the dual-head display to work. Even using my working xorg.conf file from Edgy, the best I could get was a mirrored display on both monitors. The display settings in Feisty never worked due to a bug which was never fixed so my hopes lied with Gutsy.

Now, Gutsy allows me to configure the dual-head and enable xinerama, but after restarting X, I'm still stuck with a mirrored display. I'm attaching my xorg.conf file and would appreciate any guidance on this. 

Notice the BUSID's. The first Matrox display is correct, but the second one is the address for the Intel onboard video. If I change the BUSID for the second to match and bounce X, I get no change in my display, but in the graphical config tool, I have three display interfaces instead of two: two matrox and one Intel. I've tried blacklisting the intel-agp kernel module, but it does not seem to make any difference.  Any ideas?

lspci: 
> 
00:02.0 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
0b:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 85)


xorg.conf:
> 
Section "Files"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  #	Load	"glx"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "Device"
  identifier "Matrox G450 PCI"
  boardname "Matrox Millennium G450 DualHead"
  busid "PCI:11:0:0"
  driver "mga"
  screen 0
  vendorname "Matrox"
EndSection

Section "Monitor"
  identifier "Philips 190B"
  vendorname "Generic"
  modelname "Flat Panel 1280x1024"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Matrox G450 PCI"
  Monitor "Philips 190B"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" #  
  identifier "device1"
  boardname "Matrox Millennium G450 DualHead"
  busid "PCI:0:2:0"
  driver "mga"
  screen 0
  vendorname "Matrox"
EndSection
Section "screen" #  
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "1280x1024@60"
  EndSubSection
EndSection
Section "monitor" #  
  identifier "monitor1"
  vendorname "Generic"
  modelname "Flat Panel 1280x1024"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection
Section "ServerFlags"
  option "Xinerama" "true"
EndSection


---

### Post by dilyard on 2007-11-15
Anyone?

---

### Post by dilyard on 2007-11-18
Well, I added an XP partition and it works fine with Windows.  I suppose I can give SLES a try if Ubuntu cannot properly detect video hardware.

---

