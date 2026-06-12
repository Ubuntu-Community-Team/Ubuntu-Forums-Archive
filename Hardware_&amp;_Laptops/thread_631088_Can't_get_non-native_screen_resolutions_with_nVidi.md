---
title: "Can't get non-native screen resolutions with nVidia legacy drivers"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Kelan on 2007-12-04
Hi all,
I've been having some problems with my X configuration: although I eventually managed to get a decent display going using the nVidia legacy drivers for hardware acceleration, I found myself limited to my monitor's native resolution of 1024x768 (@60). My computer is a Toshiba TE2100 Satellite; my graphics card a nVidia GeForce4 420 Go. 

I have set up my xorg.conf file as follows:

```

Section "Module"

  Load        "dri"
  Load        "glx"
  Load        "bitmap"
  Load        "ddc"
  Load        "extmod"
  Load        "glx"
  Load        "xtrap"
  Load        "record"  
  Load        "dbe"
  Load        "freetype"
  Load        "int10"
  Load        "vbe"

EndSection

Section "dri"

  Mode        0666

EndSection

Section "Files"

  FontPath 	"/usr/share/fonts/misc"
  FontPath 	"/usr/share/fonts/TTF"
  FontPath 	"/usr/share/fonts/Type1"
  FontPath 	"/usr/share/fonts/100dpi"
  FontPath 	"/usr/share/fonts/75dpi"
  FontPath 	"/usr/local/share/fonts"
  FontPath 	"/usr/share/fonts/arphicfonts"
  FontPath 	"/usr/share/fonts/baekmuk-fonts"
  FontPath 	"/usr/share/fonts/ttf-bitstream-vera"
  FontPath 	"/usr/share/fonts/default/ghostscript"
  FontPath 	"/usr/share/fonts/corefonts"
  FontPath 	"/usr/share/fonts/kochi-substitute"

EndSection

Section "InputDevice"

  Identifier	"Keyboard[0]"
  Driver	"kbd"
  Option        "XkbLayout" "dvorak"
  Option        "AutoRepeat" "500 30"
  Option        "XkbRules" "xorg"
  Option        "XkbModel" "pc104"

EndSection

Section "InputDevice"

  Identifier    "Mouse[0]"
  Driver        "mouse"
  Option        "Protocol" "Auto"
#  Option        "Device" "/dev/input/mouse2"
  Option        "Device" "/dev/input/mice"
  Option        "ZAxisMapping"   "4 5"
  Option        "buttons" "7"

EndSection

Section "Monitor"

  Identifier  "Monitor[0]"
  VendorName  "TOSHIBA"
  ModelName   "15 MULTIMEDIA DISPLAY"

  HorizSync   29.0 - 49.0
  VertRefresh 43.0 - 60.0
  Option      "DPMS" "true"

  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768  769  772  795  -HSync  +Vsync
  Modeline "800x600_60.00"   38.22  800  832  912  1024  600  601  604  622  -HSync  +Vsync
  Modeline "640x480_60.00"   23.86  640  656  720  800   480  481  484  497  -HSync  +Vsync

EndSection

Section "Device"

  Identifier	"Device[0]"
  VendorName	"Unknown"
  BoardName	"Unknown"

  Driver       "vga"

# BusID        "PCI:0:10:0"
# VideoRam      256
# Clocks        25.2 28.3

EndSection

Section "Device"

  Identifier  "Device[1]"
  Driver      "nvidia"
  VendorName  "NVidia Corporation"
  BoardName   "GeForce4 420 Go"

  BusID       "PCI:1:0:0"
#  Option      "RenderAccel" "True"
  Option      "ConnectedMonitor" "DFP"
  Option      "IgnoreDisplayDevices" "TV"
  Option      "ExactModeTimingsDVI" "1"
  Option      "DPMS"
  Option      "NoLogo" "true"

  Option      "HWcursor" "true"
  Option      "CursorShadow"
  Option      "CursorShadowAlpha" "32"
  Option      "CursorShadowXOffset" "3"
  Option      "CursorShadowYOffset" "3"
  Option      "AllowGLXWithComposite" "true"
  Option      "NvAGP" "3"

EndSection

Section "Screen"

  Identifier   "Screen[0]"
  Device       "Device[1]"
  Monitor      "Monitor[0]"

  DefaultDepth  16
  Option       "noddc"
  Option       "NoRenderExtension" "False"
  Option       "UseEdidFreqs" "True"

  Subsection   "Display"
    Viewport    0 0
    Depth       16
    Modes      "1024x768" "800x600" "640x480"
  EndSubsection

EndSection

Section "ServerFlags"

  Option        "AIGLX" "on"

EndSection

Section "Extensions"

  Option        "Composite" "enable"
# Option        "Render"    "enable"

EndSection

Section "ServerLayout"

  Identifier    "Layout[all]"
  Screen        "Screen[0]" 0 0
  InputDevice   "Mouse[0]" "CorePointer"
  InputDevice   "Keyboard[0]" "CoreKeyboard"
  Option        "AIGLX" "true"

EndSection

```

When I attempt to tab through resolutions with Ctrl+Alt++ or Ctrl+Alt+-, the 800x600 and 640x480 modes appear blank with slight jagged flickers. (If I use the open "nv" drivers, I do not have this problem, but I need the hardware acceleration.)

If anyone has a similar problem or can offer any advice, I'd be very grateful to hear it.
Thanks,
-- Kelan

P.S. I realise that, in using the proprietary nVidia drivers, I'm *supposed* to disable DRI, but I found that doing this gave choppy 3D graphics, whereas the configuration above is quite smooth.

---

