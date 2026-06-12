---
title: "No keyboard and touchpad since update to karmic"
date: 2009-12-28
forum: Hardware
---

### Post by obiwankennedy on 2009-12-28
Hi all,

My computer is a Vaio FE21M. 
I updated it to Karmic, then the keyboard and the touchpad don't work at all. If I plug another mice/keyboard, It works but the touchpad/embedded keyboard stay quite). 

I have no idea of what is going on. 
I paste my xorg.conf.

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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load  "dri"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbLayout"    "fr"
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
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "G73 [GeForce Go 7600]"
    BusID       "PCI:1:0:0"
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
```If I run this command :
sudo cat /dev/input/mice 
and then play a little with the touchpad, I see some stuff into the console but the cursor does not move.

---

### Post by Cue2 on 2010-02-11
Have You Solved This Problem? I Seem To Have The Same Problem Too. the Keyboard Works Up Until Ubuntu boots Up.

---

### Post by flippo on 2010-02-11
Nowadays keyboards and mice are detected via hotplug with hal and udev, its not recommended to configure them directly in Xorg.conf.  Check and make sure you have .fdi files for them (found in /etc/hal/fdi/policy/)  and comment out the lines:

```
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
```

in your Xorg.conf as well as the sections for your Mouse0 and Keybord0.

The fdi file you should be looking for is:
```
10-x11-input.fdi
```
And if you have a synaptics touchpad
```
11-x11-synaptics.fdi
```

Let me know what you find.

---

### Post by Cue2 on 2010-02-12
> **flippo said:**
> Nowadays keyboards and mice are detected via hotplug with hal and udev, its not recommended to configure them directly in Xorg.conf.  Check and make sure you have .fdi files for them (found in /etc/hal/fdi/policy/)  and comment out the lines:

```
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
```

in your Xorg.conf as well as the sections for your Mouse0 and Keybord0.

The fdi file you should be looking for is:
```
10-x11-input.fdi
```
And if you have a synaptics touchpad
```
11-x11-synaptics.fdi
```

Let me know what you find.

Hi flippo Thanks For The Help

ls /etc/hal/fdi/policy/

Only shows 

preferences.fdi

cat /dev/input/mice 
Does Show Things When The Mouse Is Moved Though. How Do i Get Or Create These fdi Files. (sorry About The Caps, using Vnc For Keyboard does This)

---

### Post by Cue2 on 2010-02-12
OK (no more caps ;)), I added this to the end of my xorg.conf file for a temporary fix 

```

Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection 
```

now my keyboard and mouse works without hotplug. At least until xorg.conf is changed automatically. however I really would like to get this hotplug working so if you have any idea how I can set it up (fix it) I'd appreciate it.

---

### Post by flippo on 2010-02-12
That is also an acceptable fix.  I forgot that in 9.10 ubuntu dropped hal (my latest build is 8.04), so you would have to muck around with their replacement, I *think* devicekit...  I sadly know almost nothing about it.

---

