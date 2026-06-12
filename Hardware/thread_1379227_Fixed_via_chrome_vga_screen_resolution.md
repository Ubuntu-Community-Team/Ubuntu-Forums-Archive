---
title: "Fixed via chrome vga screen resolution"
date: 2010-01-12
forum: Hardware
---

### Post by pi/roman on 2010-01-12
I just wanted to file a report somewhere that it may help someone who has the same problems as me  because I worked for a long time on this and lost a lot of hair and grew a beard. 

My Gateway MX3228 would display a resolution of 1600x1200 even though my screen could only display 1280x768 which made most of the screen not show up.  So I installed in safe video mode then I could not get the resolution to be larger than 600x480 which made the everthing so large it would not fit on the screen.  So I formatted and reinstalled trying both unichrome drivers and via drivers in different orders fomatting and reinstalling and trying all possible configurations in xorg.conf.  Nothing seemed to do anything to fix the resolution.

So I saw next to xorg.conf in the /etc/x11 folder was a file called default-display-manager which pointed to /usr/bin/gdm - gnome display manager.  Naturally my first instinct was to delete the default-display-manager file.

Afterwards all was good, my resolution displays at 1280x768.  Strange a single line file could cause so much trouble.

I would like to add that comments on alternate methods or why I should not have done that are welcome so maybe I can learn something new.

---

### Post by pi/roman on 2010-01-13
Decided to try the game VegaStrike and found that my laptop would lock up before it even loaded.  So I tried installing the proprietary VIA drivers and must have screwed it up because the resolution reverted back to the original problem.  Reinstalled the openchrome drivers and still no go, so I started piecing together a new xorg.conf to get back up by using some from alternate distros I had tried and also from the internet.  This one got me back up so it may help someone with an old Gateway laptop running on a VIA graphics chip:

```
Section "ServerLayout"
        Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
  Load         "dri"
  Load         "glx"
  Load         "dbe"
  Load         "extmod"
  Load         "dri2"
  Load         "record"
EndSection

Section "device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "PrintVGARegs"           # [<bool>]
        #Option     "PrintTVRegs"            # [<bool>]
        #Option     "I2CScan"                # [<bool>]
        #Option     "VBEModes"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "ExaNoComposite"         # [<bool>]
        #Option     "ExaScratchSize"         # <i>
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoRAM"               # <i>
        #Option     "ActiveDevice"           # [<str>]
        #Option     "BusWidth"               # [<str>]
        #Option     "Center"                 # [<bool>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForcePanel"             # [<bool>]
        #Option     "TVDotCrawl"             # [<bool>]
        #Option     "TVDeflicker"            # <i>
        #Option     "TVType"                 # [<str>]
        #Option     "TVOutput"               # [<str>]
        #Option     "DisableVQ"              # [<bool>]
        #Option     "DisableIRQ"             # [<bool>]
        #Option     "EnableAGPDMA"           # [<bool>]
        #Option     "NoAGPFor2D"             # [<bool>]
        #Option     "NoXVDMA"                # [<bool>]
        #Option     "VbeSaveRestore"         # [<bool>]
        #Option     "DisableXvBWCheck"       # [<bool>]
        #Option     "MaxDRIMem"              # <i>
        #Option     "AGPMem"                 # <i>
    Identifier   "card0"
    VendorName   "VIA Technologies, Inc."
    Boardname    "S3 Unichrome Pro"
    Busid        "PCI:1:0:0"
    Driver "openchrome"
    Option "Monitor-LVDS"  "Integrated LCD"
    Option "PanelSize" "1280x768"
    Option "SWcursor"
    Option "EnableAGPDMA" "True" 
    Option "VBEModes"  "True"
EndSection

Section "monitor" 
    Identifier    "monitor0"
    Vendorname    "Gateway"
    Modelname    "SAMSUNG LCD MONITOR"
      Option       "DPMS"
      Option       "PreferredMode" "1280x768"
     DisplaySize  305 183
     HorizSync    30-62
     VertRefresh 43-60
    UseModes     "Modes0"
    Gamma    1.0
EndSection

Section "Modes"
  Identifier   "Modes0"
    Modeline "1280x768"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
    Modeline "800x480"  29.58  800 816 896 992  480 481 484 497  -HSync +Vsync
EndSection

Section "screen" 
    Identifier    "screen0"
    Device        "card0"
    Monitor       "monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 16
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 15
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 8
        Modes "1280x768" "800x480"
    EndSubsection
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection
```

So I tried VegaStrike again to see if I could get it to lock up.. yep, soon as I booted it up.  Checked my openGL by running glxinfo and "glxinfo | grep rendering" and it was there but it seemed to have some errors finding some libraries.  So I reinstalled the 2 openGL mesa packs: libgl1-mesa-glx and libgl1-mesa-dri and I was still getting an error.  Then I downloaded and ran driconf which fixed the problems and now the game looks like it should run well although with some clipping.

The only problems I have left to figure out are that my lower resolutions still do not display properly and lower widescreen resolutions are not even available for selection although I doubt I will need lower resolutions.

---

