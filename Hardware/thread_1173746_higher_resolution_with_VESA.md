---
title: "higher resolution with VESA"
date: 2009-05-30
forum: Hardware
---

### Post by scottc52 on 2009-05-30
Is there a way of using the VESA driver, and getting a resolution higher than 800*600?

---

### Post by scottc52 on 2009-05-30
Issue solved. Here's my xorg.conf file, just in case someone needs it.

Section "ServerFlags"
  Option       "AllowMouseOpenFail" "on"
  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "freetype"
  Load         "extmod"
  Load         "dbe"
  Load         "glx"
  Load         "dri"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImPS/2 Generic Wheel Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
  Option       "Buttons" "7"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  DisplaySize  305 230
  HorizSync    30-40
  Identifier   "Monitor[0]"
  ModelName    "Unknown"
  Option       "DPMS"
  Option       "PreferredMode" "1280x1024"
  VendorName   "Unknown"
  VertRefresh  50-75
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
EndSection


Section "Screen"
  DefaultDepth 16
  SubSection "Display"
    Depth      15
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "Radeon LW"
  Driver       "vesa"
  Identifier   "Device[0]"
  Option       "XAANoOffscreenPixmaps" "true"
  Screen       0
  VendorName   "ATI"
EndSection



Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
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

---

