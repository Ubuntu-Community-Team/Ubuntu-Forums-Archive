---
title: "Geode + New Xorg server."
date: 2009-08-01
forum: Hardware
---

### Post by Arcfox on 2009-08-01
Hello. I have a problem with change correct screen resolution (1024x600) in my laptop. There is Maxmedia Cameron NB-1060 (Geode LX800 500MHz/10.2"/512Mb/).
My /etc/X11/xorg.conf :
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

#Section "ServerFlags"
#    Option    "AutoAddDevices"  "False" 
#EndSection

Section "Module"
    Load  "dbe"
    Load  "dri2"
    Load  "record"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option    "AutoRepeat"
    Option    "XkbDisable"
    Option    "CoreKeyboard"
    Option    "XkbRules"    "xorg"
    Option    "XkbModel"    "pc101"
    Option    "XkbLayout"    "us,ru'
    Option    "XkbVariant"    ",winkeys"
    Option    "XkbOptions"    "grp:lwin_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "DPMS"
    HorizSync 28-50
    VertRefresh 43-73
    Modeline "1024x600" 50.0 1024 1104 1176 1248 600 603 619 630
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
    Identifier  "Card0"
    Driver      "geode"
    VendorName  "Advanced Micro Devices [AMD]"
    BoardName   "Geode LX Video"
    BusID       "PCI:0:1:1"
    Option      "PanelGeometry" "1024x600"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
   SubSection "Display"
        Depth   24
        Modes      "1024x600"
   EndSubSection
EndSection
```This configuration file have worked with old xorg servers (I don't remmember version) but it isn't working now. When I have installed ubuntu (with lxde), file '/etc/X11/xorg.conf' was not exist but Xserver had working. I also attempted use xrandr to change screen resolution but it isn't help (resolution is not correct). Now I don't know what controlling my xorg server. Any idea?

---

