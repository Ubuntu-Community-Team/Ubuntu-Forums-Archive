---
title: "3D accelaration with Poulsbo GMA500 through EMGD"
date: 2013-01-22
forum: Hardware
---

### Post by neokod on 2013-01-22
Hello, 

I need the 3D support on my Acer Aspire One AO751h laptop.

I have found an easy way to install EMGD 1.16 on this help page of Fit-PC2 computers :
[http://www.fit-pc.com/wiki/index.php/Linux_Mint_13_on_fit-PC2](http://www.fit-pc.com/wiki/index.php/Linux_Mint_13_on_fit-PC2)

I known it's for Fit-PC2 on Linux Mint 13, but as Linux Mint is based on Ubuntu, this should works for us too !

This page include DEB packages and explications to downgrade to Xorg 1.9.

I would like to known if someone have already tried with this method ? 
(the old method was the PPA of the GMA500 team, but this method doesn't works anymore)

And if someone have used this method, I would like to known if he could help me :-)

So, I have downgrade xorg, and used your deb packages. I have blacklisted psb/gma500 modules, and added a redirection script for X (because of the "-background" option renamed "-nr").

I have found the exact resolution parameters (for the native 1366x768 resolution), and I have no errors (EE), warnings (WW), failed messages or others problems in the logs.

But, strangly, I still have a blank screen .... :(


Here is my xorg.conf :
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen          "Screen0"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
#       Modeline "1366x768x60"  72.30  1366 1413 1445 1525  768 770 775 789 -HSync +VSync
#       HorizSync       60
#       VertRefresh     60
#       Option          "DPMS"
EndSection

Section "Device"
    Identifier "Card0"
    Driver     "emgd"
    VendorName "Intel(R) DEG"
    BoardName  "Embedded Graphics"
    BusID      "0:2:0"
    Screen      0
    Option     "PcfVersion"            "1792"
    Option     "ConfigId"              "1"
    Option     "ALL/1/name"                   "LVDS"
    Option     "ALL/1/General/PortOrder"      "40000"
    Option     "ALL/1/General/DisplayConfig"  "1"
    Option     "ALL/1/General/DisplayDetect"  "1"
    Option     "ALL/1/General/swcursor"       "0"
    Option     "ALL/1/General/Accel"          "1"
    Option     "ALL/1/General/shadowfb"       "1"
    Option     "ALL/1/General/tearfb"         "0"
    Option     "ALL/1/General/xVideo"         "1"
    Option     "ALL/1/General/XVideoBlend"    "0"
    Option     "ALL/1/General/DRI"            "1"
    Option     "ALL/1/General/DRI2"             "1"
    Option     "ALL/1/General/Refresh"    "60"
    Option     "ALL/1/General/EnableRegOverride" "1"
    Option     "ALL/1/General/DispARB"           "0x00003232"
    Option     "ALL/1/Port/4/General/name"           "LVDS"
    Option     "ALL/1/Port/4/General/EdidAvail"      "0"
    Option     "ALL/1/Port/4/General/EdidNotAvail"   "5"
    Option     "ALL/1/Port/4/General/Rotation"       "0"
    Option     "ALL/1/Port/4/General/Edid"           "0"
    Option     "ALL/1/Port/4/General/CenterOff"      "1"
    Option     "ALL/1/Port/4/General/MultiDvo"       "0"
    Option     "ALL/1/Port/4/FpInfo/BkltMethod"      "1"
    Option     "ALL/1/Port/4/FpInfo/BkltT1"          "60"
    Option     "ALL/1/Port/4/FpInfo/BkltT2"          "200"
    Option     "ALL/1/Port/4/FpInfo/BkltT3"          "200"
    Option     "ALL/1/Port/4/FpInfo/BkltT4"          "50"
    Option     "ALL/1/Port/4/FpInfo/BkltT5"          "400"
    Option     "ALL/1/Port/4/Dtd/1/PixelClock"       "54720" #"72300"
    Option     "ALL/1/Port/4/Dtd/1/HorzActive"       "1366"
    Option     "ALL/1/Port/4/Dtd/1/HorzSync"         "230" #"48"
    Option     "ALL/1/Port/4/Dtd/1/HorzSyncPulse"    "16" #"32"
    Option     "ALL/1/Port/4/Dtd/1/HorzBlank"        "476" #"160"
    Option     "ALL/1/Port/4/Dtd/1/VertActive"       "768"
    Option     "ALL/1/Port/4/Dtd/1/VertSync"         "4" #"3"
    Option     "ALL/1/Port/4/Dtd/1/VertSyncPulse"    "1" #"5"
    Option     "ALL/1/Port/4/Dtd/1/VertBlank"        "8" #"22"
    Option     "ALL/1/Port/4/Dtd/1/Flags"            "0x20000"
    Option     "ALL/1/Port/4/Attr/27"    "0"
    Option     "ALL/1/Port/4/Attr/26"    "24"
    Option     "ALL/1/Port/4/Attr/18"    "1"
    Option     "ALL/1/Port/4/Attr/60"    "1"
    Option     "PortDrivers" "lvds"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth  24 
        SubSection "Display"
                Modes     "1366x768" "1280x1024" "1024x768" "800x600"
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Group 0
        Mode 0666
EndSection

Section "Extensions"
        Option  "Composite" "enable"
EndSection


Section "ServerFlags"
        Option "GlxVisuals" "all"
#       Option "IgnoreABI" "true"
        Option "AIGLX" "true"
        Option "DRM" "true"
        Option "Xinerama" "false"
EndSection

```

The Xorg.0.log :
```

[  6601.786]
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  6601.786] X Protocol Version 11, Revision 0
[  6601.786] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  6601.786] Current Operating System: Linux one 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686
[  6601.786] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-21-generic root=/dev/mapper/ubuntu-root ro quiet acpi_backlight=vendor acpi_osi=Linux mem=896mb
[  6601.786] Build Date: 20 October 2011  03:03:54PM
[  6601.786] xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see http://www.ubuntu.com/support)
[  6601.786] Current version of pixman: 0.26.0
[  6601.786]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[  6601.786] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  6601.787] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 22 13:29:34 2013
[  6601.787] (==) Using config file: "/etc/X11/xorg.conf"
[  6601.787] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  6601.789] (==) ServerLayout "X.org Configured"
[  6601.789] (**) |-->Screen "Screen0" (0)
[  6601.789] (**) |   |-->Monitor "Monitor0"
[  6601.790] (**) |   |-->Device "Card0"
[  6601.790] (**) Option "Xinerama" "false"
[  6601.790] (**) Option "AIGLX" "true"
[  6601.790] (**) Option "GlxVisuals" "all"
[  6601.790] (==) Automatically adding devices
[  6601.790] (==) Automatically enabling devices
[  6601.790] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[  6601.790]    Entry deleted from font path.
[  6601.790]    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[  6601.791] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        built-ins
[  6601.791] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  6601.791] (**) Extension "Composite" is enabled
[  6601.791] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[  6601.791] (II) Loader magic: 0x81f8e00
[  6601.791] (II) Module ABI versions:
[  6601.791]    X.Org ANSI C Emulation: 0.4
[  6601.791]    X.Org Video Driver: 8.0
[  6601.791]    X.Org XInput driver : 11.0
[  6601.791]    X.Org Server Extension : 4.0
[  6601.792] (--) PCI:*(0:0:2:0) 8086:8108:1025:0244 rev 7, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0000000/262144, I/O @ 0x00001800/8
[  6601.793] (II) Open ACPI successful (/var/run/acpid.socket)
[  6601.793] (II) LoadModule: "extmod"
[  6601.794] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  6601.795] (II) Module extmod: vendor="X.Org Foundation"
[  6601.795]    compiled for 1.9.0, module version = 1.0.0
[  6601.795]    Module class: X.Org Server Extension
[  6601.795]    ABI class: X.Org Server Extension, version 4.0
[  6601.795] (II) Loading extension MIT-SCREEN-SAVER
[  6601.795] (II) Loading extension XFree86-VidModeExtension
[  6601.795] (II) Loading extension XFree86-DGA
[  6601.795] (II) Loading extension DPMS
[  6601.795] (II) Loading extension XVideo
[  6601.795] (II) Loading extension XVideo-MotionCompensation
[  6601.795] (II) Loading extension X-Resource
[  6601.795] (II) LoadModule: "dbe"
[  6601.796] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  6601.796] (II) Module dbe: vendor="X.Org Foundation"
[  6601.796]    compiled for 1.9.0, module version = 1.0.0
[  6601.797]    Module class: X.Org Server Extension
[  6601.797]    ABI class: X.Org Server Extension, version 4.0
[  6601.797] (II) Loading extension DOUBLE-BUFFER
[  6601.797] (II) LoadModule: "glx"
[  6601.797] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  6601.798] (II) Module glx: vendor="X.Org Foundation"
[  6601.798]    compiled for 1.9.0, module version = 1.0.0
[  6601.798]    ABI class: X.Org Server Extension, version 4.0
[  6601.798] (**) AIGLX enabled
[  6601.798] (II) Loading extension GLX
[  6601.798] (II) LoadModule: "record"
[  6601.799] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  6601.799] (II) Module record: vendor="X.Org Foundation"
[  6601.799]    compiled for 1.9.0, module version = 1.13.0
[  6601.799]    Module class: X.Org Server Extension
[  6601.799]    ABI class: X.Org Server Extension, version 4.0
[  6601.799] (II) Loading extension RECORD
[  6601.799] (II) LoadModule: "dri"
[  6601.800] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  6601.800] (II) Module dri: vendor="X.Org Foundation"
[  6601.801]    compiled for 1.9.0, module version = 1.0.0
[  6601.801]    ABI class: X.Org Server Extension, version 4.0
[  6601.801] (II) Loading extension XFree86-DRI
[  6601.801] (II) LoadModule: "dri2"
[  6601.801] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  6601.802] (II) Module dri2: vendor="X.Org Foundation"
[  6601.802]    compiled for 1.9.0, module version = 1.2.0
[  6601.802]    ABI class: X.Org Server Extension, version 4.0
[  6601.802] (II) Loading extension DRI2
[  6601.802] (II) LoadModule: "emgd"
[  6601.802] (II) Loading /usr/lib/xorg/modules/drivers/emgd_drv.so
[  6601.803] (II) Module emgd: vendor="Intel(R) Corporation"
[  6601.803]    compiled for 1.9.0, module version = 1.16.3196
[  6601.803]    Module class: X.Org Video Driver
[  6601.803]    ABI class: X.Org Video Driver, version 8.0
[  6601.803] (II) EMGD: Intel(R) Embedded Media and Graphics Driver version 1.16.3196 for:
        Intel US15W Class
[  6601.803] (++) using VT number 7

