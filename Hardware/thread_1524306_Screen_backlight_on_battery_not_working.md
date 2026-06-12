---
title: "Screen backlight on battery not working"
date: 2010-07-05
forum: Hardware
---

### Post by atundel on 2010-07-05
Good morning boys and girls:

I am the proud owner of a Samsung r510 laptop running Lucid Lynx, with Intel graphics.

I am not able to control brightness with Gnome's Power Manager, neither the brightness App does. 

When started with battery the screen's dimmed and there is nothing to do about it but boot with power and then disconnect it from the charger.

Does any kind of fix exist?

Thanks in advance.

---

### Post by clrg on 2010-07-05
I have a Thinkpad T410, and I had to add some lines to /etc/X11/xorg.conf in order to get brightness control to work. It worked fine with nouveau, but not with the proprietary (evil) NVidia drivers.. Maybe you need to do something similiar. 

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "EmulateWheel" "on"
    Option         "EmulateWheelButton" "2"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
 **   Option         "RegistryDwords" "EnableBrightnessControl=1"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Not a fix, but a workaround would be to disable the option "Reduce backlight brightness" in gnome's power settings. Then it should stop doing that.

---

### Post by ak123 on 2010-07-05
None of that is necessary... 

just add the ppa on this website... [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

then install the samsung-backlight package and a few of the other ones... (look at the description in synaptic and decide which ones you want).. after that you should be good to go...

post on your results..

oh... it might be easier if you look at the packages in the software center instead of synaptic...

---

### Post by atundel on 2010-07-05
Thanks for your quick response!

Installing the packages did not solve it! :(

samsung-tools package only activated the webcam hotkey...

---

### Post by ak123 on 2010-07-10
hmmm.. its weird... the package suddenly stopped working after some update...now i dont have control...

update: try running ```
sudo dpkg --configure -a
```

worked for me...

---

