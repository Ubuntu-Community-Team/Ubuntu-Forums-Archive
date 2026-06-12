---
title: "Sharp Aquos 46&quot; 1080P 120Hz - Can't get 120Hz with xorg"
date: 2010-03-28
forum: Hardware
---

### Post by DaJL on 2010-03-28
Just got a sharp aquos LC-46D85UN and I can't get it to run at 120Hz.  Its stuck at 50Hz and I'm starting to get a headache. 

I verified my nvidia-setting and force gpu scaling is not checked.
I got the modelines with gft 19020 1080 120

Here is what my xorg.conf looks like:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SHARP HDMI"
#    HorizSync       
#    VertRefresh    
    # 1920x1080 @ 120.00 Hz (GTF) hsync: 138.84 kHz; pclk: 368.76 MHz
    Modeline "1920x1080_120.00"  368.76  1920 2072 2288 2656  1080 1081 1084 1157  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
#    Option "UseEdidFreqs" "0"
#    Option "FlatPanelProperties" "Scaling = Native"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I tried with Option "UseEdidFreqs" "0"   but that just makes it worst. same refresh but can't see my whole desktop.

Also tried with Option "FlatPanelProperties" "Scaling = Native" and that didn't change anything.

I can't find  what the  HorizSync and VertRefresh should be for this TV and its not in the manual :(

any help would be greatly appreciated.

---

### Post by DaJL on 2010-03-28
I'm in karmic but also tried in a fresh install of lucid and its the same behavior.

---

### Post by DaJL on 2010-03-28
I have an Nvidia 7300GT 256M.  Maybe I need a better video card?

---

### Post by realzippy on 2010-03-28
Assume you do not have the choice in nvidia-settings for
1920x1080?
*Acquired* EDID with nvidia-settings and pointed to that file in xorg.conf?

---

### Post by efflandt on 2010-03-28
1080p is 60 Hz.  Where in your manual do you see anything mentioning 120 Hz input modes?

Fine motion enhancement may internally interpolate images at 120 Hz to sharpen and reduce motion blur or smooth out stutter from film sources, but the HDMI (or VGA) input signal is still ~60 Hz.

My LG 32LH40 HDTV has 120 Hz enhancement, but its 1080p modes are listed as:

RGB-PC 66.587 KHz horiz, 59.934 Hz vertical
HDMI-PC 67.5 KHz horiz, 60 Hz vertical

Your manual lists "some" PC modes up to 75 Hz, but does not provide details of HDTV modes (which should be according to standards), other than that it is 1920x1080 pixels.

---

### Post by DaJL on 2010-03-28
realzippy:  I already have it running at 1920x1080 but at 60Hz

efflandt:  So I guess I had a misconception of what a 120Hz tv is :(

---