[  6601.804] (==) EMGD(0): RGB weight 888
[  6601.804] (==) EMGD(0): Default visual is TrueColor
[  6601.805] drmOpenDevice: node name is /dev/dri/card0
[  6601.805] drmOpenDevice: open result is 9, (OK)
[  6601.805] drmOpenByBusid: Searching for BusID PCI:00:00:00
[  6601.805] drmOpenDevice: node name is /dev/dri/card0
[  6601.805] drmOpenDevice: open result is 9, (OK)
[  6601.805] drmOpenByBusid: drmOpenMinor returns 9
[  6601.805] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6601.805] drmOpenDevice: node name is /dev/dri/card1
[  6601.812] drmOpenByBusid: drmOpenMinor returns -1
[  6601.812] drmOpenDevice: node name is /dev/dri/card2
[  6601.818] drmOpenByBusid: drmOpenMinor returns -1
[  6601.818] drmOpenDevice: node name is /dev/dri/card3
[  6601.825] drmOpenByBusid: drmOpenMinor returns -1
[  6601.825] drmOpenDevice: node name is /dev/dri/card4
[  6601.831] drmOpenByBusid: drmOpenMinor returns -1
[  6601.831] drmOpenDevice: node name is /dev/dri/card5
[  6601.838] drmOpenByBusid: drmOpenMinor returns -1
[  6601.838] drmOpenDevice: node name is /dev/dri/card6
[  6601.844] drmOpenByBusid: drmOpenMinor returns -1
[  6601.844] drmOpenDevice: node name is /dev/dri/card7
[  6601.850] drmOpenByBusid: drmOpenMinor returns -1
[  6601.851] drmOpenDevice: node name is /dev/dri/card8
[  6601.857] drmOpenByBusid: drmOpenMinor returns -1
[  6601.857] drmOpenDevice: node name is /dev/dri/card9
[  6601.864] drmOpenByBusid: drmOpenMinor returns -1
[  6601.864] drmOpenDevice: node name is /dev/dri/card10
[  6601.870] drmOpenByBusid: drmOpenMinor returns -1
[  6601.870] drmOpenDevice: node name is /dev/dri/card11
[  6601.876] drmOpenByBusid: drmOpenMinor returns -1
[  6601.876] drmOpenDevice: node name is /dev/dri/card12
[  6601.883] drmOpenByBusid: drmOpenMinor returns -1
[  6601.883] drmOpenDevice: node name is /dev/dri/card13
[  6601.889] drmOpenByBusid: drmOpenMinor returns -1
[  6601.890] drmOpenDevice: node name is /dev/dri/card14
[  6601.896] drmOpenByBusid: drmOpenMinor returns -1
[  6601.896] drmOpenDevice: node name is /dev/dri/card15
[  6601.903] drmOpenByBusid: drmOpenMinor returns -1
[  6601.903] drmOpenDevice: node name is /dev/dri/card0
[  6601.903] drmOpenDevice: open result is 9, (OK)
[  6601.903] drmOpenDevice: node name is /dev/dri/card0
[  6601.903] drmOpenDevice: open result is 9, (OK)
[  6601.903] drmGetBusid returned ''
[  6601.903] (II) EMGD(0): Chipset: "Intel SCH US15 Chipset"
[  6601.904] (II) EMGD(0): Detected kernel module from EMGD build 3196
[  6601.904] (II) EMGD(0): Checking for new style options
[  6601.904] (II) EMGD(0): Processing version 7.0 options
[  6601.904] (II) EMGD(0): Using configuration 1
[  6601.904] (II) EMGD(0): Checking for US15 specific configuration.
[  6601.904] (II) EMGD(0): Checking for non-chipset specific configuration.
[  6601.904] (II) EMGD(0): Setting port_order to 40000
[  6601.905] (II) EMGD(0): Setting Enable Reg Override
[  6601.905] (II) EMGD(0): Setting Disp Arb
[  6601.905] (II) EMGD(0): Allocated local dtd for port=3 dtdid=1
[  6601.905] (II) EMGD(0): Option processing done!
[  6602.146] (II) EMGD(0): Valid Display Configurations:
[  6602.146] (II) EMGD(0):   DC: 0x00000041
[  6602.147] (II) EMGD(0):   DC: 0x00000000
[  6602.147] (II) EMGD(0): Using Display Configuration 0x00000041
[  6602.147] (**) EMGD(0): Depth 24, (--) framebuffer bpp 32
[  6602.147] (==) EMGD(0): Using gamma correction (1.0, 1.0, 1.0)
[  6602.147] (II) EMGD(0): 1 modes passed validation checks
[  6602.147] (--) EMGD(0): Virtual size is 1366x768 (pitch 0)
[  6602.147] (**) EMGD(0): *Built-in mode "1366x768": 54.7 MHz (scaled from 0.0 MHz), 29.7 kHz, 38.0 Hz
[  6602.148] (II) EMGD(0): Modeline "1366x768"x38.0   54.72  1366 1595 1611 1841  768 771 772 775 (29.7 kHz)
[  6602.148] (==) EMGD(0): DPI set to (96, 96)
[  6602.148] (II) Loading sub module "fb"
[  6602.148] (II) LoadModule: "fb"
[  6602.149] (II) Loading /usr/lib/xorg/modules/libfb.so
[  6602.150] (II) Module fb: vendor="X.Org Foundation"
[  6602.150]    compiled for 1.9.0, module version = 1.0.0
[  6602.150]    ABI class: X.Org ANSI C Emulation, version 0.4
[  6602.150] (II) EMGD(0): Rotation, Flip * RenderScale options do not support XVideo, XVideo Disabled.
[  6602.150] (II) Loading sub module "ramdac"
[  6602.150] (II) LoadModule: "ramdac"
[  6602.150] (II) Module "ramdac" already built-in
[  6602.150] (II) Loading sub module "shadowfb"
[  6602.150] (II) LoadModule: "shadowfb"
[  6602.151] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[  6602.152] (II) Module shadowfb: vendor="X.Org Foundation"
[  6602.152]    compiled for 1.9.0, module version = 1.0.0
[  6602.152]    ABI class: X.Org ANSI C Emulation, version 0.4
[  6602.152] (II) EMGD(0): General Driver Configuration Options
[  6602.152] (II) EMGD(0):   PCF Version:            7.00
[  6602.152] (II) EMGD(0):   Configuration ID:       1
[  6602.152] (II) EMGD(0): Primary Display Configuration Options
[  6602.152] (II) EMGD(0):   VideoRam (Pixmap Cache): 32768
[  6602.152] (II) EMGD(0):   PORT AND DISPLAY OPTIONS
[  6602.153] (II) EMGD(0):     Port Order:           40000
[  6602.153] (II) EMGD(0):     Display Config:       Single
[  6602.153] (II) EMGD(0):     Display Detect:       On
[  6602.153] (II) EMGD(0):     FB Blend Overlay:     Off
[  6602.153] (II) EMGD(0):     Gang DVO:             Off
[  6602.153] (II) EMGD(0):     Refresh Rate:         60
[  6602.153] (II) EMGD(0):     Clone Width:          0
[  6602.153] (II) EMGD(0):     Clone Height:         0
[  6602.153] (II) EMGD(0):     Clone Refresh:        0
[  6602.153] (II) EMGD(0):   FRAMEBUFFER OPTIONS
[  6602.153] (II) EMGD(0):     Shadow FB:            On
[  6602.153] (II) EMGD(0):     Tear FB:              Off
[  6602.154] (II) EMGD(0):     Resize:               Off
[  6602.154] (II) EMGD(0):    GL TEXTURE STREAM OUTPUT:         Off
[  6602.154] (II) EMGD(0):   FRAMEBUFFER ORIENTATION OPTIONS
[  6602.154] (II) EMGD(0):     Rotation:             0 degrees
[  6602.154] (II) EMGD(0):     Flip:                 Off
[  6602.154] (II) EMGD(0):   HARDWARE ACCELERATION OPTIONS
[  6602.154] (II) EMGD(0):     HW 2D Accel:          On
[  6602.154] (II) EMGD(0):     HW Cursor:            On
[  6602.154] (II) EMGD(0):   XVIDEO OPTIONS
[  6602.154] (II) EMGD(0):     XVideo:               Off
[  6602.154] (II) EMGD(0):     XVideoBlend:          Off
[  6602.154] (II) EMGD(0):     XVideoMC:             Off
[  6602.155] (II) EMGD(0):     XVideoKey:            0xff00ff00
[  6602.155] (II) EMGD(0):     Overlay Gamma Red:    0x100
[  6602.155] (II) EMGD(0):     Overlay Gamma Green:  0x100
[  6602.155] (II) EMGD(0):     Overlay Gamma Blue:   0x100
[  6602.155] (II) EMGD(0):     Overlay Brightness:   0x8000
[  6602.155] (II) EMGD(0):     Overlay Contrast:     0x8000
[  6602.155] (II) EMGD(0):     Overlay Saturation:   0x8000
[  6602.155] (II) EMGD(0):     DRI:                  On
[  6602.155] (II) EMGD(0):     DRI2:                 On
[  6602.155] (II) EMGD(0):     EDID:                 On
[  6602.155] (II) EMGD(0):   QUICKBOOT OPTIONS
[  6602.155] (II) EMGD(0):     QuickBoot:            1
[  6602.156] (II) EMGD(0):     Seamless:             Off
[  6602.156] (II) EMGD(0):     Video Input:          0
[  6602.156] (II) EMGD(0):     Splash Screen:        Off
[  6602.156] (II) EMGD(0):     Freeze FB:        Off
[  6602.156] (II) EMGD(0):    INTERRUPT OPTIONS
[  6602.156] (II) EMGD(0):      Polling:             Off
[  6602.156] (II) EMGD(0):   GLOBAL PER PORT OPTIONS
[  6602.156] (II) EMGD(0):   Port 2            (null)
[  6602.156] (II) EMGD(0):      Multi-DVO:      Off
[  6602.156] (II) EMGD(0):      Rotation:       0 degrees
[  6602.156] (II) EMGD(0):      Flip:           Off
[  6602.157] (II) EMGD(0):      Centering:      Off
[  6602.157] (II) EMGD(0):      RenderScale:    Off
[  6602.157] (II) EMGD(0):      EDID:           Off
[  6602.157] (II) EMGD(0):      EDID Avail:     0x5
[  6602.157] (II) EMGD(0):      EDID Not Avail: 0x5
[  6602.157] (II) EMGD(0):      PANEL INFORMATION
[  6602.157] (II) EMGD(0):         FP width:     0
[  6602.157] (II) EMGD(0):         FP height:    0
[  6602.157] (II) EMGD(0):         BKLT Enable:  0
[  6602.157] (II) EMGD(0):         BKLT Method:  0
[  6602.157] (II) EMGD(0):         BKLT T1:      0
[  6602.157] (II) EMGD(0):         BKLT T2:      0
[  6602.157] (II) EMGD(0):         BKLT T3:      0
[  6602.158] (II) EMGD(0):         BKLT T4:      0
[  6602.158] (II) EMGD(0):         BKLT T5:      0
[  6602.158] (II) EMGD(0):         GPIO Pin VDD: 0
[  6602.158] (II) EMGD(0):         GPIO Pin VEE: 0
[  6602.158] (II) EMGD(0):         GPIO Pin BKLT:0
[  6602.158] (II) EMGD(0):         DVO i2c pin:  0
[  6602.158] (II) EMGD(0):         DVO i2c DAB:  0
[  6602.158] (II) EMGD(0):         DVO i2c speed:0
[  6602.158] (II) EMGD(0):         DVO ddc pin:  0
[  6602.158] (II) EMGD(0):         DVO ddc speed:0
[  6602.158] (II) EMGD(0):      Number DTD's:   0
[  6602.158] (II) EMGD(0):      Number Attr's:  0
[  6602.159] (II) EMGD(0):   Port 4            LVDS
[  6602.159] (II) EMGD(0):      Multi-DVO:      Off
[  6602.159] (II) EMGD(0):      Rotation:       0 degrees
[  6602.159] (II) EMGD(0):      Flip:           Off
[  6602.159] (II) EMGD(0):      Centering:      Off
[  6602.159] (II) EMGD(0):      RenderScale:    On
[  6602.159] (II) EMGD(0):      EDID:           Off
[  6602.159] (II) EMGD(0):      EDID Avail:     0x0
[  6602.159] (II) EMGD(0):      EDID Not Avail: 0x5
[  6602.159] (II) EMGD(0):      PANEL INFORMATION
[  6602.159] (II) EMGD(0):         FP width:     0
[  6602.159] (II) EMGD(0):         FP height:    0
[  6602.160] (II) EMGD(0):         BKLT Enable:  0
[  6602.160] (II) EMGD(0):         BKLT Method:  1
[  6602.160] (II) EMGD(0):         BKLT T1:      60
[  6602.160] (II) EMGD(0):         BKLT T2:      200
[  6602.160] (II) EMGD(0):         BKLT T3:      200
[  6602.160] (II) EMGD(0):         BKLT T4:      50
[  6602.160] (II) EMGD(0):         BKLT T5:      400
[  6602.160] (II) EMGD(0):         GPIO Pin VDD: 0
[  6602.160] (II) EMGD(0):         GPIO Pin VEE: 0
[  6602.160] (II) EMGD(0):         GPIO Pin BKLT:0
[  6602.160] (II) EMGD(0):         DVO i2c pin:  0
[  6602.160] (II) EMGD(0):         DVO i2c DAB:  0
[  6602.160] (II) EMGD(0):         DVO i2c speed:0
[  6602.160] (II) EMGD(0):         DVO ddc pin:  0
[  6602.161] (II) EMGD(0):         DVO ddc speed:0
[  6602.161] (II) EMGD(0):      Number DTD's:   1
[  6602.161] (II) EMGD(0):        1-width:       1366
[  6602.161] (II) EMGD(0):        1-height:      768
[  6602.161] (II) EMGD(0):        1-refresh:     0
[  6602.161] (II) EMGD(0):        1-dclk:        54720
[  6602.161] (II) EMGD(0):        1-horz total:  0
[  6602.161] (II) EMGD(0):        1-horz b_start:1365
[  6602.161] (II) EMGD(0):        1-horz b_end:  1841
[  6602.161] (II) EMGD(0):        1-horz s_start:1595
[  6602.161] (II) EMGD(0):        1-horz s_end:  1611
[  6602.161] (II) EMGD(0):        1-vert total:  0
[  6602.161] (II) EMGD(0):        1-vert b_start:767
[  6602.161] (II) EMGD(0):        1-vert b_end:  775
[  6602.161] (II) EMGD(0):        1-vert s_start:771
[  6602.161] (II) EMGD(0):        1-vert s_end:  772
[  6602.161] (II) EMGD(0):        1-flags:       0x20000
[  6602.161] (II) EMGD(0):      Number Attr's:  4
[  6602.161] (==) Depth 24 pixmap format is 32 bpp
[  6602.548] drmOpenDevice: node name is /dev/dri/card0
[  6602.548] drmOpenDevice: open result is 10, (OK)
[  6602.549] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.549] drmOpenDevice: node name is /dev/dri/card0
[  6602.549] drmOpenDevice: open result is 10, (OK)
[  6602.549] drmOpenByBusid: drmOpenMinor returns 10
[  6602.549] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.550] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.550] drmOpenDevice: node name is /dev/dri/card0
[  6602.551] drmOpenDevice: open result is 10, (OK)
[  6602.551] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.551] drmOpenDevice: node name is /dev/dri/card0
[  6602.551] drmOpenDevice: open result is 10, (OK)
[  6602.552] drmOpenByBusid: drmOpenMinor returns 10
[  6602.552] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.552] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.553] drmOpenDevice: node name is /dev/dri/card0
[  6602.553] drmOpenDevice: open result is 10, (OK)
[  6602.553] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.553] drmOpenDevice: node name is /dev/dri/card0
[  6602.553] drmOpenDevice: open result is 10, (OK)
[  6602.553] drmOpenByBusid: drmOpenMinor returns 10
[  6602.553] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.553] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.564] (II) EMGD(0): Rotation : 0 degrees
[  6602.564] (II) EMGD(0): RendScale: 0
[  6602.567] (II) EMGD(0): ShadowFB allocated
[  6602.630] drmOpenDevice: node name is /dev/dri/card0
[  6602.630] drmOpenDevice: open result is 11, (OK)
[  6602.630] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.630] drmOpenDevice: node name is /dev/dri/card0
[  6602.630] drmOpenDevice: open result is 11, (OK)
[  6602.630] drmOpenByBusid: drmOpenMinor returns 11
[  6602.630] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.630] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.630] drmOpenDevice: node name is /dev/dri/card0
[  6602.630] drmOpenDevice: open result is 11, (OK)
[  6602.630] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.630] drmOpenDevice: node name is /dev/dri/card0
[  6602.630] drmOpenDevice: open result is 11, (OK)
[  6602.630] drmOpenByBusid: drmOpenMinor returns 11
[  6602.631] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.631] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.631] drmOpenDevice: node name is /dev/dri/card0
[  6602.631] drmOpenDevice: open result is 11, (OK)
[  6602.631] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.631] drmOpenDevice: node name is /dev/dri/card0
[  6602.631] drmOpenDevice: open result is 11, (OK)
[  6602.631] drmOpenByBusid: drmOpenMinor returns 11
[  6602.631] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.631] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.636] (II) EMGD(0): [DRI2] Setup complete
[  6602.637] (II) EMGD(0): [DRI2]   DRI driver: emgd
[  6602.637] (II) EMGD(0): DRI2 initialization complete.
[  6602.637] (II) UXA(0): Driver registered support for the following operations:
[  6602.637] (II)         solid
[  6602.637] (II)         copy
[  6602.637] (II)         composite (RENDER acceleration)
[  6602.637] (II) EMGD(0): ShadowFB initialization complete
[  6602.637] (==) EMGD(0): Backing store disabled
[  6602.656] drmOpenDevice: node name is /dev/dri/card0
[  6602.656] drmOpenDevice: open result is 12, (OK)
[  6602.657] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.657] drmOpenDevice: node name is /dev/dri/card0
[  6602.657] drmOpenDevice: open result is 12, (OK)
[  6602.657] drmOpenByBusid: drmOpenMinor returns 12
[  6602.657] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.657] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.657] drmOpenDevice: node name is /dev/dri/card0
[  6602.657] drmOpenDevice: open result is 12, (OK)
[  6602.657] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.657] drmOpenDevice: node name is /dev/dri/card0
[  6602.658] drmOpenDevice: open result is 12, (OK)
[  6602.658] drmOpenByBusid: drmOpenMinor returns 12
[  6602.658] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.658] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.659] (II) EMGD(0): Rotation : 0 degrees
[  6602.659] (II) EMGD(0): RendScale: 0
[  6602.664] (II) EMGD(0): ShadowFB allocated
[  6602.671] (II) EMGD(0): Hardware Cursor Initialization complete.
[  6602.671] (==) EMGD(0): Silken mouse enabled
[  6602.671] (==) EMGD(0): DPMS enabled
[  6602.672] (==) RandR enabled
[  6602.673] (II) Initializing built-in extension Generic Event Extension
[  6602.673] (II) Initializing built-in extension SHAPE
[  6602.673] (II) Initializing built-in extension MIT-SHM
[  6602.673] (II) Initializing built-in extension XInputExtension
[  6602.673] (II) Initializing built-in extension XTEST
[  6602.673] (II) Initializing built-in extension BIG-REQUESTS
[  6602.673] (II) Initializing built-in extension SYNC
[  6602.673] (II) Initializing built-in extension XKEYBOARD
[  6602.673] (II) Initializing built-in extension XC-MISC
[  6602.673] (II) Initializing built-in extension SECURITY
[  6602.673] (II) Initializing built-in extension XINERAMA
[  6602.673] (II) Initializing built-in extension XFIXES
[  6602.673] (II) Initializing built-in extension RENDER
[  6602.673] (II) Initializing built-in extension RANDR
[  6602.673] (II) Initializing built-in extension COMPOSITE
[  6602.673] (II) Initializing built-in extension DAMAGE
[  6602.673] (II) Initializing built-in extension GESTURE
[  6602.719] drmOpenDevice: node name is /dev/dri/card0
[  6602.719] drmOpenDevice: open result is 12, (OK)
[  6602.719] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.719] drmOpenDevice: node name is /dev/dri/card0
[  6602.719] drmOpenDevice: open result is 12, (OK)
[  6602.719] drmOpenByBusid: drmOpenMinor returns 12
[  6602.719] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.719] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.719] drmOpenDevice: node name is /dev/dri/card0
[  6602.720] drmOpenDevice: open result is 12, (OK)
[  6602.720] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.720] drmOpenDevice: node name is /dev/dri/card0
[  6602.720] drmOpenDevice: open result is 12, (OK)
[  6602.720] drmOpenByBusid: drmOpenMinor returns 12
[  6602.720] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.720] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.720] drmOpenDevice: node name is /dev/dri/card0
[  6602.721] drmOpenDevice: open result is 12, (OK)
[  6602.721] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.721] drmOpenDevice: node name is /dev/dri/card0
[  6602.721] drmOpenDevice: open result is 12, (OK)
[  6602.721] drmOpenByBusid: drmOpenMinor returns 12
[  6602.721] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.721] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.732] drmOpenDevice: node name is /dev/dri/card0
[  6602.732] drmOpenDevice: open result is 13, (OK)
[  6602.732] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.732] drmOpenDevice: node name is /dev/dri/card0
[  6602.732] drmOpenDevice: open result is 13, (OK)
[  6602.732] drmOpenByBusid: drmOpenMinor returns 13
[  6602.733] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.733] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.733] drmOpenDevice: node name is /dev/dri/card0
[  6602.733] drmOpenDevice: open result is 13, (OK)
[  6602.733] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.733] drmOpenDevice: node name is /dev/dri/card0
[  6602.733] drmOpenDevice: open result is 13, (OK)
[  6602.733] drmOpenByBusid: drmOpenMinor returns 13
[  6602.733] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.733] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.733] drmOpenDevice: node name is /dev/dri/card0
[  6602.733] drmOpenDevice: open result is 13, (OK)
[  6602.733] drmOpenByBusid: Searching for BusID PCI:00:02:00
[  6602.733] drmOpenDevice: node name is /dev/dri/card0
[  6602.733] drmOpenDevice: open result is 13, (OK)
[  6602.734] drmOpenByBusid: drmOpenMinor returns 13
[  6602.734] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  6602.734] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  6602.750] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  6602.750] (II) AIGLX: enabled GLX_INTEL_swap_event
[  6602.750] (II) AIGLX: enabled GLX_SGI_make_current_read
[  6602.750] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  6602.750] (II) AIGLX: Loaded and initialized /usr/lib/dri/emgd_dri.so
[  6602.750] (II) GLX: Initialized DRI2 GL provider for screen 0
[  6602.850] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  6602.892] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  6602.892] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  6602.893] (II) LoadModule: "evdev"
[  6602.893] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  6602.894] (II) Module evdev: vendor="X.Org Foundation"
[  6602.894]    compiled for 1.9.0, module version = 2.3.2
[  6602.894]    Module class: X.Org XInput Driver
[  6602.894]    ABI class: X.Org XInput driver, version 11.0
[  6602.894] (**) Power Button: always reports core events
[  6602.894] (**) Power Button: Device: "/dev/input/event1"
[  6602.894] (II) Power Button: Found keys
[  6602.894] (II) Power Button: Configuring as keyboard
[  6602.894] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  6602.895] (**) Option "xkb_rules" "evdev"
[  6602.895] (**) Option "xkb_model" "evdev"
[  6602.895] (**) Option "xkb_layout" "us"
[  6602.903] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[  6602.906] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  6602.906] (II) No input driver/identifier specified (ignoring)
[  6602.907] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  6602.907] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  6602.907] (**) Sleep Button: always reports core events
[  6602.907] (**) Sleep Button: Device: "/dev/input/event2"
[  6602.907] (II) Sleep Button: Found keys
[  6602.907] (II) Sleep Button: Configuring as keyboard
[  6602.907] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  6602.907] (**) Option "xkb_rules" "evdev"
[  6602.908] (**) Option "xkb_model" "evdev"
[  6602.908] (**) Option "xkb_layout" "us"
[  6602.911] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event5)
[  6602.911] (II) No input driver/identifier specified (ignoring)
[  6602.912] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event6)
[  6602.912] (II) No input driver/identifier specified (ignoring)
[  6602.919] (II) config/udev: Adding input device WebCam (/dev/input/event4)
[  6602.920] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[  6602.920] (**) WebCam: always reports core events
[  6602.920] (**) WebCam: Device: "/dev/input/event4"
[  6602.920] (II) WebCam: Found keys
[  6602.920] (II) WebCam: Configuring as keyboard
[  6602.920] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD)
[  6602.920] (**) Option "xkb_rules" "evdev"
[  6602.920] (**) Option "xkb_model" "evdev"
[  6602.920] (**) Option "xkb_layout" "us"
[  6602.929] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  6602.929] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  6602.929] (**) AT Translated Set 2 keyboard: always reports core events
[  6602.929] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  6602.929] (II) AT Translated Set 2 keyboard: Found keys
[  6602.929] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  6602.929] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  6602.930] (**) Option "xkb_rules" "evdev"
[  6602.930] (**) Option "xkb_model" "evdev"
[  6602.930] (**) Option "xkb_layout" "us"
[  6602.932] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[  6602.932] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  6602.932] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  6602.932] (**) SynPS/2 Synaptics TouchPad: Device: "/dev/input/event7"
[  6602.932] (II) SynPS/2 Synaptics TouchPad: Found 3 mouse buttons
[  6602.932] (II) SynPS/2 Synaptics TouchPad: Found absolute axes
[  6602.933] (II) SynPS/2 Synaptics TouchPad: Found x and y absolute axes
[  6602.933] (II) SynPS/2 Synaptics TouchPad: Found absolute touchpad.
[  6602.933] (II) SynPS/2 Synaptics TouchPad: Configuring as touchpad
[  6602.933] (**) SynPS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[  6602.933] (**) SynPS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6602.933] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  6602.933] (II) SynPS/2 Synaptics TouchPad: initialized for absolute axes.
[  6602.934] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  6602.934] (II) No input driver/identifier specified (ignoring)

