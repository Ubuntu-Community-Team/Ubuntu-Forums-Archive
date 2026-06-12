---
title: "Switching Modes"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by walding on 2006-06-26
Hi,

I have an Asus A6VM laptop running Kubuntu.  I have nvidia with TwinView clone setup.  For the record (it might be linked) I have KMilo disabled as it throws up unwanted alerts.

My problem is that I have a 1280x800 resolution laptop screen.  However, when giving a presentation, I want to be able to switch modes to offer the projector output at a different resolution.  I have set up my xorg.conf file to allow for different modes, like this:

Section "Device"
...
Option "MetaModes" "1280x800, 1280x800; 1200x768, 1200x768; 1280x800, 1200x768"

BUt I don't know who to switch modes!  My Fn-7 option doesn't do anything (even though *some* of the Fn-x options do work).

Can I configure a hotkey or Fn-x option to switchmodes?  I've searched for wikis or HowTos to no avail.  Any help appreciated.

Cheers

AW

---

### Post by tonyr on 2006-06-26
Does **Kmenu->System Settings->Display** offer any resolution control?

---

### Post by walding on 2006-06-26
Ah - here I have a problem (I've not been there before).  I get the following error when I select that:

"The MOdule Display could not be loaded.

The diagnostics is:
Possible reasons:
- An error occurred during you last KDE upgrade leaving an orphaned control module
- You have old third party modules lying around.
Check these points carefully and try to remove the module mentioned in the error message. If this fails, consider contacting your distributor or packager."

I have the nvidia driver installed - could that be an issue?

---

### Post by tonyr on 2006-06-26
It could be, but I don't think so (Caveat: I'm no expert, just a guy). You could
try changing the driver in your xorg.conf from **nvidia** back to **nv**
to see if that changes any of the behavior when selecting Display.  When was the
last time you updated you Kubuntu installation?

---

### Post by wolframarnold on 2007-01-05
I found two weird problems with kubuntu 6.10 (Edgy) and TwinView:

[LIST=1]
[*]I read all the info on how to configure TwinView.  Helpful in particular was: [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html]("http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html")
When I use multiple Metamodes, such as:
```

Option "Metamodes" "1280x1024,1280x1024; 800x600,800x600; 640x480,640x480; 1280x1024,NULL; 800x600,NULL; 640x480,NULL"

```
then the server would initialize with the highest mode, as per log file:
```

(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"

```
and the login screen would show across both monitors.  The minute I log in, however, the second display would go dark and the log file would say:
```

(II) NVIDIA(0): Setting mode "1280x1024,NULL"

```
In all cases the KDE Display configuration tool would only show 1280x1024 as highest resolution.  I was expecting 2540x1024 as highest.

I experimented with the "NoTwinViewXineramaInfo" option but to no avail. Playing with adding the 2nd display under KDE also did not help.
[*]Lastly, I removed all Metamodes, except for the highest one, "1280x1024,1280x1024".  That forced KDE into the highest mode, but now the Display configuration tool will no longer launch, instead showing only the error message that walding posted:
> 
The Module Display could not be loaded.
...

[/LIST]
Listing only the highest Metamode does seem to produce properly functioning twin displays; I can drag windows across, etc. and KDE seems to be happy up to the config tool.  The pertinent sections of my final xorg.conf look like this:

```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV44 [Quadro NVS 285]"
        Driver          "nvidia"
        VendorName      "NVIDIA"
        BoardName       "NVIDIA Quadro NVS 285"
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "2"
        Option          "CursorShadow" "1"
        Option          "Coolbits" "1"
        Option          "NoPowerConnectorCheck"
        Option          "TwinView" "True"
        Option          "Metamodes" "1280x1024,1280x1024"
        Screen          0
        Option          "SecondMonitorHorizSync" "UseEdidFreqs"
        Option          "SecondMonitorVertRefresh" "UseEdidFreqs"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV44 [Quadro NVS 285]"
        Monitor         "DELL 1907FP"
        DefaultDepth    24
        SubSection "Display"
                Viewport        0 0
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport        0 0
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport        0 0
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport        0 0
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport        0 0
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "TwinView Configuration"
        Screen          0 "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama" "Off"
EndSection

```

---

