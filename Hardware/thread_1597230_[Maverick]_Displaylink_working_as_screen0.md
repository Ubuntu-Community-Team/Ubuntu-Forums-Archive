---
title: "[Maverick] Displaylink working as screen0"
date: 2010-10-15
forum: Hardware
---

### Post by ml1969 on 2010-10-15
Hello,

I use an Acer Aspire One D150 Netbook, have installed Ubuntu 10.10 -maverick.
All works fine inclusive Wlan.
I also have an Mimo 7" USB-touchscreen display.
I installed with the software-center the xorg-displaylink-driver and also the X2X (for mouse and keyboard)

With the help of google I found some settings for the xorg.conf which are working for me:

[PHP]

# xorg.conf (X.Org X Window System server configuration file)

############ Original Video Settings ###########

Section "Device"
        Identifier      "Configured Video Device"
    Driver        "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Depth   24
                Modes   "1024x600"
        EndSubSection
EndSection

#################################################

Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "DisplayLinkScreen" 0 0
        Screen  1       "Default Screen" LeftOf "DisplayLinkScreen"
        Option          "Xinerama" "off"
EndSection


#################################################

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"
         ModulePath    "/usr/lib/xorg/modules/drivers"
EndSection

############### DisplayLink Stuff ###############

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
                Depth   16
        Modes   "800x480"
        EndSubSection
EndSection


[/PHP]so if i start with the USB-display connected all looks good.
The Mimo is the main screen, I can use the keyboard and mouse on both screens
-I'm very happy about this -

BUT if I start the netbook without the usb-display I get no gdm login screen I only can use the commandline.

What have I to do that it doesn matter if the usb-dispaly is connected or not?


I hope you understand my (german) problem :guitar:


Michael


P.S. one little problem. If I use the touchscreen and if I touch the panel in the upper left corner the mouse will be in the lower right, it seems to be mirrored.

---

### Post by semidark on 2011-05-29
Hi there,

I'm trying to do the same thing, only with a Dell Inspiron Duo Netbook (Netvertible ;) )
I Only see the Ubuntu Logo on my Displaylink Display when i enter X11. When I switch to TTY1 (strg+alt+f1) I see the normal Bash console on the Displaylink Monitor. This text only console ist fully functional. But no X11 :(

I don't see why you need the x2x thinggy? Haven't seen any Howto that mentions it. Can you enlighten me?

To your GDM Problem. This link [http://libdlo.freedesktop.org/wiki/Ubuntu9.04](http://libdlo.freedesktop.org/wiki/Ubuntu9.04) mentions that you have to edit the file  /etc/gdm/Init/Default. Have you allready done this?

And now...here is my xorg.conf :)

```

Section "Files"
    ModulePath    "/usr/lib/xorg/modules"
    ModulePath    "/usr/local/lib/xorg/modules"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice    "Mouse0" "CorePointer"

    InputDevice    "Keyboard0" "CoreKeyboard"

        Screen  0       "Screen0" 0 0
        Screen  1       "DisplayLinkScreen" Above "Screen0"
        Option          "Xinerama" "off"
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
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        #Viewport   0 0
        Modes "1366x768"
        Depth     24
    EndSubSection
EndSection

############## DisplayLink Stuff ###############

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option          "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
        Depth    16
#        Modes   "1900x1200"
        Modes   "1024x768"
        EndSubSection
EndSection

```

Greetz Semidark

---

