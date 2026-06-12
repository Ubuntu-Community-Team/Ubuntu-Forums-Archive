---
title: "Problem with ATI binary driver"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by martinrandau on 2007-08-24
I have installed the ATI binary drivers by the standard method, ie install restricted modules, xorg-driver-fglrx and then using aticonfig to initialize and making the overlay.

But I get this:```

martin@yeah:~$ glxinfo | grep Yes
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
```

and xorg.conf looks like this: ```
Section "Device"
        Identifier  "Generic Video Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

In other words, the drivers are installted and setup correctly in xorg.conf but I am still using the MESA drivers and have no 3d acceleration! :confused:

Please help!

---

### Post by martinrandau on 2007-08-24
Now this is very silly: the restricted driver manager is not installed on Kubuntu, so I had to install it to allow the usage of the ati-driver. 

Problem solved...

---

