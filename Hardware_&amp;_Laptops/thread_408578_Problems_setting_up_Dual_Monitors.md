---
title: "Problems setting up Dual Monitors"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by ewestern on 2007-04-13
I recently installed Ubuntu 6.10 and was able to install the nVidia 9746 drivers.  I have tried setting up dual monitor support in the nVidia control panel but the settings do not stay when I restart gnome.

Any ideas on what I need to do in order for the dual monitors to work?  Any more information you need?  I know this is sparse but I am work right now.

Thanks.

---

### Post by Scunizi on 2007-04-14
You'll probably need to edit your xorg.conf file.  First decide if you want twinnview (supported only by nvidia) or xinerama (supported by x using nvidia drivers).  Both have slightly different functions.  Twinnview creates one huge desktop out of  both screens.  Xinerama creates two unique screens one with the standard dressing and the other with .. basically just the background.  Xinerama allows you to drag and place an item from one desktop to the other.
You can edit xorg.conf by first backing it up.. terminal... sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back  ... then to edit .. sudo gedit /etc/X11/xorg.conf.  

Here's my old xinerama setup when I ran two screens.
```
Section "ServerLayout"
 Identifier	"xinerama"
 Screen	0 "Screen0"
 Screen	1 "Screen1" RightOf "Screen0"
 InputDevice    "Generic Keyboard"
 InputDevice    "Configured Mouse"
 Option "Xinerama" "1"
EndSection

Section "Files"

 # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
 FontPath        "/usr/share/X11/fonts/cyrillic"
 FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/Type1"
 FontPath        "/usr/share/X11/fonts/100dpi"
 FontPath        "/usr/share/X11/fonts/75dpi"
 FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load           "i2c"
 Load           "bitmap"
 Load           "ddc"
 Load           "extmod"
 Load           "freetype"
 Load           "glx"
 Load           "int10"
 Load           "type1"
 Load           "vbe"
EndSection

Section "InputDevice"
 Identifier     "Generic Keyboard"
 Driver         "kbd"
 Option         "CoreKeyboard"
 Option         "XkbRules" "xorg"
 Option         "XkbModel" "pc104"
 Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier     "Configured Mouse"
 Driver         "mouse"
 Option         "CorePointer"
 Option         "Device" "/dev/input/mice"
 Option         "Protocol" "ExplorerPS/2"
 Option         "ZAxisMapping" "4 5"
 Option         "Emulate3Buttons" "true"
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection


Section "Monitor"
 Identifier	"Envision"
 Option	"dpms"
 HorizSync 30.0-81.0
 VertRefresh 56-75
EndSection

Section "Monitor"
 Identifier	"HSD HN199D"
 Option	"dpms"
 HorizSync 28.0-51.0
 VertRefresh 43-60
EndSection

Section "Device"
    Identifier  "Nvidia0"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       0
 #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "CRT"
    Option "UseDisplayDevice" "CRT"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "FALSE"
EndSection

Section "Device"
    Identifier  "Nvidia1"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       1
    #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "DFP"
    Option "UseDisplayDevice" "DFP"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "FALSE"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device	"Nvidia0"
    Monitor	"Envision"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

Section "Screen"
    Identifier	"Screen1"
    Device	"Nvidia1"
    Monitor	"HSD HN199D"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

```

Here's an example of Twinview
```
Section "ServerLayout"
 Identifier	"twinview"
 Screen	0 "Screen0"
 Screen	1 "Screen1" RightOf "Screen0"
 InputDevice    "Generic Keyboard"
 InputDevice    "Configured Mouse"
 Option "Xinerama" "0"
EndSection

Section "Files"

 # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
 FontPath        "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/Type1"
 FontPath        "/usr/share/X11/fonts/100dpi"
 FontPath        "/usr/share/X11/fonts/75dpi"
 FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load           "i2c"
 Load           "bitmap"
 Load           "ddc"
 Load           "extmod"
 Load           "freetype"
 Load           "glx"
 Load           "int10"
 Load           "type1"
 Load           "vbe"
EndSection

Section "InputDevice"
 Identifier     "Generic Keyboard"
 Driver         "kbd"
 Option         "CoreKeyboard"
 Option         "XkbRules" "xorg"
 Option         "XkbModel" "pc104"
 Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier     "Configured Mouse"
 Driver         "mouse"
 Option         "CorePointer"
 Option         "Device" "/dev/input/mice"
 Option         "Protocol" "ExplorerPS/2"
 Option         "ZAxisMapping" "4 5"
 Option         "Emulate3Buttons" "true"
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection


Section "Monitor"
 Identifier	"Envision"
 Option	"dpms"
 HorizSync 30.0-81.0
 VertRefresh 56-75
EndSection

Section "Monitor"
 Identifier	"HSD HN199D"
 Option	"dpms"
 HorizSync 28.0-51.0
 VertRefresh 43-60
EndSection

Section "Device"
    Identifier  "Nvidia0"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       0
 #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    Option "ConnectedMonitor" "CRT"
    #Option "UseDisplayDevice" "CRT"
    Option "TwinViewOrientation"  "DFP-0 RightOf CRT-0"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "NvAgp" "3"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Device"
    Identifier  "Nvidia1"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       1
    #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    Option "ConnectedMonitor" "DFP"
    Option "NvAgp" "3"
    #Option "UseDisplayDevice" "DFP"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device	"Nvidia0"
    Monitor	"Envision"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

Section "Screen"
    Identifier	"Screen1"
    Device	"Nvidia1"
    Monitor	"HSD HN199D"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

```

---

