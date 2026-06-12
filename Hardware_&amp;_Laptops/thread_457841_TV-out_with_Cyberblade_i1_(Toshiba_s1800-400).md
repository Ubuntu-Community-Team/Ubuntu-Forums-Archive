---
title: "TV-out with Cyberblade i1 (Toshiba s1800-400)"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by HydroDiOxide on 2007-05-29
I'm having a really hard time getting TV-out to work on my old Toshiba Satellite 1800-400 with a Trident Cyberblade i1 vga card. I want to have TV-out under X (Gnome) so I can use the laptop as video player when connected to my TV (composite). The FN+F5 keys seem to switch screens, but nothing shows up on my tv.

lspci output:
```

00:00.0 Host bridge: ALi Corporation M1632M Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)
```

Enabling TV-out in xorg.conf following [_these_]("http://www.xfree.org/current/trident.4.html#sect4") instructions doesn't work.

xorg.conf setup:
```
laptop videos # cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        RgbPath      "/usr/share/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/misc/"
        FontPath     "/usr/share/fonts/TTF/"
        FontPath     "/usr/share/fonts/OTF"
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/100dpi/"
        FontPath     "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
        Load  "glx"
        Load  "extmod"
        Load  "xtrap"
        Load  "record"
        Load  "GLcore"
        Load  "dbe"
        Load  "dri"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
        #VendorName     "Monitor Vendor"
        #ModelName      "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"               # [<str>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "PciRetry"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SetMClk"                   # <freq>
        #Option     "MUXThreshold"              # <i>
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # [<str>]
        #Option     "VideoKey"                  # <i>
        #Option     "NoMMIO"                    # [<bool>]
        #Option     "NoPciBurst"                # [<bool>]
        #Option     "MMIOonly"                  # [<bool>]
        #Option     "CyberShadow"               # [<bool>]
        Option     "CyberStretch" "True"        # [<bool>]
        #Option     "XvHsync"                   # <i>
        #Option     "XvVsync"                   # <i>
        #Option     "XvBskew"                   # <i>
        #Option     "XvRskew"                   # <i>
        #Option     "FpDelay"                   # <i>
        #Option     "Display1400"               # [<bool>]
        Option     "Display"    "Dual"          # [<str>]
        #Option     "GammaBrightness"           # [<str>]
        Option     "TVChipset"  "VT1621"        # [<str>]
        Option     "TVSignal"   "1"             # <i>
        Identifier  "Card0"
        Driver      "trident"
        VendorName  "Trident Microsystems"
        BoardName   "CyberBlade/i1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        DefaultDepth 16
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

Does anyone have any ideas how to get this up and running?

---

### Post by HydroDiOxide on 2007-05-30
bump :roll:

---

### Post by HydroDiOxide on 2007-06-18
bump, again... :shock:

---

### Post by Mike_T on 2008-03-25
Take a look here:
[http://www.backports.ubuntuforums.org/showthread.php?p=4260618](http://www.backports.ubuntuforums.org/showthread.php?p=4260618)

---

