---
title: "quadro nvs 420 only output on 2 screens not 4"
date: 2010-09-16
forum: Hardware
---

### Post by florusb on 2010-09-16
Hi,
i have been fighting with my freshly installed ubuntu and quadro nvs 420 card.
attached 4 monitors, installed 256.53 of the linux drivers, but only output on 2 screens: 1 and 2 on the connector.

below my current xorg.conf (i tried a lot of settings there ).
one thing i noticed if is change DFP to DFP-0 and DFP-1 i get output on 2 screens but on 1 and 4!

any ideas, as this is driving me mad!!

many thanks

florus.


Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0"
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
Screen 3 "Screen3" RightOf "Screen2"
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Files"
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

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor3"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "Quadro NVS 420"
Option "ConnectedMonitor" "DFP"
Option "CustomEDID" "DFP:/etc/X11/philips224E.bin"
BusID "PCI:3:0:0"
EndSection

Section "Device"
Identifier "Device2"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "Quadro NVS 420"
Option "ConnectedMonitor" "DFP"
Option "CustomEDID" "DFP:/etc/X11/philips224E.bin"
BusID "PCI:3:0:0"
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "Quadro NVS 420"
Option "ConnectedMonitor" "DFP"
Option "CustomEDID" "DFP:/etc/X11/philips224E.bin"
BusID "PCI:4:0:0"
EndSection

Section "Device"
Identifier "Device3"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "Quadro NVS 420"
Option "ConnectedMonitor" "DFP"
Option "CustomEDID" "DFP:/etc/X11/philips224E.bin"
BusID "PCI:4:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Device2"
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen2"
Device "Device1"
Monitor "Monitor2"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen3"
Device "Device3"
Monitor "Monitor3"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

---

