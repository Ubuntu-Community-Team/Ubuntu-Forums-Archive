---
title: "EDP display does not function"
date: 2017-11-07
forum: Hardware
---

### Post by &amp;*@Fth&amp;% on 2017-11-07
I've been trying to get a laptop EDP display working with my computer. I've built my own adapter cable with some voltage regulators off the 12V rail to power the logic and backlight. I've quintouple-checked every connection on the cable, and everything is correct.

On to the issue itself: the display just doesn't work. When I connect it to my video out, it shows up in the list of displays in the settings menu, but is initially disabled. It reports "no available resolutions", and the only refresh rate available is auto. If I enable the display at this stage, it partially corrupts the output of the running primary display ( a bottom section will go all shades of purple mixed with pieces of the frame generated before it was enabled) and the EDP display does nothing.

If I manually input the supported resolutions and refresh rates using xrandr before enabling the display, it doesn't do any of the corruption stuff, but the moment I click apply, the display is disabled again. If I enable it using the terminal, it doesn't give any errors, but nothing happens and the display stays disabled.

xorg.conf:
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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
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
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"              # [<bool>]
        #Option     "kmsdev"                # <str>
        #Option     "ShadowFB"              # [<bool>]
        #Option     "AccelMethod"           # <str>
        #Option     "PageFlip"              # [<bool>]
        #Option     "ZaphodHeads"           # <str>
        #Option     "DoubleShadow"          # [<bool>]
    Identifier  "Card0"
    Driver      "modesetting"
    BusID       "PCI:11:0:0"
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
Output of xrandr:

```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected (normal left inverted right x axis y axis)
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00*+  50.00    59.94    59.93  
   1680x1050     69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     74.76    70.00    59.98  
   1280x1024     75.02    60.02  
   1440x900      59.89    59.90  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1280x800      59.91  
   1152x864      75.00    75.00    70.00    60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.05    60.04    75.03    70.07    60.00  
   960x720       75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   960x600       60.00  
   832x624       74.55  
   960x540       59.99  
   800x600       75.00    70.00    65.00    60.00    72.19    75.00    60.32    56.25  
   840x525       74.96    69.88    60.01    59.88  
   720x576       50.00  
   800x512       60.17  
   700x525       74.76    70.06    59.98  
   720x480       60.00    59.94  
   640x512       75.02    60.02  
   720x450       59.89  
   640x480       60.00    72.81    75.00    66.67    60.00    59.94  
   720x400       70.08  
   680x384       59.80    59.96  
   576x432       75.00    75.00    70.00    60.06  
   512x384       75.03    70.07    60.00  
   416x312       74.66  
   400x300       72.19    75.12    60.32    56.34  
   320x240       72.81    75.00    60.05  
HDMI-2 disconnected (normal left inverted right x axis y axis)
DVI-D-1 disconnected (normal left inverted right x axis y axis)

```I am using the latest proprietary AMD drivers (17.40) on an RX 480 graphics card, with Kubuntu 17.10.

---

### Post by &amp;*@Fth&amp;% on 2017-11-11
Not sure if bumping is legal, but I didn't see anything in the code of conduct, so... bump.

---

### Post by &amp;*@Fth&amp;% on 2017-11-22
Bump

---

