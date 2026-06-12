---
title: "SLI Troubleshoot"
date: 2009-06-17
forum: Hardware
---

### Post by stonerhino28 on 2009-06-17
I have a box that has am ASUS P5N-T Deluxe, an Intel Q6600, 8 GB RAM, 2 x EVGA 8800 GT in SLI.  My xorg.conf is as follows:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Option         "SLI"    "Auto"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    # generated from default
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:03:00:00"
    Driver    "nvidia"
EndSection

Section "Device"
    Identifier     "Device1"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:04:00:00"
    Driver    "nvidia"
EndSection

When I run:
    sudo lspci | grep VGA
I get:
    03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

At one time i got a similar line:
    03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
    04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
I then went in and added the line
    Option         "SLI"    "Auto"
I had some issues and then restarted.  I had to load the old xorg file and then restarted but now i only show one card.  Is there something that i am missing?

Thanks,
Steve  :sad:

---

