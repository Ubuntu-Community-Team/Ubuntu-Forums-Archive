---
title: "LG r405, can't get X to work"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by BrunoXLambert on 2008-03-09
Hello,

I bought a brand new LG-R405 ([http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=FR&sku_id=0665000FS10098998&catid=25314](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=FR&sku_id=0665000FS10098998&catid=25314))

I had to throw the "noapic nolapic acpi=noirq" option at grub to make it boot.

My Ethernet adapter only work on Slax 6.0.0 and Ubuntu hardy-alpha6 (doesn't work on debian etch, debian testing(20080306) and slackware 12.0, I guess the driver is in the kernel 2.6.24).

Right now I can't get X to work using the hardy-alpha6 LiveCD. I have only been able to start X in Slax.. The Graphic card is an ATI Xpress 2500 (looks like working fine), but I always get a 

(EE) No devices detected.

Fatal server error: 
no screens found.

I've got not error about the graphic card, It just can't see my 14.1'' display... I've used the same xorg.conf file than in Slax, with no result.

```

Section "ServerLayout"
Identifier     "X.org Configured"
Screen      0  "Screen0" 0 0
InputDevice    "Mouse0" "CorePointer"
InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/share/fonts/TTF"
FontPath     "/usr/share/fonts/OTF"
FontPath     "/usr/share/fonts/Type1"
FontPath     "/usr/share/fonts/misc"
FontPath     "/usr/share/fonts/75dpi/:unscaled"
EndSection

Section "Module"
Load  "GLcore"
Load  "dbe"
Load  "dri"
Load  "extmod"
Load  "glx"
Load  "record"
Load  "xtrap"
Load  "freetype"
Load  "type1"
EndSection

Section "InputDevice"
Identifier  "Keyboard0"
Driver      "kbd"
EndSection

Section "InputDevice"
Identifier  "Mouse0"
Driver      "mouse"
Option      "Protocol" "auto"
Option      "Device" "/dev/input/mice"
Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier   "Monitor0"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection

Section "Device"
Identifier  "Card0"
Driver      "radeonhd"
VendorName  "ATI Technologies Inc"
BoardName   "Unknown Board"
BusID       "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
EndSubSection
EndSection

```

Does anybody have an answer for this?

Thanks, 
Bruno Lambert

---

### Post by BrunoXLambert on 2008-03-11
Using the proprietary ATI driver kind of solved my problem. Just sucks I had to use blobs.

---

