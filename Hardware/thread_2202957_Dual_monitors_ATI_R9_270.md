---
title: "Dual monitors ATI R9 270"
date: 2014-02-01
forum: Hardware
---

### Post by bewareofthephog on 2014-02-01
I picked up a Radeon R9 270 today and installed the drivers from the *.run file I downloaded off of ATI's site.  I'm having two problems.  First, the admin catalyst software prompts me for a password and then never opens.  Secondly I'd like to have a dual monitor setup but the second monitor is not recgonized.  I have one monitor that is going from DVI>VGA and works fine.  The other is going from HDMI>DVI>VGA.  This monitor is not seen at all by my system in either screen or the catalyst package.  I've tried to 

```
aticonfig -f
```

followed by

```
aticonfig -set-pcs-str="DDX,EnableRandR12,FALSE"
```

And I'm still coming up with 1 monitor.  Has anyone had any success with this?

---

### Post by bewareofthephog on 2014-02-01
btw, it looks like everything is correct in xorg.conf

```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

---

### Post by kzq-lutar-x8o on 2014-12-06
> **bewareofthephog said:**
> btw, it looks like everything is correct in xorg.conf

```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```


Have you sorted your problem out?


I have a problem with ATI R9 285 compact version.

The opensource driver recognises all devices as a single screen. On other hand, AMD prop driver does not recognise dual dvi connected monitor (I use hazro 30wie). Just both drivers are unbelievably bad.

---

