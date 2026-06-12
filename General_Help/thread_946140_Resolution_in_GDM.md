---
title: "Resolution in GDM"
date: 2008-10-13
forum: General Help
---

### Post by Hieronymus on 2008-10-13
Hi, 

how can I change the resolution used for the gdm login window? I have already changed the /etc/X11/xorg.conf sections in a way that it can only chose my default screen resolution. Still it uses a resolution to large making my options fall of the screen...

:-) 

Any thoughts?

---

### Post by matey3 on 2008-10-13
I AM also looking for the command to set my lost resolution bak to what it was before. I cant hardly work with this screen! 
you can try **control-alt and + sign** and may be you can get yours back?
but mine does not go back to 1024X768 or whatever it was before?

I know there is a reconfiguration command but cant remember exactly how it went?

---

### Post by Hieronymus on 2008-10-13
Ok, I've solved this one. I made an error in the /etc/X11/xorg.conf file. This is my xorg.conf for those who need the info:

```



# VIA X11 Config file
# Created on: 2007-11-20T12:30:27-0800.
#
# Version: 6.9.0
#
Section "Files"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/local"
  FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/URW"
  FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
  FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
  FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/baekmuk:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/japanese:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/kwintv"
  FontPath     "/usr/X11R6/lib/X11/fonts/truetype"
  FontPath     "/usr/X11R6/lib/X11/fonts/uni:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/CID"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc/sgi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/input/mice"
EndSection

Section "ServerFlags"
  Option       "AllowMouseOpenFail" "on"
EndSection

Section "Module"
  Load         "v4l"
  Load         "glx"
  Load         "type1"
  Load         "extmod"
  Load         "dbe"
  Load         "freetype"
  Load         "dri"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "pc104"
  Option       "XkbRules" "xfree86"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[0]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "CorePointer"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "PS/2 Generic Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
  DisplaySize  250 150
  HorizSync    28-500
  Identifier   "Monitor[0]"
  ModelName    "VIEWSONIC VA912-4SERIES"
  Option       "DPMS"
  VendorName   "VSC"
  VertRefresh  43-60
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
#  Modeline     "1024x600" 71.11 1024 1080 1192 1360 600 601 604 630
#  Modeline     "1024x600" 69.32 1024 1080 1184 1344 600 601 604 629
#  Modeline     "1024x600" 68.48 1024 1080 1184 1344 600 601 604 629
   Modeline     "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -hsync +vsync 
EndSection

Section "Screen"
  DefaultDepth 32 
  SubSection "Display"
    Depth      32
    Modes      "1024x600"  
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "Device"
  BoardName    "Framebuffer Graphics"
  Driver       "via"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "VIA Technology"
  Option "NoDDCValue"
  Option "ActiveDevice" "LCD,CRT"
  Option "PanelID"      "17"
  Option  "DisplayHardwareLayout" "LCD"
  Option  "ForceLCD"
#[<bool>]
  Option  "VideoOnDevice" "LCD"
#  Option "LCDPort" "DVP0"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[0]" "SendCoreEvents"
  InputDevice  "Mouse[1]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
EndSection

```Jeroen

---

