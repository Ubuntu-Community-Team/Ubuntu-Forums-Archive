---
title: "NVidia Dual CRT / TV out - Brain Melting"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by danimal72 on 2006-04-02
Hi Folks,

I've been trying to do this for a couple days now... I've been through dozens of forums, TUTs and recommendations but to no avail so far.

My goal is to have a CRT and TV output - Specifically for MythTV. I'd ideally like MythTV to run on the TV (shocker, eh?) and a desktop to run on the CRT. I can get the CRT to work /or/ the TV, but not both. Here are some details:

Motherboard and CPU:
SIS Chipset, Duron 1200, 512M DDR

Graphics Card:
Nvidia Geforce 4 MX 440, 64M (NV18)

Monitor:
Korea Data Systems; KDS Visual Sensations VS-190p; STC0812; 30.0-96.0; 50.0-160.0

OS:
Ubuntu 5.1, Updated as usual
*and*
apt-get install nvidia-glx nvidia-settings

xorg.0.log Version Info:
 sudo grep 'version' /var/log/Xorg.0.log

        to make sure that you have the latest version.
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:13:17 UTC 2006 T
(II) Module ABI versions:
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Font Renderer, version 0.4
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
        compiled for 6.8.2, module version = 2.1.0
        ABI class: X.Org Font Renderer, version 0.4
        compiled for 4.0.2, module version = 1.0.7667
        ABI class: XFree86 Server Extension, version 0.1
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
        compiled for 6.8.2, module version = 1.0.2
        ABI class: X.Org Font Renderer, version 0.4
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
        compiled for 4.0.2, module version = 1.0.7667
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org XInput driver, version 0.4
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org XInput driver, version 0.4
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7


xorg.conf (Works for TV only)
----------------------------------------------------
//SNIP//
Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
//SNIP// (you don't really want to see my Keyboard/mouse settings, do you?)
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        VendorName      "Dans Video"
        BoardName       "Nvidia GeForce4 440MX"
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "2"
        Option          "NoLogo" "0"
        Option          "RenderAccel" "1"
        Option          "CursorShadow" "1"
        Option          "Coolbits" "1"
        Option          "ConnectedMonitor" "crt, tv"
        Option          "NoPowerConnectorCheck"
        Option          "TwinView" "1"
        Option          "Metamodes" "640x480,640x480;"
#        Option          "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL; 800x600,800x600; 640x480,640x480;"
        Option          "SecondMonitorHorizSync" "31-82"
        Option          "SecondMonitorVertRefresh" "56-76"
        Option          "NoTwinViewXineramaInfo"
        Option          "TwinViewOrientation" "Clone"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Viewport 0 0
                Depth 24
                Modes "640x480"
#               Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "TwinView Configuration"
        Screen 0 "Default Screen" 0 0
        InputDevice "Configured Mouse"
        InputDevice "Generic Keyboard"
        Option "Xinerama" "On"
EndSection

Section "DRI"
        Mode    0666
EndSection

----------------------------------------------------
sudo grep 'WW' /var/log/Xorg.0.log

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0

----------------------------------------------------
sudo grep 'EE' /var/log/Xorg.0.log

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


So, The above puts a desktop on the TV.. So I know the TV works, anyway.

The following config gives me a normal desktop, but nada for the TV:
----------------------------------------------------
//SNIP//
Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
//SNIP// (keyboard/mouse)
Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen          0
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "2"
        Option          "NoLogo" "0"
        Option          "RenderAccel" "1"
        Option          "CursorShadow" "1"
        Option          "Coolbits" "1"
        Option          "NoPowerConnectorCheck"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver          "nvidia"
        Screen          1
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Monitor"
        Identifier      "TeleVision"
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Identifier "Screen0"
        Device "Device0"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
#               Modes "640x480"
                Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "TeleVision"
        DefaultDepth    24
        Option          "TVOutFormat" "SVIDEO"
        OPtion          "TVStandard" "NTSC-M"
        Option          "ConnectedMonitor" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Basic Layout"
        Screen 0 "Screen0"
        Screen 1 "Screen1" rightof "Screen0"
        InputDevice "Configured Mouse"
        InputDevice "Generic Keyboard"
EndSection

Section "DRI"
        Mode    0666
EndSection
----------------------------------------------------
 sudo grep 'WW' /var/log/Xorg.0.log

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 210MHz
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 210MHz
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 210MHz
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 210MHz
(WW) NVIDIA(0): Not using mode "1024x768" (height 1536 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "960x720" (height 1440 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "928x696" (height 1392 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "896x672" (height 1344 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8

----------------------------------------------------

 sudo grep 'EE' /var/log/Xorg.0.log

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) NVIDIA(1): The requested configuration of display devices is not
(EE) NVIDIA(1):      supported in the hardware.

----------------------------------------------------


Please help save my brain from total meltdown....

---

### Post by danimal72 on 2006-04-04
**bump**

I'm sure there is someone here that can help me. Please?

Not even getting any love from the nvnews forum **sigh**

---

