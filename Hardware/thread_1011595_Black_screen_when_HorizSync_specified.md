---
title: "Black screen when HorizSync specified"
date: 2008-12-14
forum: Hardware
---

### Post by kristopherwilson on 2008-12-14
When I add a value for HorizSync, I just get a black screen when starting X (with no warnings or errors in the log file).

My card is:

```
01:00.0 VGA compatible controller: VIA Technologies, Inc.
K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
```

Here is my xorg.conf:

```
Section "ServerLayout"
   Identifier     "X.org Configured"
   Screen      0  "Screen0" 0 0
   InputDevice    "Mouse0" "CorePointer"
   InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
EndSection

Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option       "Protocol" "auto"
   Option       "Device" "/dev/input/mice"
   Option       "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
   Identifier   "Monitor0"
   VendorName   "Panasonic"
   ModelName    "TH-46PZ85U"

   Option "NoDDC"
   
   HorizSync 15-110
   VertRefresh 48-120
EndSection

Section "Device"
   Identifier  "Card0"
   Driver      "openchrome"
   VendorName  "Unknown Vendor"
   BoardName   "Unknown Board"
   BusID       "PCI:1:0:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Monitor0"
   DefaultDepth    24
   SubSection     "Display"
      Depth       8
      Modes      "1440x900" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
      Depth       16
      Modes      "1440x900" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
      Depth       24
      Modes      "1440x900" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
      Depth       32
      Modes      "1440x900" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection
```

I'm using the horizontal and vertical frequencies specified in my TV's user manual. Any ideas why this is happening?

---

