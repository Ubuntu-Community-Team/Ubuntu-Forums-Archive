---
title: "Matrox G450 Dual Head"
date: 2010-07-09
forum: Hardware
---

### Post by Curly Drew on 2010-07-09
I have a Matrox g450 with dual VGA out, currently I am only able to get the two screens to display the same thing, the default setting. I have found forum posts that describe how to get dual head on previous versions of Ubuntu ([http://ubuntuforums.org/showthread.php?t=374611](http://ubuntuforums.org/showthread.php?t=374611)) however I am unable to make the advised changes work (I am unsure as to whether I am doing something incorrectly or if it is a version issue).

Firstly I have generated the following xorg.conf running Xorg -configure

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "record"
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
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA G400/G450"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```This xorg.conf works as it should (i.e. in mirror mode). I then modified it to have a second entry for another monitor, shown below;

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option    "Xinerama" "true"
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
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "record"
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
    DisplaySize      300   240    # mm
    Identifier   "Monitor0"
    Option         "PreferredMode"  "1024x768"
    Option        "DPMS"
EndSection

Section "Monitor"
    DisplaySize      300   240    # mm
    Identifier   "Monitor1"
    Option         "PreferredMode"  "1024x768"
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0 Primary"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA G400/G450"
    BusID       "PCI:1:0:0"
    Option "OldDmaInit" "True"
    Screen 0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0 Secondary"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA G400/G450"
    BusID       "PCI:1:0:0"
    Option "OldDmaInit" "True"
    Screen 1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0 Primary"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card0 Secondary"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

```This xorg.config does not work, however removing one of the lines of the server layout (as below), allows it to work in the default "mirror mode";

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    #Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option    "Xinerama" "true"
EndSection

```Changing the ServerLayout section to read as follows (i.e. using "screen1" instead of "screen0") also fails; 

```

 Section "ServerLayout"
     Identifier     "X.org Configured"
     Screen      1  "Screen1" 0 0
     InputDevice    "Mouse0" "CorePointer"
     InputDevice    "Keyboard0" "CoreKeyboard"
     Option    "Xinerama" "true"
 EndSection

```I am unsure as to how to proceed, the two entries are the same apart from identifiers but behave differently. Any advice would be welcome,
Thanks in advance,
Drew

---

### Post by necomo_j on 2010-07-29
I have the same problem. The mga driver is installed by default but the monitor detection utility under monitor preferences only detects one monitor and thats a bit symptomatic...

Did you allready find a workaround on this issue?

---

### Post by Steelkilt on 2010-08-30
Count me in too.  Same problem.  Same Matrox G450 card.  Unlike your situation, I do not even have an xorg.conf file in my etc/X11 directory.  I was planning to create one, but based on your experience, that may not work.  Are you running 10.04?

---

### Post by Steelkilt on 2010-09-01
Drew,

Did you generate the Xorg.conf file by running the command "-configure" ?  Is that the magical command?  Do you have to be in the etc/X11 directory to run that command?

I can't see the problem with what you did.  It's consistent with what I have read.  But, I have no idea what I am doing.

Doesn't stop me.

Thanks.

---

### Post by Steelkilt on 2010-09-02
I am now up to where Drew was.  I generated an Xorg.cong file using the instructions at:


[http://www.osguides.net/operation-sy...buntu-910.html]("http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html") 		                   		  		  		 		 			 				

I made most of Drew's edits and a few from the Maxtor site.  The monitors work in mirror mode, but not side-by-side yet.

JG

---

