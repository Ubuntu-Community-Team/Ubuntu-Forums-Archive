---
title: "Screen Resolution Problem"
date: 2011-10-25
forum: Hardware
---

### Post by 0mbr3 on 2011-10-25
Hi all, 

I really am desperate for help here, i spent countless hours on a this problem and even though i learn a lot from it i am now really giving up and about to go back to windows as i really need to get some work done now :(

So basically i am using a Dell Vostro 3550 with an Hybrid intel/ ATi graphic card with only free drivers.I am on a fresh install of Ubuntu 11.10. 
Now the problem is that after i plug in my external monitor to extend my desktop, the resolution and positioning of my screen start to change randomly every few minutes. Screens Turns ON and OFF, inverse them self, and do all sort of strange configuration. 

I was thinking maybe dis-activating the auto-detection of the screen  resolution ? But can't figure how to do that.. something with Randr ? 

I changed my xorg.conf to the following (before it used to detect a bunch of screens that weren t there):


```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
    Load  "glx"
    Load  "record"
    Load  "radeon"
    Load  "i915"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
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
    Option "PreferredMode"  "1366x768"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "PreferredMode"  "1680x945"
    Option "LeftOf"  "Monitor0"
    Option "Enable"  "true"    
EndSection


Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
    Option      "EnableRandR12" "false"
        Option      "monitor-LVDS1" "Monitor0"
    Option      "monitor-VGA1" "Monitor1"
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "radeon"
    Option      "EnableRandR12" "false"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
    Identifier  "Card3"
    Driver      "fbdev"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Card4"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
    Identifier  "Card5"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
     
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card0"
    Monitor    "Monitor1"
 
EndSection



```


I would greatly appreciate any help/ insights / ideas.

Thanks a lot

---

