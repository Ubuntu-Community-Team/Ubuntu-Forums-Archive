---
title: "Microsoft Wireless Laser Mouse 6000 scroll wheel"
date: 2008-11-14
forum: General Help
---

### Post by blis102 on 2008-11-14
Hello,

I have a Microsoft Wireless Laser Mouse 6000 on Ubuntu 8.1. Everything is working fine, other than that the scroll wheel is behaving like the forward and back buttons in Firefox and the horizontal scroll in other applications. The horizontal scroll wheel on the other hand is behaving like the up and down scroll wheel in most applications. The left and right buttons and the side buttons work as expected.

When running xev I get this for scroll down:

```
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 31, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17118396, (44,161), root:(924,224),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17118397, (44,161), root:(924,224),
    state 0x10, button 7, same_screen YES
```

This for scroll up:

```
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 31, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17165189, (52,160), root:(932,223),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17165189, (52,160), root:(932,223),
    state 0x10, button 6, same_screen YES
```

This is for scroll right:


```
KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17305081, (21,175), root:(901,238),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17305081, (21,175), root:(901,238),
    state 0x18, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17305081, (21,175), root:(901,238),
    state 0x18, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17305081, (21,175), root:(901,238),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

This is for scroll left:

```
KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17344337, (19,176), root:(899,239),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17344338, (19,176), root:(899,239),
    state 0x18, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17344338, (19,176), root:(899,239),
    state 0x18, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13b, subw 0x0, time 17344338, (19,176), root:(899,239),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

And this is the left and right side buttons respectively:

```
KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17495869, (169,173), root:(176,236),
    state 0x10, button 9, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17495869, (169,173), root:(176,236),
    state 0x10, button 9, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17496049, (169,173), root:(176,236),
    state 0x10, button 9, same_screen YES

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17496581, (169,173), root:(176,236),
    state 0x10, button 8, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17496582, (169,173), root:(176,236),
    state 0x10, button 8, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x13b, subw 0x0, time 17496745, (169,173), root:(176,236),
    state 0x10, button 8, same_screen YES
```

I have nothing for mice in my xorg.conf file. 

I am wondering what a proper setting in the xorg file would be to get my buttons to behave as expected. If there is any more information you need, please let me know.

Thanks!

---

### Post by blis102 on 2008-11-15
Anyone have any idea how I could fix this?

---

### Post by sdowney717 on 2008-11-15
[http://www.xfree86.org/4.0.1/xmodmap.1.html](http://www.xfree86.org/4.0.1/xmodmap.1.html)
perhaps xmodmap will help

---

### Post by Xgen on 2008-11-15
OR here:

[http://ubuntuforums.org/showthread.php?t=968530](http://ubuntuforums.org/showthread.php?t=968530)

---

### Post by blis102 on 2008-11-17
Thank you for the responses, but I really have no idea how to go about using either of those (xmodmap has nothing about changing mouse settings... that I could find). Any other (graphical :) ) solutions? 

Ill try tinkering around with the xorg file again, see if I can figure it out.

Thanks!

---

### Post by dcstar on 2008-11-18
> **blis102 said:**
> Thank you for the responses, but I really have no idea how to go about using either of those (xmodmap has nothing about changing mouse settings... that I could find). Any other (graphical :) ) solutions? 
.....

I just tried one of these on my own system (8.04) and the scroll wheel worked fine.

---

### Post by blis102 on 2008-11-18
Yeah, I had my mouse working on 8.04 with some tweaking but no such luck on 8.1. Would you mind posting your xorg.conf file so I can try out what you have?

Cheers,
D

---

### Post by dcstar on 2008-11-19
> **blis102 said:**
> Yeah, I had my mouse working on 8.04 with some tweaking but no such luck on 8.1. Would you mind posting your xorg.conf file so I can try out what you have?


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:13:41 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "False"
    Option         "UseEdidDpi" "False"
    Option         "NvAGP" "3"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

---

