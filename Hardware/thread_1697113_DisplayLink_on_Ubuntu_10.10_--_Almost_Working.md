---
title: "DisplayLink on Ubuntu 10.10 -- Almost Working"
date: 2011-02-28
forum: Hardware
---

### Post by omizzle on 2011-02-28
hi all,

so, i got my DisplayLink 2nd monitor almost working. right now, i see the "ubuntu" logo and the 5 red dots on the DisplayLink monitor, but i am at a loss for how to actually interact with that monitor. i suspect there's something missing in my xorg.conf to get a second desktop loaded on the DisplayLink monitor, but i've tried all kinds of things and i'll be damned. right now, while it'd be nice to get xinerama working, i just want the second monitor accessible. here's my dirt simple xorg.conf:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "DisplayLinkScreen" 0 0
	Screen      1  "Screen0" RightOf "DisplayLinkScreen"
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
EndSection

############### DisplayLink Stuff ###############                                                                 

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
EndSection

any thoughts appreciated.

---

### Post by altometer on 2011-02-28
I got the same thing. When contacting Display link, they only say that they do not officially support using their devices on ubuntu.

---

### Post by omizzle on 2011-02-28
blah i feel so close! i can control-alt-f1 etc.. into a terminal on that monitor, but getting X going on it is proving difficult. i'll keep thwacking at it.

---

### Post by altometer on 2011-03-01
let me know if you get anywhere, I would love to use 3 monitors again :)

---

### Post by semidark on 2011-05-29
Same thing here. Did you make any progress on this?
Got to the ubuntu Logo on my Displaylink Screen:

Here is my xorg.conf:
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


```I found this threat: [http://ubuntuforums.org/showthread.php?t=1597230](http://ubuntuforums.org/showthread.php?t=1597230)

ml1969 writes he got it working. Will ask him how he did it. We must be missing something.

Greetz semidark

---

### Post by Ulysses on 2011-06-01
Hello,

I'm having precisely the same problem!
I've already posted in another thread about this same thing!

I tried with Ubuntu 10.04, Ubuntu 10.10, and finally with 11.04 (I installed each one after the other, upgrading as I went). Nothing works. I got as far as the Ubuntu and 5 dots and that is it.

I now have installed Windows 7 (blech!) and am trying to see how the Displaylink works with that - and it works as a third monitor seamlessly.
I'm downloading 11.04 to do it as a fresh install and see how that works.

But, I am going to check this thread if you have any updates at all. Post me a hint, at the very least.

RAR

---

### Post by semidark on 2011-06-02
Yes!!! Got my displaylink Device running in Ubuntu Maverick 10.10

I commented my build-in Display in my xorg.conf and now I got my External Display up and running :guitar:
So my serverlayout section now looks like this:

```
Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice    "Mouse0" "CorePointer"

    InputDevice    "Keyboard0" "CoreKeyboard"

    #Screen  1       "Screen0" Below "Screen0" 
    Screen  0       "DisplayLinkScreen" 0 0 
    Option          "Xinerama" "off"
EndSection

```No Compiz and no Dualscreen. But at the moment i don't mind ;)

Greetz Semidark

---

### Post by khoaofgod on 2012-10-08
I got same problem on Ubuntu 12.
My 3RD Monitor show Ubuntu Logo and 5 dots only. 


```
Section "ServerLayout"
    Identifier     "X.org Configured"


    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Screen      0  "DisplayLinkScreen"
    Screen      1  "aticonfig-Screen[0]-0" Rightof "DisplayLinkScreen"
    Option          "Xinerama" "off"
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
    Load  "glx"
    Load  "dri2"
    Load  "dbe"
    Load  "dri"
    Load  "record"
    Load  "extmod"
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
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "DisplayLinkMonitor"

    Option      "DPMS" "true"
    Option      "PreferredMode" "1920x1080"
    Option      "TargetRefresh" "60"
    Option      "Rotate" "normal"
    Option      "Disable" "false"

EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"
    Identifier  "DisplayLinkDevice"
    Driver      "displaylink"
    Option        "fbdev" "/dev/fb1"
    Option "ShadowFB" "off"
    Option      "DisplayLinkMonitor"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3600 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "DisplayLinkScreen"
    Device     "DisplayLinkDevice"
    Monitor    "DisplayLinkMonitor"
    DefaultDepth     24
    SubSection "Display"        
        Depth     24
        Modes    "1920x1080"
    EndSubSection
EndSection

```

---

### Post by overdrank on 2012-10-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