```

A lsmod :
```

# lsmod
Module                  Size  Used by
joydev                 17161  0 
i2c_isch               12639  0 
arc4                   12473  2 
snd_hda_codec_realtek    63493  1 
snd_hda_intel          32515  0 
coretemp               13168  0 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
kvm                   357806  0 
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
microcode              18209  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
psmouse                84843  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13031  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 37276  0 
bnep                   17707  2 
parport_pc             31968  0 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13037  0 
ath5k                 135205  0 
ath                    19187  1 ath5k
emgd                  577343  5 
snd                    61991  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              461161  1 ath5k
lpc_sch                12727  0 
cfg80211              175375  3 ath5k,ath,mac80211
ext2                   67204  1 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
drm_kms_helper         47303  1 emgd
drm                   238768  7 emgd,drm_kms_helper
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
xts                    12723  2 
gf128mul               14503  1 xts
dm_crypt               22402  1 
vesafb                 13477  1 
pata_sch               12700  2 
r8169                  55976  0 
wmi                    18590  0 
video                  18847  0 

```

My modules blacklisted :
```

blacklist gma500_gfx
blacklist psb_gfx
blacklist acer_wmi

```

My Grub important informations
```

GRUB_GFXPAYLOAD_LINUX=1366x768x24
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor acpi_osi=Linux console=tty1 mem=896mb"

```

My packages
```

ii  x11-xserver-utils                         7.7~3ubuntu1                              i386         X server utilities
ii  xserver-common                            2:1.13.0-0ubuntu6.1                       all          common files used by various X servers
ii  xserver-xephyr                            2:1.13.0-0ubuntu6.1                       i386         nested X server
ii  xserver-xorg                              1:7.5+6ubuntu3.1                          i386         the X.Org X server
ii  xserver-xorg-core                         2:1.9.0-0ubuntu7.6                        i386         Xorg X server - core server
ii  xserver-xorg-input-evdev                  1:2.3.2-6ubuntu3.1                        i386         X.Org X server -- evdev input driver
ii  xserver-xorg-input-wacom                  1:0.10.8-0ubuntu1.1                       i386         X.Org X server -- Wacom input driver
ii  xserver-xorg-video-geode                  2.11.11-1~maverick1                       i386         X.Org X server -- Geode GX2/LX display driver
rc  xserver-xorg-video-intel                  2:2.20.9-0ubuntu2                         i386         X.Org X server -- Intel i8xx, i9xx display driver
rc  xserver-xorg-video-openchrome             1:0.3.1-0ubuntu1                          i386         X.Org X server -- VIA display driver
ii  xserver-xorg-video-savage                 1:2.3.1-2ubuntu2.1                        i386         X.Org X server -- Savage display driver
rc  xserver-xorg-video-vmware                 1:12.0.2+git.e5ac80d8-0ubuntu1            i386         X.Org X server -- VMware display driver
rc  libgl1-mesa-dri:i386                      9.0-0ubuntu1                              i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:i386                      9.0-0ubuntu1                              i386         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:i386                        9.0-0ubuntu1                              i386         free implementation of the GL API -- shared library
ii  libglu1-mesa:i386                         9.0.0-0ubuntu1                            i386         Mesa OpenGL utility library (GLU)
ii  libtxc-dxtn-s2tc0:i386                    0~git20110809-3                           i386         Texture compression library for Mesa
ii  mesa-utils                                8.0.1+git20110129+d8f7d6b-0ubuntu2        i386         Miscellaneous Mesa GL utilities
ii  emgd-bin                                  1.16.3196                                 i386         X11 drivers for Intel E6xx Processor and US15W/US15WP/WPT chipsets.
ii  emgd-dkms                                 1.16.3196                                 all          Intel EMGD driver in DKMS format.


```

My kernel is 3.5.0-21-generic from Ubuntu Quantal.

I hope someone could help me ! This will be very very very appreciated ! :D

Hello ! :-)

I known this post isn't for the EMGD solution, so, if there is some people who want to have 3D support for Poulsbo throught EMGD, I suggest to go on this thread :

[http://ubuntuforums.org/showthread.php?p=12468024#post12468024](http://ubuntuforums.org/showthread.php?p=12468024#post12468024)

Thanks

---

### Post by bodhi.zazen on 2013-01-22
For open source solutions see:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

For the EMGD, as it is a closed source driver, you will need to contact intel.

The EMGD has not worked on Linux in quite some time and as such is depreciated. Altough I have seen people claim it works, as you can see from your experience, I have not seen a working tutorial.

Good luck to you.

---

### Post by neokod on 2013-01-22
Hello bodhi.zazen,

The open source solution doesn't support 3D.

As explained in my first post, I need the 3D support, it's why I propose to try this method.

Thanks

---

### Post by bodhi.zazen on 2013-01-22
> **neokod said:**
> Hello bodhi.zazen,

The open source solution doesn't support 3D.

As explained in my first post, I need the 3D support, it's why I propose to try this method.

Thanks

You have 2 options:

1. Write the open source code yourself.

2. Contact Intel and ask them to fix the closed source driver so that it works with a modern kernel and xorg.

---

### Post by neokod on 2013-01-22
So, why under Fedora, EMGD with 3D works out of the box for Poulsbo ?

Is the communauty of Ubuntu is less ingenious than thoses of Fedora ?

---

### Post by bodhi.zazen on 2013-01-22
> **neokod said:**
> So, why under Fedora, EMGD with 3D works out of the box for Poulsbo ?

EMGD does not work out of the box, you would have to install it as it is a closed source driver, and thus not included in the Fedora repositories, let alone "out of the box". What version of Fedora are you talking about ?

The EMGD driver works with xorg 1.9 or lower and kernels < 3.0 (I think, not positive about the kernel version).

If you have the EMGD working for a modern version of Fedora (16, 17, 18, or rawhide) you should publish the how to. to my knowledge the EMGD has not worked in Fedora for years and the Fedora community will NOT accept bug reports for the EMGD driver.

See: [http://fedoraproject.org/wiki/Test_Day:2010-04-15_Intel](http://fedoraproject.org/wiki/Test_Day:2010-04-15_Intel)

That is Fedora testing, specifically for Intel. Please note:

> What's needed to test

    An Intel graphics adapter (i810 or later, **[size=4][color=red]except GMA 500 / Poulsbo**[/color][/size])  

So no, Fedora does NOT support the gma500, let alone the EMGD, either.

Part of your problem here is that at this time the GMA500 is showing it's age and the tutorials you are following are written for old versions of Ubuntu. Again not sure what version of Fedora you are using.

If it is a modern version of Fedora, you probably would need to update either the kernel or xorg in Ubuntu. If you link a working tutorial for Fedora 16-rawhide I will help if I can.

> Is the communauty of Ubuntu is less ingenious than thoses of Fedora ?

That attitude will not get you very far. The problem you have is that the EMGD is a closed source driver. You should direct your anger at Intel for failing to provide drivers. In fact if you continue to post in this style, I will not help you either and I have been using the GMA 500 for a long time. FWIW, I filed the (kernel) bug reports with both Fedora and Ubuntu so that the open source driver works out of the box with both Fedora and Ubuntu. Without my bug reports, you would get a black screen if you booted either, and would have to compile a custom kernel ;) .

---

### Post by Adam_GUI on 2013-01-22
> **neokod said:**
> So, why under Fedora, EMGD with 3D works out of the box for Poulsbo ?

Is the communauty of Ubuntu is less ingenious than thoses of Fedora ?

Do what now?  What version of Fedora?  Where?
People have had install errors with EMGD 1.16 in Fedora since version 16.
Kernel 3.2 and up have an open source driver that supports so much as some 2D rendering.  

EMGD 1.16 contains packages for Fedora 14 and MeeGo 1.2.  MeeGo has been split and Fedora 14 is four versions old.  
The big caveat to this driver looks to be running it on XOrg 1.9.
Intel had a hand in MeeGo and Fedora, which is why they got packages at all.
Their wording makes it sound like they can't release the source for the EMGD drivers -- something that would hopefully make getting it to work on new versions of XOrg far easier.

I can see why Ubuntu took the line they did with not pushing the EMGD driver.  It's a frozen dinosaur for what Ubuntu wants to ship and be up-to-date with.  

The Wiki here says the open driver suppsedly works alright with 12.10.  But, darn it, I'm tired of having to put a six month release version on that machine to just turn around and have the driver issue again in six more months.

So, I gave up, used Linux Mint Debian Edition and at least got some 2D effects on a Dell Inspiron Mini 1010.  It's not perfect, but at least it has the correct resolution.  

I only ever got EMGD 1.16 to partily install.  In Debian Squeeze, in Ubuntu 12.04, in LMDE.  Forget that mess.
As much as I'd love for that binary blob to work, it hasn't done so well since 10.10.  I have something working now.  I'm not willing to deal with it anymore.  

The game has become waiting for open drivers to happen or PowerVR to release documentation and allow Intel to put out source for EMGD.

I was annoyed to the point of picking up a different netbook and leaving the GMA500 beast as a beater that I now regard as nothing more than expendible.

---

### Post by ahallubuntu on 2013-01-22
I have one of these netbooks, too, and I have given up on EMGD and 3D/hardware acceleration.  My solution (until I finally get rid of it) is to have Ubuntu 11.04 and Ubuntu 12.04 both installed as a dual boot.  If I need to watch videos (need hardware acceleration to get decent performance), I use 11.04 with the EMGD driver.  But 11.04 is no longer supported, so I will use 12.04 (open source driver, no hardware acceleration) for everything else.

But I plan to replace this old netbook as soon as I can, anyway.  Even with EMGD it's very slow and completely unusable for certain things (like Skype).

Here is someone who worked on(?) porting EMGD to Windows 7 and Windows 8 - maybe you can find out if there are any plans for support of EMGD on 3.x Linux kernels:

[http://gma500booster.blogspot.com/](http://gma500booster.blogspot.com/)

---

### Post by techfanatic on 2013-02-01
> **ahallubuntu said:**
> Here is someone who worked on(?) porting EMGD to Windows 7 and Windows 8 - maybe you can find out if there are any plans for support of EMGD on 3.x Linux kernels:

[http://gma500booster.blogspot.com/](http://gma500booster.blogspot.com/)

Obviously, there's nothing for Linux.
I had given up for those tryings.

---

### Post by ferry_toth on 2013-02-03
> **neokod said:**
> And if someone have used this method, I would like to known if he could help me :-)

So, I have downgrade xorg, and used your deb packages. I have blacklisted psb/gma500 modules, and added a redirection script for X (because of the "-background" option renamed "-nr").

I have found the exact resolution parameters (for the native 1366x768 resolution), and I have no errors (EE), warnings (WW), failed messages or others problems in the logs.

But, strangly, I still have a blank screen .... :(

<snip>

I hope someone could help me ! This will be very very very appreciated ! :D

I guess the instructions you followed are for the fitpc. This has a HDMI connected to the SDVO. Your laptop probable has the display connected to the LVDS port.

I have a fitpc myself so my xorg.conf won't help you much. For instands I have 
portorder 

You didn't mention how you exactly downgraded X and where you got the emgd package.

Myself, I added maverick from deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) maverick main and added the ppa from Jools Wills to obtain emgd and some other stuff (mplayer-vaapi).

Downgrading easily goes wrong as some packages refuse to downgrade because of complicated dependancies. I needed to 'help' the downgrade by removing certain packages temporarily and/or force a certain version in aptitude.

In your case you have xserver-common 1.13, while it should probably be 1.9.
Similar libgl1-mesa-dri 9, where I have 7.9.

There will probably be other stuff too that didn't downgrade. 

It's a mess and probably get's more messy with each new ubuntu release. Don't forget, your making a sort of of remix of packages, that ultimately have little to do with ubuntu anymore.

The good news is: it can actually work. The emgd 2D is about the same speed as gma500_gfx, but supports 3D and video decode (through vaapi). I played a 1080 HD video with my fitpc!

Kubuntu opengl and gles desktop effects don't really work that well (crash kwin). With xrender it's fine, but you don't need emgd to do that.

All that said, if you need to play video it may be worth to go to emgd. For 3D, I have mixed results. Kwin desktop effects is not really worth the trouble, and from what I heard gnome and unity give no joy. XBMC runs (the gl based gui give 15fps), but that doesn't play video well. mplayer-vaapi is what you need for HD playback. If you need to run other gl applications, they might work well, 


Ferry

---

### Post by dimos15 on 2013-02-15
try eminteepc
linux mint + emgd

here it is

[http://eminteepc.freeforums.org/eminteepc-v1-50-this-week-end-t32.html]("http://eminteepc.freeforums.org/eminteepc-v1-50-this-week-end-t32.html")

---

### Post by thopiekar on 2013-07-11
Hello all together,

don't know if there is any interest left getting EMGD working on your devices, but I want to get it working again.
Maybe some people of you remember me from the past - for those who don't: I made the Xorg downgrades and the xorg.conf generator for our community. I'm glad to see many howto's using them online ;)
After my netbook's mainboard got broken I wasn't able to test my work, but now I bought a cheap mainboard from asia and I'd like to work on it again :)

Well, as EMGD 1.16 is out and there seem to be problems getting it working on Raring.. What are the most big problems at the moment? Do we still need Xorg downgrades? What about the kernel version?
Hope you can get me up-to-date again, thanks!

Got now EMGD working. Just need to make downgrading Xorg and Mesa cleaner.
I'm not really sure but I think I never downgraded Mesa for older EMGD versions before.
In my point of view OpenGL is fast and works good.
Tested on openarena, XBMC, projectm-pulseaudio and other opengl-software..
Just a framework, called kivy, I wanted to get working does not work, but seems to be releated to SDL.

If there are any questions feedback is welcome **in this thread**.

[ATTACH=CONFIG]250207[/ATTACH]
(Xorg 1.9 + Mesa 7.9 on Ubuntu Saucy (kernel 3.11) )

PS: This glxgears window above gives ~425FPS
PSS: Sorry about the screenshot quality..

---

### Post by wenceslao2 on 2014-02-09
Wow!, could you post a how to?, I would love to go back to linux since I have to remain windows 7 installed because of the 2D and 3D acceleration. How's the video playback?

---

### Post by thopiekar on 2014-02-10
Well, in my case installing Win7 was not an option as I just have 16GB SSD.

Video playback is ok, if you are watching SD video..
As I didn't get VA-API working and looking at the CPU usage, I think it is related to the encoding that the playback is that poor.
Saw people at yoctoproject providing patches for EMGD or vaapi to make (their own) driver work.
Sadly I found no way to debug that as I think there are missing dependencies or find these patches to make it work.

I'm uploading my work to GitHub and my PPA at launchpad. There are many old packages in it, but I'm working on a clean up.
So it is still a work in progress.

Can't say it will work on your netbook, too, I use a Asus T91. The driver still does not configure the screen automaticly, you'll need to configure it by hand. (emgd-xorg-conf does not work for me since emgd 1.10) But Intel provides two samples for that and one of it worked.
However when looking at the hours I spent on getting this driver work, getting no help from Intel as they say I had to own a company to get deeper support and I never asked for money in the past even for a cup of coffee, I will probably now don't provide any instructions as long as I don't see any feedback.

PS: Here a clip to see my results: [http://youtu.be/v5VHH5ie2CY](http://youtu.be/v5VHH5ie2CY)

Well, added now quick start guide at [https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide](https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide)
Give still not support on that, so you'll need to make it work in your own.
Please let me know when you get it working to collect the configurations which need to be made.

---

### Post by lumpysaurus on 2014-02-23
> **thopiekar said:**
> Well, added now quick start guide at [https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide](https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide)
Give still not support on that, so you'll need to make it work in your own.
Please let me know when you get it working to collect the configurations which need to be made.

Hi,

Thanks for your work, I'm going to try this on a Vaio P that is currently running 12.04.3. (3.11 kernel)

The quick start says to use install xorg-module but there isn't such a thing to install. Could you elaborate the steps I'd need to take to try this out?

Thanks

Tim

---

### Post by thopiekar on 2014-02-25
Oh, sorry it was not meant to stay as a name of a package.
The needed meta package is called "[COLOR=#333333][FONT=Consolas]xserver-xorg-1.9-video-emgd[/FONT][/COLOR]" and will install the meego subpackage.

PS: I just updated the quick start guide as it is needed to blacklist the opensource driver and force to load the emgd driver.
PSS: Now building libav against the libva I got from Tizen. I'm wondering which version it really has, as it seems to be 1.0.15 but including 1.1.x. However, vainfo does not crash with it and I hope the libav rebuild will give us VA-API support soon.

I've got good and bad news. The good is that I got OpenGL ES now running and the bad OpenGL is broken now as I moved the binaries to a multilibrary layout now. I'm going crazy :mad:

The reason why I moved the libraries to that layout is that dependencies like libva expect the binaries at /usr/lib/i386-*/* :???:
I'll make now the mesa-7.9 package multiarch as well. OpenGL was working with it before very well..

So for those who are testing the drivers: it might come to missing files, messed up dependencies, conflicting files or whatever. In most cases it would be enough to disable the driver at xorg.conf and remove emgd from boot. Just hold on and wait - fixes will be available in my PPA soon. (Hopefully :P)

UPDATE: Everything (OpenGL/OpenGL ES) works now except of VA-API! ( Using the fedora14 binaries)

---

### Post by lumpysaurus on 2014-03-02
I've tried this on 12.04 but there are no packages in your repository for precise. I'm going to give saucy a try now. I'll let you know how I get on.

I'm having real trouble installing xserver-xorg-1.9-video-emgd and mesa7.9 using your repo. It's a clean install of 13.10. Do you have any tips for the steps I should take?

Thanks

---

### Post by thopiekar on 2014-03-03
Well, which messages / output do you get. Looks like I need to add more time to that. Do you use a GUI to install the packagea or a commandline tool, e.g. apt-get?

Well, I didn't take care that much on precise as there is enough work on getting libva working. You might notice I'm providing different versions of it at the moment on the repo for testing.
I just contacted the yoctoproject team - hope it get mail from them.

---

### Post by lumpysaurus on 2014-03-04
> **thopiekar said:**
> Well, which messages / output do you get. Looks like I need to add more time to that. Do you use a GUI to install the packagea or a commandline tool, e.g. apt-get?


I'm using apt-get but I'm not sure the exact steps you are expecting me to use with your repo. I've clean installed 13.10 because I got to a point where it wouldn't boot (no CTRL ALT F1 etc)

So what commands from here would you expect me to run? I'll run them and report back the exact problems I'm having, hopefully by working through it we can create some kind of guide for other people that want to do the same thing.

---

### Post by thopiekar on 2014-03-04
To add the repository, run:
```

