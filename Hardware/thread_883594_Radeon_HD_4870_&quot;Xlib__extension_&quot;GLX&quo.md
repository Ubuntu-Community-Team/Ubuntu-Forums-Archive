---
title: "Radeon HD 4870 &quot;Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;.&quot;"
date: 2008-08-08
forum: Hardware
---

### Post by Ubuntiac on 2008-08-08
Howdy all,

I just installed the drivers for this using the guide here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Only changing --buildpkg Ubuntu/Gutsy to --buildpkg Ubuntu/8.04 (as I'm on Hardy)

.Debs were all created and installed with no errors. Xorg has:

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Option      "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "XAANoOffscreenPixmaps" "on"
        Option      "TexturedVideo" "off"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "off"
        Option      "Textured2D" "on"
        Option      "UseFastTLS" "1"
        Option      "BackingStore" "on"
        BusID       "PCI:1:0:0"
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

Section "DRI"
        Group        "Video"
        Mode         0666
EndSection

Section "Extensions"
        Option      "RENDER" "Enable"
        Option      "DAMAGE" "Enable"
        Option      "Composite" "Enable"
EndSection


```


Yet when I do fglrxinfo I get:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Yet when I do fglrxinfo I get:
> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!


and Xorg.0.log shows:
> (EE) fglrx: Failed to load module "glx" (module does not exist, 0)
(EE) fglrx(0): Failed to load GLX module.

(EE) fglrx(0): XMM failed to open CMMQS connection.


Does anyone have any ideas?

Thanks!


**SOLVED!**

Installing and uninstalling a mix of official Ubuntu drivers and unofficial .run files from ATI / Nvidia had deleted some important files and left other garbage modules screwing things up.

I ended up reinstalling Kubuntu but quickly discovered that if you only install the .run file automatically from ATI, **it will work at first, but die when you upgrade the kernel / restricted modules**.

To get it working silky smooth (with 3d) even with upgrades, please, please save yourself the time and first check if the 48XX is supported yet in EnvyNG by:

installing and running EnvyNG, choosing the ATI tab, selecting "Automatic" and clicking next.

If it says your hardware isn't supported (which is what it does at the time of writing this) follow this guide **carefully**:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29)

The difference between this guide and the many others out there is that it correctly works with ubuntu's package / update system.

Oh yeah, and adding Option "composite" "true" in your /etc/X11/xorg.conf under "screen" seems to help, too.

Enjoy!

---

