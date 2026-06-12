---
title: "Change Screen Resolution (xrandr not working)"
date: 2016-10-09
forum: Hardware
---

### Post by moepmon11 on 2016-10-09
Recently I installed Lubuntu 16.04 to replace Win7 on my Medion Akoya e1228 netbook, the graphics card is nvidia GMA 3150. I would like to change the resolution to 1024x600. However, I can not do this and I am stuck with 800x600. On Windows the resolution was fine, however I removed it.

I then tried using xrandr to set the resolution as advised on many pages in the web and get ```

xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 800x600 (desired size 1024x600)
```

The output of xrandr afterwards is
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600       75.00*
   1024x600_60.00  59.85
```

I considered whether the graphics card is not detected. The output of lspci | grep VGA, so it seems to be detected.
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
```

I have the impression that the display is not properly identified. The output of sudo lshw -C video
  ```
*-display:0 UNGEFORDERT 
       Beschreibung: VGA compatible controller
       Produkt: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 02
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:fe900000-fe97ffff ioport:dc00(Größe=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff
  *-display:1 UNGEFORDERT
       Beschreibung: Display controller
       Produkt: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2.1
       Bus-Informationen: pci@0000:00:02.1
       Version: 02
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:fe780000-fe7fffff
```

I tried creating a new xorg.config with sudo X -configure. Then I followed [https://community.linuxmint.com/tutorial/view/877 to adapt xorg.conf]("https://community.linuxmint.com/tutorial/view/877") and tried setting the resolution in the xorg.conf file. However, this did not change anything, the content of xorg.conf is below.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
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
    Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "CustomEDID"             # <str>
        #Option     "DRI"                    # <str>
        #Option     "Present"                # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "HWRotation"             # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "CustomEDID"             # <str>
        #Option     "DRI"                    # <str>
        #Option     "Present"                # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "HWRotation"             # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1024x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes   "1024x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1024x600"
    EndSubSection
EndSection

```

---

### Post by rdb3 on 2016-11-02
Check out ajgreeny"s post (post # 14) with his solution in the link he provides.

The display resolution discussion begins at post #10.

[https://ubuntuforums.org/showthread.php?t=2341502](https://ubuntuforums.org/showthread.php?t=2341502)

---

