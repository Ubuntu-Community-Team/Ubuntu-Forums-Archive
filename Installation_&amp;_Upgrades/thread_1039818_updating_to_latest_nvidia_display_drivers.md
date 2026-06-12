---
title: "updating to latest nvidia display drivers"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by underworld288 on 2009-01-14
After I installed the latest display drivers (180.22) from nvidia's website my computer won't boot into ubuntu. When I select to boot into ubuntu the loading screen comes up but then I just get a black screen. I looked at my xorg.conf file and the nvidia installer must have messed it up because now it hardly has anything in it. I tryed to run ```
Xorg -configure
``` but it failed telling me that it set up to many displays. 

Can anybody try to help me through this?

---

### Post by underworld288 on 2009-01-15
After much pain and suffering trying to figure this out i have managed to fix the problem. It was the xorg.conf file that was the problem - although I already knew that much.

---

### Post by rameijer on 2009-01-15
I, and I'm sure many others, would be grateful if you could tell us exactly what you did [IMG]http://sc.webmessenger.msn.com/10.1.0323.0/session/images/emoticons/smile_regular.gif[/IMG]

---

### Post by toobitz on 2009-01-17
Could you please share with the community how you solved the problem? I personally would be very grateful. Thank you!

---

### Post by underworld288 on 2009-01-17
ok the problem that my machine was having had to do with the xserver saying it couldn't find a working monitor. I simply went through the xorg.conf.new file that the Xorg -configure command outputted to the /home/username directory. After looking through that file and the file that nvidia installer automatically made I made changes until it worked. This is my resulting xorg.conf file...

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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
    ModelName      "Samsung SyncMaster"
    HorizSync      30.0 - 81.0
    VertRefresh    56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Driver	   "nvidia"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

