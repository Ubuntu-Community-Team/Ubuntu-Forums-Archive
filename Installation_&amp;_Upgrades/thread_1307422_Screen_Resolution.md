---
title: "Screen Resolution"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by hadihandojo on 2009-10-31
I have just installed Ubuntu 9.10 into my Workstation with Intel D945GCLF2 mainboard, I have got problem with my screen resolution because there are only two options 800x600 and 640x480 while I am pretty sure my LCD screen can display up to 1024x768. Could you help me how to fix this problem? Thank you.

Best regards,
Hadi Handojo
SmartBox

---

### Post by bubbles99 on 2009-10-31
**restart your system**. then go to system/preferences/display preferences. if you still cant set you resolution, i cant help you. soz.

---

### Post by hadihandojo on 2009-10-31
Yes, I did try to restart the system but same result only two options in system->preference->display. Thank you.

Hadi Handojo
SmartBox

---

### Post by tkappauf on 2009-10-31
Same board, same problem.

---

### Post by tkappauf on 2009-11-03
Check your hardware.

In the process of trying to fix the issue, I got it so goofed up I had to remove the computer from its remote location (about 25' away) and connect everything directly. I installed a cd drive and booted from that (Hardy, which worked fine as to monitor resolution) to edit and return to the original Karmic xorg.conf. With the short vga cable without an extender, the monitor resolution worked as I hoped. After returning the computer to the cabinet, I'm back to the 800x600. So in this case anyway, the hardware makes a difference that it didn't make in Jaunty.

Todd K.

---

### Post by chumpjaw on 2009-11-03
same problem here... screen is at 800x600.  I ran into this before and fixed it with the /etc/x11/xorg.conf file, but don't see it in 9.10???

---

### Post by chumpjaw on 2009-11-03
> **chumpjaw said:**
> same problem here... screen is at 800x600.  I ran into this before and fixed it with the /etc/x11/xorg.conf file, but don't see it in 9.10???


ok...  here we go... thanks Pipsey ([http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283))

First - create a file called xorg.conf with the following in it...
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
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
    Load  "record"
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
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
EndSection
```Second - now move that file to /etc/X11/ 

Third - from the terminal
```
sudo chmod a+r /etc/X11/xorg.conf
```Fourth - reboot and change the resolution from your display properties.

---

### Post by hadihandojo on 2009-11-04
Hi,
Thank you, after I change the xorg.conf, it works. I even got 8 choices from 640x480 up to 1360x768. Thank's once again.

Best regards,
Hadi Handojo
SmartBox

---

