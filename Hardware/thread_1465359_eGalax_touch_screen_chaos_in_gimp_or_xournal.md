---
title: "eGalax touch screen chaos in gimp or xournal"
date: 2010-04-29
forum: Hardware
---

### Post by Horatio on 2010-04-29
Has anyone using the eGalax touch screen been able to us it to draw, and can you help me configure it? I get a bunch of line from the corner of the screen to where the stylus currently is instead of a smooth path.

I'm using the drivers downloaded from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm).

I'm hoping someone was at the point I'm at( the default configurations after executing ./setup.sh) and know what needs to be done from here.

Thanx

---

### Post by Chac on 2010-09-29
Same issue for me
Did you already fix it?

---

### Post by Chac on 2010-09-29
Hi 
I found the fix

Comment out

#Section "InputClass"
#        Identifier "evdev tablet catchall"
#        MatchIsTablet "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection

in /usr/share/X11/xorg.conf.d/10-evdev.conf

And add following xorg.conf in /etc/X11/ (Modify for your card, etc):

Section "ServerLayout"
        InputDevice "EETI" "SendCoreEvents"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ACI MW221"
    HorizSync       47.0 - 84.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
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

### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###

---