sudo add-apt-repository ppa:thopiekar/emgd
sudo apt-get update

```

Then install the EMGD-driver by:
```

sudo apt-get install emgd-driver

```

This should be enough to install the driver and it also should downgrade Xorg to v1.9 and Mesa to 7.9. Hope it works :)

---

### Post by lumpysaurus on 2014-03-04
If I do that, I get this error

```
 
littlevaio:~$ sudo apt-get install emgd-driverReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 emgd-driver : Depends: xserver-xorg-1.9-video-emgd but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


 
```

---

### Post by thopiekar on 2014-03-05
ok, now run
```

sudo apt-get install xserver-xorg-1.9-video-emgd

```

and if a similar problem appears run on the next package the same command.

Thank you for your feedback!

---

### Post by lumpysaurus on 2014-03-05
> **thopiekar said:**
> ok, now run
```

sudo apt-get install xserver-xorg-1.9-video-emgd

```

and if a similar problem appears run on the next package the same command.

Thank you for your feedback!

Now I get this

littlevaio:~$ sudo apt-get install  xserver-xorg-1.9-video-emgd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 xserver-xorg-1.9-video-emgd : Depends: xserver-xorg-1.9-video-emgd-meego1.2 (= 1.16-201403012312+emgd~rev94~ubuntu13.10.1) but it is not going to be installed or
                                        xserver-xorg-1.9-video-emgd-meego-wayland (= 1.16-201403012312+emgd~rev94~ubuntu13.10.1) but it is not going to be installed or
                                        xserver-xorg-1.9-video-emgd-tizen1.0 (= 1.16-201403012312+emgd~rev94~ubuntu13.10.1) but it is not going to be installed or
                                        xserver-xorg-1.9-video-emgd-fedora14 (= 1.16-201403012312+emgd~rev94~ubuntu13.10.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by thopiekar on 2014-03-05
ok, it wants to install [COLOR=#000000]xserver-xorg-1.9-video-emgd-meego1.2
[/COLOR]I know there is a problem, which should be fix soon..
Try to install [COLOR=#000000]xserver-xorg-1.9-video-emgd-tizen1.0.

```
[/COLOR]sudo apt-get install xserver-xorg-1.9-video-emgd-tizen1.0[COLOR=#000000]
[/COLOR]
```

---

### Post by lumpysaurus on 2014-03-05
> **thopiekar said:**
> ok, it wants to install [COLOR=#000000]xserver-xorg-1.9-video-emgd-meego1.2
[/COLOR]I know there is a problem, which should be fix soon..
Try to install [COLOR=#000000]xserver-xorg-1.9-video-emgd-tizen1.0.

[/COLOR]```
sudo apt-get install xserver-xorg-1.9-video-emgd-tizen1.0[COLOR=#000000]
[/COLOR]
```

Done successfully, now i've managed to install emgd-driver however it doesn't look like it installed mesa 7.9. What should I do now?

littlevaio:~$ sudo apt-get install emgd-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms emgd-drm-dkms emgd-headers emgd-headers-meego1.2 emgd-utils
  emgd-utils-ced-lite emgd-utils-gui emgd-utils-gui-meego1.2 fakeroot
  libdrm-dev libkms1 xserver-xorg-1.9-video-emgd
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed
  dkms emgd-driver emgd-drm-dkms emgd-headers emgd-headers-meego1.2 emgd-utils
  emgd-utils-ced-lite emgd-utils-gui emgd-utils-gui-meego1.2 fakeroot
  libdrm-dev libkms1 xserver-xorg-1.9-video-emgd
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,576 kB of archives.

> **lumpysaurus said:**
> Done successfully, now i've managed to install emgd-driver however it doesn't look like it installed mesa 7.9. What should I do now?

littlevaio:~$ sudo apt-get install emgd-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms emgd-drm-dkms emgd-headers emgd-headers-meego1.2 emgd-utils
  emgd-utils-ced-lite emgd-utils-gui emgd-utils-gui-meego1.2 fakeroot
  libdrm-dev libkms1 xserver-xorg-1.9-video-emgd
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed
  dkms emgd-driver emgd-drm-dkms emgd-headers emgd-headers-meego1.2 emgd-utils
  emgd-utils-ced-lite emgd-utils-gui emgd-utils-gui-meego1.2 fakeroot
  libdrm-dev libkms1 xserver-xorg-1.9-video-emgd
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,576 kB of archives.


Just further evidence of mesa7.9 not being installed
littlevaio:~$ dpkg -l | grep mesa
ii  libegl1-mesa:i386                         9.2.1-1ubuntu3                                  i386         free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:i386                 9.2.1-1ubuntu3                                  i386         free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dri:i386                      9.2.1-1ubuntu3                                  i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:i386                      9.2.1-1ubuntu3                                  i386         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:i386                        9.2.1-1ubuntu3                                  i386         free implementation of the GL API -- shared library
ii  libglu1-mesa:i386                         9.0.0-1                                         i386         Mesa OpenGL utility library (GLU)
ii  libopenvg1-mesa:i386                      9.2.1-1ubuntu3                                  i386         free implementation of the OpenVG API -- runtime
ii  mesa-utils                                8.1.0-2                                         i386         Miscellaneous Mesa GL utilities

---

### Post by thopiekar on 2014-03-06
Well, now OpenGL applications will run now, but you will just see a black window. To install mesa-7.9 you'll need to install "libgl1-mesa-7.9-glx" and other packages like egl if you like, but egl is fully provided by EMGD so I think that more is not needed. (Haven't tested it so far.) All packages which are named with "mesa-7.9" should replace the upstream packages.

---

### Post by lumpysaurus on 2014-03-06
Without installing mesa the whole system locks up. I've installed mesa now.

But now when I boot I go straight to the command prompt. Typing X says that it isn't installed and suggests installing xserver-xorg

---

### Post by thopiekar on 2014-03-06
Sounds like [COLOR=#333333][FONT=Ubuntu]xserver-xorg-1.9[/FONT][/COLOR] is not installed. Remember that I had to make a symlink in that package to provide the executable.
So what is the situation now? [COLOR=#333333][FONT=Ubuntu]xserver-xorg-1.9-core[/FONT][/COLOR] is still installed right? Neither [COLOR=#333333][FONT=Ubuntu]xserver-xorg-1.9[/FONT][/COLOR] nor [COLOR=#333333][FONT=Ubuntu]xserver-xorg [/FONT][/COLOR]are installed?
I wonder why it happend as I marked [COLOR=#333333][FONT=Ubuntu]xserver-xorg conflicting [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]xserver-xorg-1.9-core[/FONT][/COLOR] and made [COLOR=#333333][FONT=Ubuntu]xserver-xorg-1.9 [/FONT][/COLOR]a possible replacement of [COLOR=#333333][FONT=Ubuntu]xserver-xorg[/FONT][/COLOR] :/

In case of a default install there should be a meta-package depending on [COLOR=#333333][FONT=Ubuntu]xserver-xorg[/FONT][/COLOR], e.g. [k/l/x]ubuntu-desktop..[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by lumpysaurus on 2014-03-06
> **thopiekar said:**
> Sounds like xserver-xorg-1.9 is not installed. Remember that I had to make a symlink in that package to provide the executable.
So what is the situation now? xserver-xorg-1.9-core is still installed right? Neither xserver-xorg-1.9 nor xserver-xorg are installed?
I wonder why it happend as I marked xserver-xorg conflicting xserver-xorg-1.9-core and made xserver-xorg-1.9 a possible replacement of xserver-xorg :/

In case of a default install there should be a meta-package depending on xserver-xorg, e.g. [k/l/x]ubuntu-desktop..


"Neither xserver-xorg-1.9 nor xserver-xorg are installed?"
Correct 

It uninstalled ubuntu-desktop as far as I remember when I installed xserver-xorg-1.9-video-emgd-tizen1.0

> **lumpysaurus said:**
> "Neither xserver-xorg-1.9 nor xserver-xorg are installed?"
Correct 

It uninstalled ubuntu-desktop as far as I remember when I installed xserver-xorg-1.9-video-emgd-tizen1.0

I've managed to install xserver-xorg-1.9 and that means I can start X. I don't have ubuntu-desktop installed. Starting X comes up with a blank screen, I'm not sure if thats because ubuntu-desktop is uninstalled or because I have my xorg.conf wrong. I'm not sure what the difference is between the two templates given.

Could you explain?

> **lumpysaurus said:**
> I've managed to install [COLOR=#000000]xserver-xorg-1.9 and that means I can start X. I don't have ubuntu-desktop installed. Starting X comes up with a blank screen, I'm not sure if thats because ubuntu-desktop is uninstalled or because I have my xorg.conf wrong. I'm not sure what the difference is between the two templates given.

Could you explain?
[/COLOR]


Ok figured it out, I was using the rv template, the cb one works!

I'm going to see how it performs now!

Thanks!

---

### Post by thopiekar on 2014-03-06
No problem. Don't forget to set the resolution and the color depth well in the xorg.conf. Someone already asked me how to do that on GitHub. Take a look there for explainations. 

[https://github.com/EMGD-Community/intel-binaries-linux/issues/5](https://github.com/EMGD-Community/intel-binaries-linux/issues/5)

---

### Post by lumpysaurus on 2014-03-09
Have you managed to get any desktop compositors to work with this technique?

---

### Post by thopiekar on 2014-03-09
Tested so far Compiz in MATE and KWin (I think I used the xorg module for meego1.2 as tizen1.0 was missing a library - can't remember exactly).
Additionally Enlightenment 17 also worked while having OpenGL enabled.
The best for OpenGL and OpenGL ES support is so far using the xorg driver for fedora, but some applications require a newer version of Mesa.
I made some researches about the distributions (fedora/meego/tizen) and found out that Tizen1.0 used Mesa 8.1, but 8.1 has never been really released. It was directly called 9.0.
I also checked the yocto-projects mailing list and they suggested somewhere in the past (didn't found it again in their recipes) to use Mesa 9.1.6. So I looked for it in Launchpad and found it at Raring. Repackaged them and made them installable aside the upstream libgl1-mesa-*-glx packages using the alternative system.
See: [https://code.launchpad.net/~thopiekar/emgd/mesa-9.1](https://code.launchpad.net/~thopiekar/emgd/mesa-9.1) . Somehow the code import is buggy, hope launchpad will fix that soon.

---

### Post by Adam_GUI on 2014-07-05
@thopiekar
Thanks for setting up a PPA and getting the EMGD working again.
I have a Dell Insperon Mini 1010 with a GMA500 chip that has gone from being incredibly slow to being somewhat stable.
I'm running Xubuntu 14.04.

For anyone with this same model, some stuff I've had to do so far:

Edit grub for display size and backlight.  Correct resolution for my model is 1024x576 @ 32bit color.

Disable Grub splash.  The splash screen during boot would freeze the system and require a hard reboot.
If there's something more annoying than getting this card to work, it's having to sit through a fsck
every other boot because you had to power down the system to get past the splash screen.

Installed XDM.  GDM might work.
LightDM just doesn't work.  I don't know why.  It just doesn't.
Typing "lightdm" at command prompt just had a line return.  No output.
Root could get to a desktop with "startx".
Made a change to allow users to issue "startx" and was taken to a desktop.
XDM comes up after boot.  So, there's no reason to manually issue "startx" anymore.

Using mplayer for video works. 
Downloaded a video from youtube.  
It's handy to have something like winff installed to make resolutions smaller, 
as the system seems to handle video playback better with smaller resolutions.
Took the video down to 800x600 with XVid compatible AVI instead of MP4.
Audio sync is better, but not great.
This is still time-and-battery-consuming.  
If you depend on a GMA500 for presentations, do stuff like this ahead of time.

Didn't have audio with flash video in firefox.  Not sure why.  I'll test again later.

Low level compositing from xfce runs well enough to get docky going.
Haven't attempted full compiz with emgd yet.  
But, since video playback is still iffy, I don't want to push the system further.

_Edit without wanting to necrobump_:
System started waiting forever to do so much as open a quick launch window for me using the EMGD drivers.

I installed Debian 7.5 with their live CD.
Default resolution out of the box.  Working base compositing, so, I can run things like cairo-dock with correct label rendering.
Added myself to the sudo group.
VLC worked after changing the default video driver.  Forget which.  LibVA is installed, but isn't a selection in VLC.

Cheese works.  First time I've seen that happen in a while.  Not GMA related.  Just an observation.
LibreOffice is sitting at version 3 over there.  But, there are debs on the machine waiting to go.

Microphone is really scratchy.  There used to be an easy fix for that.  But, I don't remember what it was.
Altered the ALSA config to match my model = no change.  Installed pulseaudio with pavucontrol = no change.
Still, everything works at a good clip.  Youtube videos aren't choppy.  Local playback of video works well.

Not that I rely on the machine for anything.  But, for now, I'm keeping this machine running Debian.

---

### Post by thopiekar on 2014-07-24
@Adam No problem. How does it work for you? Do you get any kernel freezes? My Asus T91 still has some problems thats why I started fixing compilation warnings from the DRM driver.

* Didn't noticed that grub problem.. However I hope to get this working: [http://askubuntu.com/questions/501283/append-options-to-grub-cmdline-linux-default-without-modification-on-files](http://askubuntu.com/questions/501283/append-options-to-grub-cmdline-linux-default-without-modification-on-files)
* About the lightdm problem: [https://github.com/EMGD-Community/intel-binaries-linux/issues/11](https://github.com/EMGD-Community/intel-binaries-linux/issues/11)
* If you got a perfectly working xorg.conf please add it here: [https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf](https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf)
* Also the instructions at [https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide-no-va-api-support](https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide-no-va-api-support) are not up-to-date - blacklisting and add "emgd" to /etc/modules is not needed anymore
* Well, libVA needs to be downgraded to 1.0.x because the closed-source binary provided by Intel was built against it and does not support the new API. I'm also working on making my libva* packages a smooth replacement to the upstream libraries. But I expect there is still a problem with the DRM mdoule :(
* If there are any (fixable) problems, just add them on Github: [https://github.com/EMGD-Community/intel-binaries-linux/issues](https://github.com/EMGD-Community/intel-binaries-linux/issues)

Feel free to contribute :)

---

### Post by Adam_GUI on 2014-07-31
> **thopiekar said:**
> @Adam No problem. How does it work for you? Do you get any kernel freezes? My Asus T91 still has some problems thats why I started fixing compilation warnings from the DRM driver.

* Didn't noticed that grub problem.. However I hope to get this working: [http://askubuntu.com/questions/501283/append-options-to-grub-cmdline-linux-default-without-modification-on-files](http://askubuntu.com/questions/501283/append-options-to-grub-cmdline-linux-default-without-modification-on-files)
* About the lightdm problem: [https://github.com/EMGD-Community/intel-binaries-linux/issues/11](https://github.com/EMGD-Community/intel-binaries-linux/issues/11)
* If you got a perfectly working xorg.conf please add it here: [https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf](https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf)
* Also the instructions at [https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide-no-va-api-support](https://github.com/EMGD-Community/intel-binaries-linux#quick-start-guide-no-va-api-support) are not up-to-date - blacklisting and add "emgd" to /etc/modules is not needed anymore
* Well, libVA needs to be downgraded to 1.0.x because the closed-source binary provided by Intel was built against it and does not support the new API. I'm also working on making my libva* packages a smooth replacement to the upstream libraries. But I expect there is still a problem with the DRM mdoule :(
* If there are any (fixable) problems, just add them on Github: [https://github.com/EMGD-Community/intel-binaries-linux/issues](https://github.com/EMGD-Community/intel-binaries-linux/issues)

Feel free to contribute :)

I'm no longer running Ubuntu on the system.  I have to go for a stable system instead of living on the edge.
So, you can compare what I've got with a running Debian system against what you have to work with in Ubuntu.

Not exactly what you've asked for, but this is what I've got:

Debian 7.5 XFCE (Installed from the Debian Stable Live CD). [Found here.]("https://www.debian.org/CD/live/")
There's a bug in the installer regarding Grub.  You must be connected to a network for it to install correctly.
So, it's a good idea to hook the computer up to an ethernet cord during installation.

There is no Xorg.conf anymore.  Bugs the hell out of me, too.

Display reports a resolution of 1024x576 at Zero Hertz.  So, still fighting XOrg with the driver over here.  Works, though.

XOrg version reports as being 1:7.7+3~dev7u1.  So, way behind there?
linux-image-3.2.0-4.  I'm booting into the 686-PAE kernel.

It loads a GMA500 driver.  Most likely the free driver written by the guy over at Mandriva.

There's no splash during boot by default.  I get text all the way until lightdm loads.

libva reports:
libva-intel-vaapi-driver 1.0.17-1
libva-x11-1                 1.0.15-4
libva                          1.0.15-4

No libva glx driver is in use.

VLC handles video playback fine.
VLC version 2.0.3 "Twoflower".
Video Settings must use "X11 Video Output (XCB)".

Flash video runs fullscreen in IceWeasel and Chrome with no stuttering.
So, there's probably significant regression in processing with newer versions of XOrg.

Low level compositing works.  I get labels over icons in cairo-dock.

Audio is a little scratchy.  Could be ALSA?  I'm not sure.  Either way, it's not the fault of the video driver.

---

### Post by thopiekar on 2014-07-31
Well, I would prefer to install Xubuntu then. You can remove all the branding then or also use MATE like me if you like it more like the "oldschool" ;)

I would suggest you to use my Ubuntu PPA with Debian (which works in most cases) but some of my packages depend on a newer version of libc6. Which means that you'll need to upgrade on your Debian install, but it will break some applications. They will still work, but for example VLC (got that info from a Debian user) will not show OSD notifications anymore.

So there is still the option to move to a supported Ubuntu release or to rebuild every package I host at launchpad, which might be not so hard for a experianced Debian user (using pbuilder).

You will have at the end OpenGL + ES working - not every 3D application will work as a downgrade to mesa 7.9 will not have all the features as the upstream. Playback will be smooth (SD quality using XBMC).
And finally I'm working at the moment getting libVA working, but don't beleave it will ever work without problems because of the driver.

About had the ALSA problem: I found a kernel option which made my soundcard work. It was about selecting the right buffer, just google about that option in snd_hda_intel.
About [COLOR=#000000]libva-intel-vaapi-driver[/COLOR] : It is useless as it is meant to be used with the opensource intel driver..[COLOR=#000000][/COLOR]

Haven't posted here any news for a long time, so fresh news here from my GMA500 netbook running Ubuntu Vivid.
Have updated our DRM driver module and EMGD works here very well, after doing a general downgrades using my PPA.

Regards

---

### Post by emmanuel.dejesus on 2015-04-24
Hi Thopiekar,

Great! Just installed Vivid yesterday, your emgd is working great on it.

I've tried to install xbmc but it depends on libva1.2. Did you have any success with libva1.2 and emgd? Have you planned to add it for Vivid on you PPA ?

---

### Post by thopiekar on 2015-04-24
Well, many packages depend on it and for any reason they strictly need exactly this "real" package. I tried to make a replacement like I've done for Xorg, but after installing my libva1-1.0.16, which virtually provides libva1, the real package (which is provided by Ubuntu) can't be removed and is still needed. I'm sure there is anything wrong with my packages. but I can't get what :(

Additionally I have to fix an kernel warning I saw in "dmesg". It should be related to the patches I made, but I already saw patches for other projects (like XEN) which also had this warning. I hope I can apply the fixes on the EMGD driver, too.

Btw. did you had to make any tweaks to your xorg.conf? I'm always interested to collect specific xorg.conf's for different devices on github: [https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf](https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf)

---

### Post by emmanuel.dejesus on 2015-04-24
I've only modified the resolution from your asus_T91.conf and it worked out of the box (after commented the options)
My laptop is acer aspire one 751.

---

### Post by validust on 2015-04-28
Hi ye brethren of all sexes of GMA500 perseverance!
Got this to work with Vivid, with MATE (and consequently no ubuntu desktop), on my ASUS 1101 HA, by firstly placing the (simplest) emgd.conf file as xorg.conf in /etc/X11. 
The display was off center, and not much functioned. I then moved /usr/share/X11/xorg.conf.d to /etc/X11, and moved the xorg.conf file, re-renamed "10-emgd.conf", into that.
When rebooting (and using the System-Preferences-Monitors), the display was okay. [ATTACH=CONFIG]261706[/ATTACH]
 And by installing the multimedia packages of emgd110, it all 
worked. :D - To my great surprise.
This is to say: Thank you thopiekar!  :wink:         

[LIST]
[*] 
[/LIST]

---

### Post by thopiekar on 2015-04-30
> **emmanuel.dejesus said:**
> I've only modified the resolution from your asus_T91.conf and it worked out of the box (after commented the options)
My laptop is acer aspire one 751.

Could you tell me which resolution it is?

@validust: Which components have you installed? When possible I would like to add them in my PPA if they work.

---

### Post by validust on 2015-05-01
Hi thopiekar! It seems to me the simplest way to clarify my dispositions is by appending the screenshots. I´ve no routine in handling the what-alls of this certainly splendid communication device. Apologies.
To get the brightness applet working (also the brightness function in Power Manager),  I first uninstalled the emgd-backlight of your PPA. Was informed that doing so would uninstall the emgd-driver too. Did it anyway, and installed the emgdbl of emgd110. The emgd driver was still there and functioning! I did not complain :)  That is also why it shows as if the emgd-driver is not installed. Got to love linux! :D  ...Yeah... the emgd-drm-dkms... Must have installed it. When I wasn´t paying attention.
For whatever it´s worth I mention also a lightdm tic: When booting, there is first a correctly drawn login screen, which is replaced by a somewhat hinky dito. *That* one accepts my login attempt. When clicking ENTER, there is *another* well apointed login screen. Which give way to... The Desktop. 
[ATTACH=CONFIG]261689[/ATTACH][ATTACH=CONFIG]261690[/ATTACH][ATTACH=CONFIG]261691[/ATTACH][ATTACH=CONFIG]261692[/ATTACH]                                                   
(The precise repo is installed so I could fetch this n that to make mobilemediaconverter work.)
BTW When writing the command "emgd-xorg-conf" (of emgd110) in a terminal, the "10-emgd-conf" file was created in /usr/share/X11/xorg.conf.d (which I hadn´t deleted earlier).

---

### Post by thopiekar on 2015-05-05
Well, emgd-xorg-conf which I wrote before for emgd-1.10 was also not working anymore for me. It seems that the needed configurations have changed now in 1.18. As I focus to keep the driver alive I didn't work on this tool anymore, just to save time and invest it on the important things.
However, emgd-backlight-dkms and emgdbl are the same. I just renamed the package into emgd-backlight and moved it to the github branch just to have all EMGD stuff together at one place. I wonder why installing the old emgdbl package works except of my emgd-backlight-dkms (does not make much sense to me).
Could you show me the exact content of your xorg.conf? And have you tried the "EMGD GUI Utility" at Applications>Tools? Does everything work there (incl external monitors via VGA or HDMI)?
I thought that a individual xorg.conf is always needed to setup the driver - at least it was always needed for my device...
Many thanks for the screenshots btw.! :)

Finally good news: Yesterday I just get a rid of the kernel warning which appeared for the 3.19.x kernel.

PS: I just found a way now how to force ldconfig to use our downgraded libva (libva.so.1 => /usr/lib/i386-linux-gnu/vaapi-1.0.16/libva.so.1 (0xb3490000)) :D

---

### Post by validust on 2015-05-05
"(does not make much sense to me)" lol ! :D Well, thopiekar, it has gotten so that if something linuxoidal seems to make sense to me, I assume that I´ve misunderstood it. ;)
I am in ubuntu-mate 14.04.2 now. Have just upgraded with your latest. And switched emgd-backlight to emgdbl of emgd110. Yup.
EMGD GUI... I´ve opened it. And then I closed it. When this whatchamacallit is as ready as it can be, I will make yet another partimage image (which is, thankfully, possible since I´ve installed it on an ext3 partition), and try it out.
The xorg.conf file is identical to the 10-emgd.conf file. When I started with *this* Trusty, I skipped making it an xorg.conf file. Just moved /usr/share/X11/xorg.conf.d to /etc/X11 (using the superuser caja of Precise), and placed the 10-emgd.conf in it. That worked too.

```

Section "ServerLayout"
     Identifier     "Default Layout"
     Screen 0       "Screen0"        0 0 
EndSection

Section "Device"
     Identifier                                           "Intel_EMGD-0"
     Driver                                               "emgd"
     VendorName                                           "Intel(R) DEG"
     BoardName                                            "Embedded Graphics"
     BusID                                                "0:2:0"
     Screen                                               0
     VideoRAM                                             131072
     Option     "PcfVersion"                              "1792"
     Option     "ConfigId"                                "1"
     Option     "PortDrivers"                             "lvds"
     Option     "ALL/1/name"                              "lvds-display"
     Option     "ALL/1/General/DisplayConfig"             "1"
     Option     "ALL/1/General/DisplayDetect"             "1"
     Option     "ALL/1/Port/4/General/name"               "LVDS"
     Option     "ALL/1/Port/4/General/Edid"               "1"
     Option     "ALL/1/Port/4/Attr/70"                    "0"
     Option     "ALL/1/General/Accel"                     "1"
EndSection

Section "Screen"
     Identifier    "Screen0"
     Device        "Intel_EMGD-0"
     Monitor       "LVDS"
     SubSection    "Display"
          Depth     24
          Modes    "1366x768"
     EndSubSection

EndSection

Section "Monitor"
     Identifier   "LVDS"
     ModelName    "LCD Panel used by EMGD" 
EndSection

Section "DRI"
     Mode         0666
EndSection

Section "Extensions"
     Option "composite" "enable"
EndSection

```


  [ATTACH=CONFIG]261780[/ATTACH][ATTACH=CONFIG]261781[/ATTACH][ATTACH=CONFIG]261782[/ATTACH]

Am really grateful for your work. You´re worth every good news and breakthrough! :)

----------

An oddity which has stumped me ever since I managed to get Precise working with emgd110 - Bless you! - is the emoticons in facebook. Most of them show to me (Not whoever is receiving them) as something other than they should; the simpatico :) for example, shows as an arrow pierced heart. At times they are correct, a week or more, and then they flip over to show up wrongly again. Is there anything to do about it?

-------------------

Tried out the EMGD GUI.  It worked, though the greyed out colour depth stayed at 32. Couldn´t "ungrey" it. Could be that "Colour Correction" is dependent on 32?  Btw; The one deciding reason for me to stay on with your 1.16 in Trusty-MATE is the excellent colours. A great improvement on emgd1.10 in Precise!   
I don´t have any external monitors...

---

### Post by thopiekar on 2015-05-15
Your workaround should not be needed now - I really wonder why older versions of Ubuntu just loaded the kernel module without any additions (maybe some old configurations were left). However thank you for pointing that out! I added this fix ( [https://github.com/EMGD-Community/intel-binaries-linux/commit/7e8cb583a0724665a7e322866fe2ac03ce11f55a](https://github.com/EMGD-Community/intel-binaries-linux/commit/7e8cb583a0724665a7e322866fe2ac03ce11f55a) ) which worked for me here locally.

Well, as you said that you've got it working with minimal configurations I was interested whether external monitors are also detected without any problems. I had to define all outputs (incl. built in monitor) on my own.

I'm not familiar with the EMGD GUI that much, check the Intel *.pdf's for this driver release you can find in my github repo ( [https://github.com/EMGD-Community/intel-binaries-linux](https://github.com/EMGD-Community/intel-binaries-linux) )

---

### Post by validust on 2015-05-16
Yes! Now there are only your emgd-1.16 adorning my ubuntu-mate-14.04.  emgd-backlight shines. :D  Pity I can´t shed any light on external monitors detection...

(One more bean, and I´ll be able to message Bucky Ball or some equally helpful and friendly moderator about the demise of mate-1.6, and its making my how-to [http://ubuntuforums.org/showthread.php?t=2195959](http://ubuntuforums.org/showthread.php?t=2195959) quite defunct. Cannot insinuate myself into it, and give visitors notice, since the thread is "closed".)

---

### Post by raul23 on 2015-09-04
Are you still working on this driver? I'm using Sony Vaio P and i'm curious if it would work better than opensource driver. 
If I'm correct this driver should work with new kernels, how about newest Mint?

---

### Post by validust on 2015-09-12
Hi! Just a note: I run thopiekars emgd-1.16 in ubuntu-MATE 14.04. The last kernel update that was accepted was 3.16.0-41-generic. None of the later (so far up to 3.16.0-49-generic) has worked. Not complaining, just noting. ;)
Edit 2016.01.27: Am running ubuntu-mate with kernel 4.2.0-22-generic now. So... Also did an upgrade to ubuntu-15.10 wily, by fetching wilys repos to synaptic, and "upgrade all". And thereafter fetched ubuntu-16.04´s repos, and did the same.

---

### Post by raul23 on 2015-09-15
Thanks. 

Does EMGD driver have any 2D video acceleration (I don't mean vaapi)?

---

### Post by validust on 2015-09-17
Hi raul23!
I don´t know enough to be able to answer your question. Sorry. Actually I don´t know enough to even *understand* the question.
What I *do* know is that with the packages (starting with "emgd-driver" when installing) in the screenshots, I am able to play most videos (Not 1080p, of course.) with SMPlayer (xv output driver), and when a 720p video lags, for the very most part mpv Media Player plays it perfectly. The file .mpv/config is placed in my home folder. My machine is ASUS1101HA, 1366x768px.

```

# Write your default config options here!

[default]
vo=xv
hwdec=vaapi
ao=alsa
vf=eq
autosync=30
video-zoom=-0.07
sub-auto=all
sub-visibility=yes
osd-font-size=30
sub-text-font-size=50
sub-text-border-size=4
sub-text-shadow-offset=3
sub-text-shadow-color='#FF000000'
sub-text-spacing=-1
osd-level=1
osd-shadow-offset=0
osd-duration=5000
slang=en
brightness=20
contrast=42
saturation=14
save-position-on-quit=yes
#cache=123400

[protocol.https]
#force-window=immediate

```

---

### Post by raul23 on 2015-09-17
Thank you very much, it is as good answer as I will probably get.
Do you use a special version of mplayer or just the one from repositories?

---

### Post by validust on 2015-09-17
It´s the mplayer from repo, raul23. You can see it in one of the screenshots. ;)

---

### Post by raul23 on 2015-09-19
Thank you very much :)

---

### Post by Jason_Pearn on 2016-01-01
Just thought I would post here with thanks. I spent some time setting up my Vaio P with Xubuntu and Lubuntu and configured the xorg.conf with correct settings from [http://pcloadletter.co.uk/2012/07/06/iemgd-for-vaio-p/](http://pcloadletter.co.uk/2012/07/06/iemgd-for-vaio-p/) for backlight / frequencies. After including the emgd-backlight-dkms package and a few other tweaks including removing light-locker (causing hangs after resume), blacklisting gma500_gfx, everything is working as it should be.

---

### Post by yoshi3142 on 2016-01-07
This may be a stupid question, but my colleague got hp slate2 working with emgd driver (including fluid fullscreen video playback, and decent framerate in unity on 14.04), but i cannot. 

Afaik both devices have gma600 chip, unless there is some minor difference in our tablets (which i have yet to narrow down). Anyone can share some info on whether gma600 should work or is it completely incompatible with this driver?

---

### Post by Edglex on 2016-01-15
I have just managed to get EMGD working with vaapi (accelerated video decoding) and 3D/2D acceleration in Xubuntu 14.04 on my vaio P. I'm quite happy because I didn't think it was actually possible to have vaapi working, and the P series can't really manage any video decoding using the CPU! Video playback is using kodi (xbmc).

I actually based this off of the joggler 14.04 images from Jools Willis available here: [http://jwills.co.uk/projects/joggler-xubuntu/](http://jwills.co.uk/projects/joggler-xubuntu/)

I took his joggler 14.04 image, and built my own 3.2.74 kernel with the emgd driver and patches for i2c, sound etc. This was necessary because his joggler kernel is stripped down so it didn't have support for my sata controller, wifi card or anything. There were also a few other hoops to jump through. I can post full instructions to reproduce it if anyone is interested.

I'm wondering if I should upload the rootfs image somewhere so that anyone can copy it onto their own system if they want to (I can post instructions). But I don't have any hosting, and it is big (like 4-5GB), and I'd really like it to go somewhere where it wont disappear in a couple of months. Could someone suggest somewhere to host it? Alternatively I could upload my kernel packages and some instructions to modify his image.

A tip: have an emgd ubuntu install alongside one using the open source driver (so you can use VGA out for presentations) and keep a shared /home partition :)

FYI, Jools also has a couple of repos with the required packages, but I broke my 14.04 install trying to get them working (I didn't try for long though):

[https://launchpad.net/~jools/+archive/ubuntu/emgd-xorg1.9](https://launchpad.net/~jools/+archive/ubuntu/emgd-xorg1.9)
[URL="https://launchpad.net/~jools/+archive/ubuntu/joggler"]https://launchpad.net/~jools/+archive/ubuntu/joggler


[/URL]

---

### Post by Jason_Pearn on 2016-01-17
Hi Edglex, I am interested in your version of Xubuntu as I have been playing around with mine now for the last couple of weeks but not got as far as you ! I have private space or if you can upload the kernel / instructions ? The P is a great machine which was overlooked many years ago :)

---

### Post by trs79 on 2016-01-18
Could others who are using EMGD please respond and let me know if they do or don't have tearing when graphics are moving horizontally? It's an effect similar to the one seen here: [https://web.archive.org/web/20160118200949/http://www.iwillfolo.com/wordpress/wp-content/uploads/2014/09/Nvidia-tearing.jpg](https://web.archive.org/web/20160118200949/http://www.iwillfolo.com/wordpress/wp-content/uploads/2014/09/Nvidia-tearing.jpg) You can really see it when moving a desktop window across the screen. I've tried a lot of different options in xorg.conf but nothing has prevented the tearing.

---

### Post by eisenstein10 on 2016-01-18
Hello,

I am currently working on getting this to run on Xubuntu trusty as well as debian jessie, on an Asus EeePC 1201 HA with GMA500

I ran into issues with the emgdbl module. It doesn't work on trusty while on jessie it won't even compile.

The debian install tells me to do a "make oldconfig && make prepare" in the kernel sources. But that gives other issues, making me think that the stock kernel 3.16.0.4-686-pae might be the wrong one for this driver. I didn't find older kernels in the repo. So, if I have to compile Kernel myself, I would be very grateful for any instructions related to the emgd driver configuration.

Status for both systems is about the same. SD Video works well, 720p Video is stuttering with an estimated framerate of 15-20 fps.
As mentioned, hotkeys dont work on both systems, but suspend/hibernation works in debian if ran from tty1 (pm-suspend), while wakeup will freeze most of the time, showing a black screen when suspended from graphical environment (XFCE). Need further research here. But, can be shut down with this [SysRQ]+REISUB thing.
Also no success so far in using libva, despite vainfo tells me something that seems correct to my noobie eyes. That makes me think that I just need to convince the system to actually use it but at this point no clue how to do so.

====================

Thanks alot to Mr Thopiear for keeping this driver alive =)

> **trs79 said:**
> Could others who are using EMGD please respond and let me know if they do or don't have tearing when graphics are moving horizontally? It's an effect similar to the one seen here: [https://web.archive.org/web/20160118200949/http://www.iwillfolo.com/wordpress/wp-content/uploads/2014/09/Nvidia-tearing.jpg](https://web.archive.org/web/20160118200949/http://www.iwillfolo.com/wordpress/wp-content/uploads/2014/09/Nvidia-tearing.jpg) You can really see it when moving a desktop window across the screen. I've tried a lot of different options in xorg.conf but nothing has prevented the tearing.

Not seen on my really slow Netbook running emgd

---

### Post by Edglex on 2016-01-23
> **Jason_Pearn said:**
> Hi Edglex, I am interested in your version of Xubuntu as I have been playing around with mine now for the last couple of weeks but not got as far as you ! I have private space or if you can upload the kernel / instructions ? The P is a great machine which was overlooked many years ago :)

Hi Jason, thats great. If you let me know details of where to upload I'll stick my kernel packages, kernel module and full system image on there. I also love the P and just wish I could find something more powerful in the same form factor. Also the battery life is a bit of a bummer (even with the extended battery).

For the vaio p I also have a working xorg.conf, and some lsfsb binaries and rc.local for overclocking.

I have another xorg.conf where vga was working, but you have to swap your xorg.conf files and restart X with the VGA connected, and it only supports 1024x768 mirrored. Since I worry about the reliability of this (and it's pretty limited) I prefer to boot a separate ubuntu install with xorg modesetting and the open source driver where xrandr is working properly, as I have plenty of space on my msata. Also, sleep etc works properly with the open source driver (with the work around).

> **eisenstein10 said:**
> Hello,

I am currently working on getting this to run on Xubuntu trusty as well as debian jessie, on an Asus EeePC 1201 HA with GMA500

I ran into issues with the emgdbl module. It doesn't work on trusty while on jessie it won't even compile.

The debian install tells me to do a "make oldconfig && make prepare" in the kernel sources. But that gives other issues, making me think that the stock kernel 3.16.0.4-686-pae might be the wrong one for this driver. I didn't find older kernels in the repo. So, if I have to compile Kernel myself, I would be very grateful for any instructions related to the emgd driver configuration.

Status for both systems is about the same. SD Video works well, 720p Video is stuttering with an estimated framerate of 15-20 fps.
As mentioned, hotkeys dont work on both systems, but suspend/hibernation works in debian if ran from tty1 (pm-suspend), while wakeup will freeze most of the time, showing a black screen when suspended from graphical environment (XFCE). Need further research here. But, can be shut down with this [SysRQ]+REISUB thing.
Also no success so far in using libva, despite vainfo tells me something that seems correct to my noobie eyes. That makes me think that I just need to convince the system to actually use it but at this point no clue how to do so.

====================

Thanks alot to Mr Thopiear for keeping this driver alive =)

Apparently anything much newer than trusty will be very difficult since udev and systemd have changed a lot, and xserver depends on these (you need the old 1.9 xserver for emgd to work).

You can try using my kernel and driver when I have uploaded it. They come as .deb packages. Also you could just try using my 14.04 image. kodi plays 720p very well (certainly for h264 anyway). Apparently using mplayer-vaapi 1080p will even work, but I haven't got a working install for this. On the vaio p the CPU isn't strong enough to even play SD video (and I have the "fast" 1.86GHz model), so EMGD is really important!

I've found suspend works using the open source driver and the "pm-suspend --quirk-vbemode-restore" quirk described here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

I haven't been able to get suspend to work consistently with the closed source driver, though the work around helps to the point that it works sometimes. 

I'm booted using the open source driver right now (because I'm working instead of watching videos :P) but when I next reboot I will post the output of vainfo.

Some other tips - try using opera 12 as a web browser - it's a bit quicker. You may also be able to over clock using lfsb. On my vaio p I use:

/sbin/modprobe i2c-dev
/usr/local/bin/lfsb -y ics9ums9610bl 150

To set the fsb to 150Mhz.

Edit Also there is stuff about hot keys on the ubuntu page. They are working fine for me on the vaio.

Here's the vainfo output:

```
libva: VA-API version 0.32.1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
Using XCB based dispatch table.
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.16)
vainfo: Driver version: Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointMoComp
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointMoComp
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointMoComp
```

---

### Post by eisenstein10 on 2016-01-25
Sorry for replying so late

Well I did alot of fiddling and got some things to work, while stuck on other things.

- Compositing works well, also in debian
- Suspend/resume works well. Hibernation doesnt work, I haven't investigated this any further so far.
- But there is an issue with logging out: Display freezes, but Machine can be reached via ssh. rmmod emgd && sservice lightdm restart fixes this but no tty1-6 after this point. I did a rather dirty workaround: added "rmmod emgd" to thopiekar's Xcompat script (/usr/bin/Xcompat) just one line before the X server is actually started.
- No success at all with emgdbl module, while asus_wmi works for most [Fn]-Keys but not backlight
- libva: phew. vainfo reports good looking output (actually the same as yours, if I recall correctly, currently on another machine) while still high CPU Load on playing Video and stuttering at 720p Material. So I guess Hardware-Decoding is available to the system but not used by the players. I did alot of research on topics like libva, libav, gstreamer, but since I'm not an expert at all I've been learning quite alot but no success in getting a nice Video decoding ;-)
- Found and fixed alot of missing XFCE-settings with the help of google: Unmuting didnt work, now works. Scrambled sound, now repaired. 

Overall state is: Desktops works well and very responsive, Sound works, Web Video works somehow, HD Video doesn't work. Netbook is ready for a second life if watching videos is not too important.

I'm going away from further investigating theese things now. I want to put all my steps needed into a single file for 1-command-reinstall onto another partition. This way I want to find out if my changes lead to a reproducible working system. That will take some time. However I'm going to try your tips. I will report if any success. But I am a slow man so .... :D

---

### Post by Edglex on 2016-01-25
For libva you need a player compiled to use it. There is a specially built version of kodi in one of the ppas I linked you to, and also a version of mplayer-vaapi for an earlier ubuntu release that I didn't install yet (I think this is also in Thopiekar's ppa?). kodi I think also has a youtube player and some other web video players (plugins anyway), I didn't try them yet but they should work I think. Are you building yourself or using Thopiekar's repo? I haven't been able to get vaapi working with his builds. He is using driver 1.16 and I have built 1.18, I don't know if that could have anything to do with it. What's your vainfo output?

I have different hardware but I don't think you want emgdbl. I have built a custom kernel with patches for backlight, sound and i2c, and it works well. I have an issue with the machine not muting the speakers when headphones are inserted (have to mute them manually), but I am sure this worked initially, I haven't investigated further.

Did you use any tricks to get suspend working? Here it results in a blank screen, or a screen filled with pretty much random pixels. When it does work resume often fails (though sometimes restarting lightdm blindly from a vt works). Also, shut down often crashes.

I have uploaded my kernel, emgd driver etc to Jason's owncloud site: [http://jpearn.ddns.net:81/owncloud/index.php/s/8zieckupIJ731g9](http://jpearn.ddns.net:81/owncloud/index.php/s/8zieckupIJ731g9)

Later this week I will add my vanilla system image to the site and post some instructions here with how to install it to a partition etc. The system has the correct xserver and other required packages, and kodi already installed. A bunch of packages are taken from earlier ubuntu releases and pinned. I tried to reproduce the whole thing on a plain xubuntu install but kept breaking the system. Later I built the kernel and emgd module, and I haven't tried them on a plain xubuntu install but it might be possible to get it to work using a combination of these modules and thopiekar's repo (and/or Jools Will's repo) . If you do want to try them, ignore the dkms errors when installing the kernel (unless you need any of the stuff dkms builds... in which case I think you're stuffed - I haven't investigated why it doesn't find the headers!). Then copy emgd.ko to /lib/modules/3.2.74-gma500/kernel/drivers/gpu/drm/emgd/ and run depmod -a.

---

### Post by eisenstein10 on 2016-01-25
Wow thats alot of instructions

I'm just about to install a new system on the 1201HA in order to get things reproduceable. 
Somehow I lost track of which application wants whatever library, so i installed and uninstalled a lot and now I suspect the system is messed up - at least I cant get any of the gstreamer pipelines to work that are supposed to deliver diagnostic output. I definitely need a clean system now.

Suspend/Resume: Well I changed some of the boot options but not sure if this was the reason. Information about grub and loaded modules follows. Can you ssh into the machine when it hangs? If so, you'll probably find useful information in dmesg.

I'm gonna download your kernel and try it as soon as i got a clean system. Thanks for that.

Output of vainfo:

```

libva info: VA-API version 0.34.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/emgd_drv_video.so
libva info: Found init function __vaDriverInit_0_32
Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.34 (libva 1.2.1)
vainfo: Driver version: Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
vainfo: Supported profile and entrypoints
      VAProfileNone                   :    <unknown entrypoint>
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG4Simple            :    VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointMoComp
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointMoComp
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointMoComp
      VAProfileJPEGBaseline           :    <unknown entrypoint>

```
Note that this is libva1.2.1. I tested thopiekar's Xserver-emgd-tizen which installed this version.

/etc/default/grub
```

...
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
...
[CODE]

lsmod
[CODE]
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
snd_hda_codec_realtek    69632  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
snd_hda_intel          32768  6 
gpio_sch               16384  0 
i2c_isch               16384  0 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
arc4                   16384  2 
coretemp               16384  0 
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
ath9k                 135168  0 
uvcvideo               73728  0 
kvm_intel             139264  0 
rfcomm                 61440  0 
bnep                   20480  2 
ath9k_common           32768  1 ath9k
videobuf2_vmalloc      16384  1 uvcvideo
bluetooth             430080  10 bnep,rfcomm
videobuf2_memops       16384  1 videobuf2_vmalloc
kvm                   413696  1 kvm_intel
videobuf2_core         49152  1 uvcvideo
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
v4l2_common            16384  1 videobuf2_core
videodev              139264  3 uvcvideo,v4l2_common,videobuf2_core
ath9k_hw              442368  2 ath9k_common,ath9k
snd_timer              28672  2 snd_pcm,snd_seq
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              618496  1 ath9k
joydev                 20480  0 
media                  24576  2 uvcvideo,videodev
serio_raw              16384  0 
snd                    69632  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_sch                16384  0 
cfg80211              450560  4 ath,ath9k_common,ath9k,mac80211
soundcore              16384  2 snd,snd_hda_codec
shpchp                 32768  0 
mac_hid                16384  0 
emgdbl                 16384  0 
video                  20480  0 
parport_pc             32768  0 
sparse_keymap          16384  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
psmouse               102400  0 
pata_sch               16384  2 
emgd                  577536  4 
drm_kms_helper        114688  1 emgd
atl1c                  45056  0 
drm                   282624  7 emgd,drm_kms_helper

```

---

### Post by Edglex on 2016-01-26
Hmm, well it looks as though you have libva working! Also, it is version 1.18. I'd be interested to hear your process. Perhaps I should give Thopiekar's install another try. Good luck with the rebuild!

---

### Post by eisenstein10 on 2016-01-26
Lets be stated: If you use thopiekars archive and simply install the emgd-driver packacke, this will get you the xserver-xorg-1.9-video-emgd-megoo1.2 driver plus libva1.0.16

It was one of my last tests to manually install the xserver-xorg-1.0-video-emgd-tizen driver from the same archive, which installs libva1.2.1, But at this point I had already messed my system and too many issues. So thats why I decided to make a fresh install. I'll do that today.

Thopiekar's packages are somewhat messed on their own, I think. Just packaging problems but because of that you first need to get a working environment with open source driver, then install the emgd-driver which will replace some of the packages. Thats why I loose track of which libraries are actually installed and used on the system.

My idea is to get a minimal list of packages that I definitely need for my specific system, call them "hardware-related", put them in a script which installs this minimal system, and on top of this I'd like to install a desktop with standard packages. Working on this.

---

### Post by Edglex on 2016-02-03
@[**[COLOR=#000000]eisenstein10[/COLOR]**]("http://ubuntuforums.org/member.php?u=2017380") how did you get on with your reinstall?

Another tip - I've been using the pale moon browser built for atom [http://linux.palemoon.org/download/atom/](http://linux.palemoon.org/download/atom/)

It works reasonably well, still not an amazing browsing experience, but better than FF or chrome. The old opera build still seems to be king (but there are probably security issues with it).

---

### Post by validust on 2016-02-05
Thank you for the tip, Edglex! The first thing I noticed when starting Pale Moon was how smooth the scrolling is. And it is faster.
An oddity: After having signed in to youtube, I got an email from google saying that someone had signed in there (to youtube) with a google account, from Windows, Firefox 31.9...
- That was me, of course, though I´m reasonably sure that ubuntu-mate 14.04 is linux. ;)

"Pale Moon uses a Windows Firefox 31.9 user agent for Google/YouTube  sites (due to some compatibility issues that Google is not interested in  fixing)." Oh. :)

---

### Post by davide19 on 2016-02-18
Hi! I'm using Asus eeepc 1201HA. I've installed ubuntu studio 14.04 on. 
EMGD Driver seems to works, I follow this guide 
[http://andre.blaatschaap.be/2015/03/installing-xubuntu-on-an-asus-eeepc-1201ha/](http://andre.blaatschaap.be/2015/03/installing-xubuntu-on-an-asus-eeepc-1201ha/) 
where I get to know this driver. The only stuff that doesn't work is backlight... I tried to install with apt EMGD-backlight package, but nothing worked. Using fn+ backlight combination show the "backlight changing small window", but backlight standing still.

after setting on /etc/default/grub
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"

```
on /sys i found backlight files:
```

dario@dario-1201HA:~$ find /sys -iwholename *bright*
/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/leds/ath9k-phy0/brightness
/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/leds/ath9k-phy0/max_brightness
/sys/devices/platform/eeepc/leds/eeepc::touchpad/brightness
/sys/devices/platform/eeepc/leds/eeepc::touchpad/max_brightness
/sys/devices/platform/eeepc/backlight/eeepc/brightness
/sys/devices/platform/eeepc/backlight/eeepc/max_brightness
/sys/devices/platform/eeepc/backlight/eeepc/actual_brightness
find: "/sys/kernel/debug": Permesso negato
/sys/module/video/parameters/brightness_switch_enable

```

I tried to change the brightness files in there but it seems not working (I read on some forums that sometimes it works)

Suspend on ram working by defaut instead ^^

can anybody help me? :D

---

### Post by Edglex on 2016-02-18
Try my kernel build I posted further up this page. There are some patches in it for backlight. Install the headers first, and ignore the dkms errors when installing. Then copy emgd.ko to /lib/modules/3.2.74-gma500/kernel/drivers/gpu/drm/emgd/ and run "depmod -a".

---

### Post by davide19 on 2016-02-19
I tried and it didn't work :(:cry::cry::cry:

---

### Post by validust on 2016-02-19
Hi davide19! My machine is a cousin of yours; ASUS 1101HA. Quite a while ago I installed thopiekars emgd 1.16 in ubuntu-mate-14.04. It has worked splendidly, and does so in ubuntu-mate-16.04 too. (Cannot vouch for "suspend-to-ram", since I´ve never tried it.) I have kernel 4.2.0-22-generic installed. The kernel before that was 3.16.0-41-generic. Don´t know how the ones in between functions.
[https://launchpad.net/~thopiekar/+archive/ubuntu/emgd](https://launchpad.net/~thopiekar/+archive/ubuntu/emgd)
About backlight: When I mimicked your command, the result was somewhat different
```
          find /sys -iwholename *bright*
/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/leds/ath9k-phy0/brightness
/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/leds/ath9k-phy0/max_brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::scrolllock/brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::scrolllock/max_brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::capslock/brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::capslock/max_brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::numlock/brightness
/sys/devices/platform/i8042/serio0/input/input3/input3::numlock/max_brightness
/sys/devices/platform/emgd_psb/backlight/emgd_psb/brightness
/sys/devices/platform/emgd_psb/backlight/emgd_psb/max_brightness
/sys/devices/platform/emgd_psb/backlight/emgd_psb/actual_brightness
```

Also, in my setup there is a file "/sys/class/backlight/emgd_psb/brightness", which can be used (as root) to change brightness value. Maybe, *maybe* you too have it. And while it needs to be set after each boot, it would make it easier on the eyes while you try this and that.
Good luck! :)

Just remembered, I *think* that it is important to remove all existing emgd files before installing the packages of thopiekars emgd 1.16.

---

### Post by davide19 on 2016-02-21
so.... I tried the kernel 4.2.0-22 and brightness keep not working... :(
do you use the flags about acpi and brightness on /etc/default/grub ??
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
Using fn+f5/f6 for brightness modification without it doesn't do anything, with the grub flags it changes the files about brightness, show the small window on the up-right corner, but it doesn't modify the actual brightness.

On the machine are running ubuntu studio 14.04, using low latency kernel. I don't know why with 4.2.0-22-generic give me some issue on boot, it cannot find partition uuid so I giveup about that 
Every time I install the packages of linux (headers... image...) dkms, i guess, recompile and install the emgd, 3d rendering keep working. 

Another problem is logout, and sometimes also "shutting off" or suspending the system display came black and all freezes... I cannot go also on tt1 (altr+ctrl+F1...F6 does not work. I enable alt+ctrl+backspace but it also not working
> [COLOR=#000000][INDENT]Just remembered, I *think* that it is important to remove all existing emgd files before installing the packages of thopiekars emgd 1.16.[/INDENT]
[/COLOR]

I think dkms do that itself :/

---

### Post by validust on 2016-02-21
```
GRUB_CMDLINE_LINUX=""
```

That thing about hanging/screen blanking when rebooting/halting; I gave up finding a solution a long time ago. Maybe it worked with the pre-installed Windows. Since then I have nibbled on some 15-20 distros, and it has always been the same. Sometimes it works, often it doesn´t. Could be that it´s a hardware issue? The only time that I need to go back and let the shut-down go through properly, is when I want to make an image of the partition, using "partimage" (which is dependent on ext3).

The Fn+F5/F6 doesn´t do anything on the OS for me. (But it has effect on the boot screen.) I use either the "Power Management Preferences" or the MATE brightness icon.

This is intriguing. Have started a torrent dl of the mammoth ubuntu studio 14.04.4 *32bit*  :) And we shall see what we shall see.

---

### Post by validust on 2016-02-21
Got it to work. With your /etc/default/grub-youknow, I installed 3.16.0-41-generic, and it brought along a folder /eeepc to /sys/class/backlight.
When I opened ubuntu studio with 4.2.0-27-latency again, there it was. And functioning. :)  
That was the short version. ;)

---

### Post by validust on 2016-02-22
If, davide19, you get it to work with the emgd variant that you have, then good and well.
If, on the other hand, it doesn´t, this is how I did it:
Installed ubuntu studio 14.04.4 on a 14GB partition. Kernel 4.2.0-27-lowlatency.
Installed thopiekars emgd 1.16. When marking emgd-driver, many of the other emgd packages gets marked too. I don´t know which of the rest of the emgd packages are necessary. On page 5 in this thread there are screenshots of the packages I installed.
Placed the file /10-emgd.conf in /usr/share/xorg.conf.d

```
Section "ServerLayout"
     Identifier     "Default Layout"
     Screen 0       "Screen0"        0 0 
EndSection

Section "Device"
     Identifier                                           "Intel_EMGD-0"
     Driver                                               "emgd"
     VendorName                                           "Intel(R) DEG"
     BoardName                                            "Embedded Graphics"
     BusID                                                "0:2:0"
     Screen                                               0
     VideoRAM                                             131072
     Option     "PcfVersion"                              "1792"
     Option     "ConfigId"                                "1"
     Option     "PortDrivers"                             "lvds"
     Option     "ALL/1/name"                              "lvds-display"
     Option     "ALL/1/General/DisplayConfig"             "1"
     Option     "ALL/1/General/DisplayDetect"             "1"
     Option     "ALL/1/Port/4/General/name"               "LVDS"
     Option     "ALL/1/Port/4/General/Edid"               "1"
     Option     "ALL/1/Port/4/Attr/70"                    "0"
     Option     "ALL/1/General/Accel"                     "1"
EndSection

Section "Screen"
     Identifier    "Screen0"
     Device        "Intel_EMGD-0"
     Monitor       "LVDS"
     SubSection    "Display"
          Depth     24
          Modes    "1366x768"
     EndSubSection

EndSection

Section "Monitor"
     Identifier   "LVDS"
     ModelName    "LCD Panel used by EMGD" 
EndSection

Section "DRI"
     Mode         0666
EndSection

Section "Extensions"
     Option "composite" "enable"
EndSection
```


Rebooted. Pasted GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" in /etc/default/grub.
Installed kernel 4.2.0-22-generic. Rebooted. Highlighted "Advanced options for Ubuntu". Clicked ENTER. Highlighted 4.2.0-22-generic. Clicked ENTER. It took some time to get to login... And the brightness whatsit did *not* appear.
Installed kernel 3.16.0-41-generic, and went through the same steps as with 4.2.0-22.
When I had the desktop loaded, and did Fn+F6, I just gaped. There it was! And it worked!
And when I rebooted, and chose 4.2.0-27-lowlatency, it was still there.

That was the somewhat longer version. I´m really curious to see how this works for you.

---

### Post by Edglex on 2016-06-26
I've been using my vaio p a bit more lately, and am finding that just using gma500 is a bit more useful than fussing with emgd. The beta opera version works quite well, hibernation works (but make sure you have a swap partition not a swap file), VGA out works for presentations, and I even figured out that you can enable the 3G and GPS in new kernel versions without needing to install anything extra [1]. Not sure if I'm imagining it but battery life even seems better.

I am wondering if the way forward is to install XP and instant mode, so that I can watch videos in instant mode and play the odd game in XP. Instant mode is linux anyway, perhaps there is a way to increase the filesystem size and customise it a bit. Really though, if I want to watch a video or play games I can fire up my tablet. The strength of the vaio is allowing me to do work and being really portable, and I don't need to watch videos for that.

The other thing I've want to try out is opera mini. It's a java phone app but works in an emulator. It sends web page requests to opera's servers which render and compresse them before sending them back, so it should relieve the laptop of the rendering effort. Would be nice if there was an open source equivalent so I could install a page renderer on a home machine and just point the client on the vaio to it. 

[1] Unblock the card:
 sudo modprobe sony-laptop
 sudo rfkill unblock 10

 If it works, you should find the 3G card appears in network mangler. Also, ttyHS0 up to ttyHS6 should appear in /dev/. To enable GPS, open /dev/ttyHS4 at 9600 and type "AT_OGPS=2". There is no echo with what you type, but you should get "OK" back, and if you open /dev/ttyHS1 you'll see NMEA data coming through. "AT_OGPS=0" turns it off again. If you set it to 1 it has some other sort of mode (position only?)

EDIT:
I haven't used this since I last posted and now I've looked at it again I've found that the "sudo rfkill unblock 10" doesn't always work because the ID of the wwan card changes. So the following should be used instead (use grep/sed to get the ID of the wwan card and unblock that ID):

sudo rfkill unblock `rfkill list | grep sony-wwan | sed 's/\([0-9]*\):.*/\1/'`

---

### Post by ddurdle on 2016-06-26
> **Edglex said:**
> I've been using my vaio p a bit more lately, and am finding that just using gma500 is a bit more useful than fussing with emgd. The beta opera version works quite well, hibernation works (but make sure you have a swap partition not a swap file), VGA out works for presentations, and I even figured out that you can enable the 3G and GPS in new kernel versions without needing to install anything extra [1]. Not sure if I'm imagining it but battery life even seems better.

I am wondering if the way forward is to install XP and instant mode, so that I can watch videos in instant mode and play the odd game in XP. Instant mode is linux anyway, perhaps there is a way to increase the filesystem size and customise it a bit. Really though, if I want to watch a video or play games I can fire up my tablet. The strength of the vaio is allowing me to do work and being really portable, and I don't need to watch videos for that.

The other thing I've want to try out is opera mini. It's a java phone app but works in an emulator. It sends web page requests to opera's servers which render and compresse them before sending them back, so it should relieve the laptop of the rendering effort. Would be nice if there was an open source equivalent so I could install a page renderer on a home machine and just point the client on the vaio to it. 

[1] Unblock the card:
 sudo modprobe sony-laptop
 sudo rfkill unblock 10

 If it works, you should find the 3G card appears in network mangler. Also, ttyHS0 up to ttyHS6 should appear in /dev/. To enable GPS, open /dev/ttyHS4 at 9600 and type "AT_OGPS=2". There is no echo with what you type, but you should get "OK" back, and if you open /dev/ttyHS1 you'll see NMEA data coming through. "AT_OGPS=0" turns it off again. If you set it to 1 it has some other sort of mode (position only?)

Yes, I've been using the opensource GMA500 drivers in Debian on this machine for the past 2 years (first wheezy, then jessie).  It works relatively well.  Even some transparency works.  Video playback is poor.  KODI performance likewise.

---

### Post by Edglex on 2016-07-06
Despite only just figuring out how to use it, I've decided to ditch the 3G/GPS card in my machine and put a Broadcom Crystal HD (BCM70015) in there instead. This is a mini pci-e card that can decode HD video, so you don't need a good GPU. Driver support seems a bit stale, but hopefully easier to get going (and without so many caveats) as the GMA500. I'll report back here at some point with how that goes.

---

### Post by Edglex on 2016-11-21
[s]Just a quick note to say that the crystal HD card works really well (with drivers from here [https://github.com/dbason/crystalhd](https://github.com/dbason/crystalhd), note the error in git clone line of the readme, and make sure to apt-get install firmware-crystalhd). With the crystal HD you're good to upgrade to ubuntu 16.04 as well (which will no longer work with any proprietary GMA500 drivers at all). The crystal HD installation process is much easier than trying to get proprietary GMA500 working.

The only issue is flash video doesn't work, though it supposedly should with firefox, but even then only until April 2017. For that reason I can't be bothered to follow up on it, there's always youtube-dl or one of the many flash video downloader plugins for that.[/s]

The crystal HD has bad tearing, because the open gma500 driver is slow at painting the screen, and I can't find a way to get it to synchronise to vsync. I'm still hoping to find a solution, but not had any luck so far (the best way seems to be to use vlc from a framebuffer console, but it is a bit of a faff and far from perfect). I'm going to try building mplayer with crystal HD support, which I hope may help. It's kind of insane that even when a piece of hardware is providing the video uncompressed, it still can't draw it to the screen fast enough.

On the plus side, I've discovered that I can use remote X forwarding from a workstation at home to get a really good web browsing experience. Just use ```
ssh -YC4c arcfour,blowfish-cbc user@host firefox -no-remote
```
This makes the machine feel basically as fast as any other for browsing. Oddly enough watching e.g. youtube videos works fairly well, but they still tear and I have no sound (that is apparently possible, not sure what performance will be like  [http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh](http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh)).

EDIT: The below works better for running firefox, it causes the ssh session to close properly when firefox exits:
```
ssh -YC4c arcfour,blowfish-cbc user@host 'export \`dbus-launch\`; dbus-launch firefox -no-remote; kill -TERM $DBUS_SESSION_BUS_PID'
```

---

### Post by Adam_GUI on 2017-01-11
Bump?  I think Theopiekar is still maintaining this.
What are the current install procedures?

I've been itching to install something to have on this old Dell Mini 1010 machine.
If I can get the emgd running, great.  If not, I guess it's good for stuff as long as it's not video.

---

### Post by punkidd on 2017-03-01
> **davide19 said:**
> so.... I tried the kernel 4.2.0-22 and brightness keep not working... :(
do you use the flags about acpi and brightness on /etc/default/grub ??
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
Using fn+f5/f6 for brightness modification without it doesn't do anything, with the grub flags it changes the files about brightness, show the small window on the up-right corner, but it doesn't modify the actual brightness.

On the machine are running ubuntu studio 14.04, using low latency kernel. I don't know why with 4.2.0-22-generic give me some issue on boot, it cannot find partition uuid so I giveup about that 
Every time I install the packages of linux (headers... image...) dkms, i guess, recompile and install the emgd, 3d rendering keep working. 

Another problem is logout, and sometimes also "shutting off" or suspending the system display came black and all freezes... I cannot go also on tt1 (altr+ctrl+F1...F6 does not work. I enable alt+ctrl+backspace but it also not working

I think dkms do that itself :/


Hi man !
I'm a really new user from linux world and I've been researching a way to improve my  old Asus Eeepc 1201HA...
I saw a few things here but , really don't understand nothing. Could you, or someone help me :}

My main objective , is to watch at least 720p videos ( using stremio,popcorntime,netflix web,youtube - or kodi , cause I don't use it since it was XBMC).}
right now I'm using Xubuntu 16.10, and resuming, it's ok, really functional and faster than crappy w7 default.But even the display been fine I can't play videos, streaming or local.

I really want to learn how to improve this machine, if somemone help's me I buy a coffee :)

---

### Post by cariboo on 2017-03-01
> **punkidd said:**
> Hi man !
I'm a really new user from linux world and I've been researching a way to improve my  old Asus Eeepc 1201HA...
I saw a few things here but , really don't understand nothing. Could you, or someone help me :}

My main objective , is to watch at least 720p videos ( using stremio,popcorntime,netflix web,youtube - or kodi , cause I don't use it since it was XBMC).}
right now I'm using Xubuntu 16.10, and resuming, it's ok, really functional and faster than crappy w7 default.But even the display been fine I can't play videos, streaming or local.

I really want to learn how to improve this machine, if somemone help's me I buy a coffee :)


Your best bet would be to start a new thread on your problem. Lets us know the specifications of your system eg:

[LIST]
[*]CPU
[*]Ram
[*]Graphics adapter
[/LIST]

Also let us know what you have tried yourself.

---

### Post by punkidd on 2017-03-02
> **cariboo said:**
> Your best bet would be to start a new thread on your problem. Lets us know the specifications of your system eg:

[LIST]
[*]CPU
[*]Ram
[*]Graphics adapter
[/LIST]

Also let us know what you have tried yourself.




Assus Eeepc 1201 HA 
-[Intel Atom Z520]("http://www.notebookcheck.info/Intel-Atom-Z520-Notebook-Processor.33025.0.html") 1.333 GH
-2gb
-[Intel Graphics Media Accelerator (GMA) 500]("http://www.notebookcheck.info/Intel-Graphics-Media-Accelerator-GMA-500.17145.0.html")

Well, I've tried to use Lubuntu 16.04 (x86) just to see if a lighter system than w7 can do more for this old netbook, and it is much more smother than w7. But any videoplayback it's lagy and shuttering... After that, I saw a video , and someon sugested Xubuntu , and it's the same experience.
The display still in 1360x768 and the images are great, but the video processing is realy laggy. I've tried to use diferente programs and soft solutions , but since I research a little bit more ,  I see there is much more pratical look for answers here.

As I told, I'm really new user of LInux , so I'm trying to understand how things work and how I can do my project.

---

### Post by cariboo on 2017-03-02
Did you check out the link in post #2?

[https://ubuntuforums.org/showthread.php?t=2107593&p=12468454&viewfull=1#post12468454](https://ubuntuforums.org/showthread.php?t=2107593&p=12468454&viewfull=1#post12468454)

---

### Post by punkidd on 2017-03-06
> **cariboo said:**
> Did you check out the link in post #2?

[https://ubuntuforums.org/showthread.php?t=2107593&p=12468454&viewfull=1#post12468454](https://ubuntuforums.org/showthread.php?t=2107593&p=12468454&viewfull=1#post12468454)



Thanks man!!

I skiped this post by mistake . I'll try thoose fix and when I finish, will report here ;)

---

### Post by ipderek on 2017-03-21
Just want to give my 2 cents.

It is a workable solution, but not perfect.

1. backlight is still not working
2. sleep &/or suspense to ram is not working.

follow this link
[http://www.fit-pc.com/wiki/index.php/Linux_Mint_13_on_fit-PC2](http://www.fit-pc.com/wiki/index.php/Linux_Mint_13_on_fit-PC2)
 to prepare downgrading xorg to 1.9, but don't use the ubuntu old repo because xserver will be fail to install.

from this site to add PPA
[https://launchpad.net/~thopiekar/+archive/ubuntu/emgd](https://launchpad.net/~thopiekar/+archive/ubuntu/emgd)

install xorg 1.9, emgd driver (default will install meego version, i prefer to use fedora, both should work), flashplayer plugin and emgd blacklight (but not working)

blacklist psb_gfx and gma500_gfx

xorg.conf

Section "Device"
    Identifier "Intel EMGD"
    Driver     "emgd"
    VendorName "Intel(R)"
    BoardName  "Embedded Graphics"
    BusID      "0:2:0"
    Screen      0
    Option     "PcfVersion"                          "1792"
    Option     "ConfigId"                            "1"
    Option     "ALL/1/name"                          "Northville"
#    Option     "ALL/1/General/VideoRAM"              "32768"
    Option     "ALL/1/General/PortOrder"             "40000"
#    Option     "ALL/1/General/DisplayConfig"         "1"
    Option     "ALL/1/General/DisplayDetect"         "1"
    Option     "ALL/1/General/TuningWA"       "1"
    Option     "ALL/1/Port/4/General/name"           "LVDS"
    Option     "ALL/1/Port/4/General/EdidAvail"      "1"
#    Option     "ALL/1/Port/4/General/EdidNotAvail"   "4"
#    Option     "ALL/1/Port/4/General/Rotation"       "0"
    Option     "ALL/1/Port/4/General/Edid"           "1"
    Option     "ALL/1/Port/4/FpInfo/BkltMethod"      "0"
    Option     "ALL/1/Port/4/Dtd/1/PixelClock"       "33231"
    Option     "ALL/1/Port/4/Dtd/1/HorzActive"       "1024"
    Option     "ALL/1/Port/4/Dtd/1/HorzSync"         "64"
    Option     "ALL/1/Port/4/Dtd/1/HorzSyncPulse"    "128"
    Option     "ALL/1/Port/4/Dtd/1/HorzBlank"        "256"
    Option     "ALL/1/Port/4/Dtd/1/VertActive"       "600"
    Option     "ALL/1/Port/4/Dtd/1/VertSync"         "21"
    Option     "ALL/1/Port/4/Dtd/1/VertSyncPulse"    "2"
    Option     "ALL/1/Port/4/Dtd/1/VertBlank"        "45"
    Option     "ALL/1/Port/4/Dtd/1/Flags"            "0x20000"
    Option     "ALL/1/Port/4/Attr/26"                "32"
    Option     "ALL/1/Port/4/Attr/60"                "1"
    Option     "ALL/1/Port/2/General/name"           "VGA"
    Option     "ALL/1/Port/2/General/EdidAvail"      "1"
#    Option     "ALL/1/Port/2/General/EdidNotAvail"   "5"
#    Option     "ALL/1/Port/2/General/Rotation"       "0"
    Option     "ALL/1/Port/2/General/Edid"           "1"
#    Option     "ALL/1/Port/2/FpInfo/BkltMethod"      "0"
#    Option     "ALL/1/Port/2/Dtd/1/PixelClock"       "33231"
#    Option     "ALL/1/Port/2/Dtd/1/HorzActive"       "800"
#    Option     "ALL/1/Port/2/Dtd/1/HorzSync"         "64"
#    Option     "ALL/1/Port/2/Dtd/1/HorzSyncPulse"    "128"
#    Option     "ALL/1/Port/2/Dtd/1/HorzBlank"        "256"
#    Option     "ALL/1/Port/2/Dtd/1/VertActive"       "600"
#    Option     "ALL/1/Port/2/Dtd/1/VertSync"         "21"
#    Option     "ALL/1/Port/2/Dtd/1/VertSyncPulse"    "2"
#    Option     "ALL/1/Port/2/Dtd/1/VertBlank"        "45"
#    Option     "ALL/1/Port/2/Dtd/1/Flags"            "0x20000"
#    Option     "ALL/1/Port/2/Attr/26"                "32"
#    Option     "ALL/1/Port/2/Attr/60"                "1"
    Option     "PortDrivers"                         "lvds sdvo"
EndSection

#Section "ServerFlags"
#     Option "Xinerama" "True"
#EndSection


Change these 2 lines according to your machine resolution.

Option "ALL/1/Port/4/Dtd/1/HorzActive" "1024"
Option "ALL/1/Port/4/Dtd/1/VertActive" "600"

24bit the screen not that good.
Option "ALL/1/Port/4/Attr/26" "32"

---

### Post by ipderek on 2017-03-21
Mine is lubuntu 16.04

---

### Post by ipderek on 2017-03-21
if you are planning not to use the machine more than 5 mins, please log out, otherwise, the screen will freeze.

reboot is the only solution.

---

### Post by ipderek on 2017-03-21
Use lubuntu 16.04 gnome mplayer to play 720p just fine.

Use Opera latest stable to watch youtube, but not firefox although i switch youtube to use flashplayer.

---

### Post by ipderek on 2017-03-21
Thanks Otacon from forum.ubuntu.org.cn for providing a workable xorg.conf.

Thanks Irads from fit-pc.com for proding wiki.

 A big thank to Thomas Karl Pietrowski for providing latest EMGD driver, xorg 1.9 and flashplayer plugin

---

### Post by ipderek on 2017-03-22
Just found a list of sample xorg.conf from Github.  Have to thank Thomas Karl Pietrowski again!!!

[https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf](https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf)

---

### Post by Edglex on 2017-10-12
I've noticed that thopiekar is still supporting this for recent ubuntu versions, so I decided to upgrade to xubuntu 16.04 and try to get it working. After install I simply added his ppa and did "apt-get install emgd-driver", and copied my xorg.conf in place. However, it seems that it failed to build the emgd.ko module, as the system wont finish booting, and trying to start X in recovery mode it tells me that the module is missing (which it indeed appears to be).

Does anyone know a procedure to make this work? I'm currently installing kernel 4.4.0-97 to see if that will work, as 4.4.0 is the earliest kernel available with 16.04.

Do I need a custom kernel, or to install one from an earlier ubuntu release?

EDIT: Ok, you just need to add the ppa, install emgd-driver then install linux-image-4.4.0-97-lowlatency, linux-headers-4.4.0-97 and linux-headers-4.4.0-97-lowlatency and everything seems to work.

My hope is that with emgd and the crystal hd mini pcie card watching 1080p video up to h264 should work great... fingers crossed!

Thanks yet again thopiekar!

EDIT2:
Just some more notes.

The audio stutter problem (related to gma500 chipset?) causes mplayer to go too slowly as well audio to be unusable. I've seen a few others mention it and I have the fix noted down (can't remember where I found it), but what you need to do is open /etc/pulse/default.pa and change the (uncommented) line "load-module module-udev-detect" and change it to "load-module module-udev-detect tsched=0 ". Then restart pulse audio with "pulseaudio -k".

I have ffmpeg and mplayer built with crystalhd support, and the crystalhd driver installed. With the audio problem fixed, emgd working, and crystal hd support, mplayer works perfectly right up to 1080p for everything except h265 (which it can't decode). You need to make the crystalhd codecs have priority before other codecs, by specifying the option "-vc ffmpeg2crystalhd,ffdivxcrystalhd,ffwmv3crystalhd,ffvc1crystalhd,ffh264crystalhd,ffodivxcrystalhd", and use xv for video output. You can specify these options in many mplayer GUIs, I'm using smplayer for example.

EDIT3:
One more thing, opengl wasn't working, I kept getting the software rasterizer with mesa. It's taken a few hours for me to figure out that a symlink had the wrong name! Running "sudo mv /usr/lib/i386-linux-gnu/dri/emgd_dri.so.so /usr/lib/i386-linux-gnu/dri/emgd_dri.so" fixed it.

---

### Post by Edglex on 2018-03-16
Interestingly I installed libva from thopiekar's repo and it looks to be working. At least vainfo gives:

libva: VA-API version 0.32.1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
Using XCB based dispatch table.
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.16)
vainfo: Driver version: Intel(R) Embedded Media and Graphics Driver 1.18 Build 3398
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG4Simple            :    VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointMoComp
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointMoComp
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointMoComp

But I didn't find a player yet that can use it. Might have to build one.

---

