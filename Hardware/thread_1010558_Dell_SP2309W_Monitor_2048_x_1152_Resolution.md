---
title: "Dell SP2309W Monitor 2048 x 1152 Resolution"
date: 2008-12-13
forum: Hardware
---

### Post by undoIT on 2008-12-13
I am checking out the new Dell SP2309W monitor with 2048 x 1152 resolution and I am wondering if it is possible to run this monitor at full resolution with Ubuntu. I currently own an XPS M1330 laptop with X3100 graphics card and a MacBook 5,1 with Nvidia GeForce 9400m. I use the M1330 as my primary laptop and would like to connnect it to the SP2309W with an HDMI cable. Not sure if the X3100 is capable of 2048 x 1152, but I know that the 9400m is.

Anyhow, I'm wondering if anyone with Ubuntu and a laptop has purchased this monitor and if they are able to run it at full resolution?

---

### Post by jedsmallwood on 2008-12-23
I have been able to run this monitor at full resolution with an updated ubuntu 8.10.  I'm running on a desktop with an embedded nvidia card, if that matters at all.  Out of the box, 8.10 does not identify the monitor correctly.  Getting the latest set of updates allows the system to identify the monitor, there was a specific update to the hwdata package for a whole slew of Dell monitors near the end of October.

While my motherboard does have an HDMI out, I haven't been able to get video out of it so my experience has just been with the DVI link.  I think that its a motherboard problem as opposed to an Ubuntu problem.  I had the same issue running Vista.


Overall, I'm satisfied with the monitor and would recommend it.

---

### Post by gcshum on 2008-12-30
Are you able to make the built-in mic work? If you can, please let me know how to do it. I'm using Ubuntu Hardy. The built-in webcam works automatically.

Thanks.

---

### Post by forestcomber on 2009-04-25
I'm running Ubuntu 9.04 on an Asus eee PC 901.  The resolution is perfect at 2048 x 1152.  The webcam works perfectly.  But I can't get the microphones to work !!

Anyone have any luck ?

---

### Post by shekhark on 2009-10-11
I haven't been able to extend the monitor beyond 1680x1050 and would like to use 2048x1152 resolution in 9.04 Jaunty. How might I do this? Do I need to add entries to xorg.conf?

---

### Post by funmler on 2009-10-18
I had the exact same problem. My new Dell SP2309W Monitor would not display 2048 x 1152 Resolution when using DVI

I traced the problem to a busted maximum pixiel clock check.

Here is my xorg.conf. 

The important bit was the 
        Option "ModeValidation" "NoMaxPClkCheck"


```
Section "Monitor"
        Identifier "DELL SP2309W"
        VendorName "DELL"
        ModelName "DELL SP2309W"
        HorizSync 30-92
        VertRefresh 56-85
        Mode    "2048x1152"     # vfreq 59.909Hz, hfreq 70.992kHz
        DotClock        156.75
        HTimings        2048 2096 2128 2208
        VTimings        1152 1155 1160 1185
        Flags    "+HSync" "-VSync"
        EndMode
        #                DotClock        156.750000
        #                Flags   "-HSync" "+VSync"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "DELL SP2309W"
        DefaultDepth    24
        Option   "AddARGBGLXVisuals"   "true"
        Option "ModeValidation" "NoMaxPClkCheck"
        SubSection "Display"
                Modes "2048x1152"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        Option         "NoLogo" "yes"
        Option         "RenderAccel" "true"
        Option         "AllowGLXWithComposite" "true"
        Option         "Backingstore" "true"
        Option         "XAANoOffscreenPixmaps"   "true"
        #    Option         "TripleBuffer"   "true"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

```For any one that is interested here is the Xlog that tells me what the problem is. Gotten by running 
startx -- verboselog = 6

```

...
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GS at PCI:3:0:0:
(--) NVIDIA(0):     DELL SP2309W (DFP-0)
(--) NVIDIA(0): DELL SP2309W (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL SP2309W (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): DELL SP2309W (DFP-0): Native FlatPanel Scaling is supported
(--) NVIDIA(0): DELL SP2309W (DFP-0): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): DELL SP2309W (DFP-0): DFP is not internal to notebook
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for DELL SP2309W (DFP-0) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : DEL
(--) NVIDIA(0): Monitor Name                 : DELL SP2309W
(--) NVIDIA(0): Product ID                   : 53276
(--) NVIDIA(0): 32-bit Serial Number         : 811160659
(--) NVIDIA(0): Serial Number String         : U783F97V0YTS
(--) NVIDIA(0): Manufacture Date             : 2009, week 31
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 510mm x 290mm
(--) NVIDIA(0): Valid HSync Range            : 30.0 kHz - 92.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 56 Hz - 85 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 170.0 MHz
(--) NVIDIA(0):
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 75 Hz
(--) NVIDIA(0):
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1152 x 864  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 60 Hz
(--) NVIDIA(0):   1680 x 1050 @ 60 Hz
(--) NVIDIA(0):
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   2048 x 1152 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 156.75 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2048, 2096
(--) NVIDIA(0):     HSyncEnd, HTotal : 2128, 2208
(--) NVIDIA(0):     VRes, VSyncStart : 1152, 1155
(--) NVIDIA(0):     VSyncEnd, VTotal : 1160, 1185
(--) NVIDIA(0):     H/V Polarity     : +/-
(--) NVIDIA(0):
(--) NVIDIA(0):
(--) NVIDIA(0): Raw EDID bytes:
(--) NVIDIA(0):
(--) NVIDIA(0):   00 ff ff ff ff ff ff 00  10 ac 1c d0 53 54 59 30
(--) NVIDIA(0):   1f 13 01 03 80 33 1d 78  ea 18 55 a9 53 37 ad 25
(--) NVIDIA(0):   13 50 54 a5 4b 00 71 4f  81 80 b3 00 01 01 01 01
(--) NVIDIA(0):   01 01 01 01 01 01 3b 3d  00 a0 80 80 21 40 30 20
(--) NVIDIA(0):   35 00 fe 22 11 00 00 1a  00 00 00 ff 00 55 37 38
(--) NVIDIA(0):   33 46 39 37 56 30 59 54  53 0a 00 00 00 fd 00 38
(--) NVIDIA(0):   55 1e 5c 11 00 0a 20 20  20 20 20 20 00 00 00 fc
(--) NVIDIA(0):   00 44 45 4c 4c 20 53 50  32 33 30 39 57 0a 00 bc
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for DELL SP2309W (DFP-0) ---
(--) NVIDIA(0):
(II) NVIDIA(0): Frequency information for DELL SP2309W (DFP-0):
(II) NVIDIA(0):   HorizSync   : 30.000-92.000 kHz
(II) NVIDIA(0):   VertRefresh : 56.000-85.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0):
(II) NVIDIA(0): --- Building ModePool for DELL SP2309W (DFP-0) ---
(II) NVIDIA(0):   Validating Mode "2048x1152":
(II) NVIDIA(0):     2048 x 1152 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 156.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2096
(II) NVIDIA(0):       HSyncEnd, HTotal : 2128, 2208
(II) NVIDIA(0):       VRes, VSyncStart : 1152, 1155
(II) NVIDIA(0):       VSyncEnd, VTotal : 1160, 1185
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: PixelClock (156.8 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 155.0 MHz).
(II) NVIDIA(0):
...

```
Finally I want to give credit to the freebsd people who put together this awesome document that helped me solve the problem

[http://ru.download.nvidia.com/freebsd/180.44/README/chapter-16.html](http://ru.download.nvidia.com/freebsd/180.44/README/chapter-16.html)

---

### Post by funmler on 2009-10-18
jeez spoke too soon... The initial login comes up at 2048x1152 but then resets to 1680x1050 when I login.:confused:

I think I am just going to go find a VGA cabal .:) 

Here is the log
```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux atlas 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 17 23:14:21 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "DELL SP2309W"
(**) |   |-->Device "Device0"
(**) Option "DontZap" "False"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@3:0:0) nVidia Corporation G70 [GeForce 7800 GS] rev 162, Mem @ 0xe0000000/16777216, 0xd0000000/268435456, 0xe1000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) NVIDIA X compatibility module for ABI 5.0 built from xorg-server-1.5.99.901
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "yes"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Option "ModeValidation" "NoMaxPClkCheck"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GS (G70) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(II) NVIDIA(0): GPU RAM Type: GDDR3
(--) NVIDIA(0): VideoBIOS: 05.70.02.33.07
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): VPES : 6
(II) NVIDIA(0): SPS  : 16
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 7800 GS
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GS at PCI:3:0:0:
(--) NVIDIA(0):     DELL SP2309W (DFP-0)
(--) NVIDIA(0): DELL SP2309W (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL SP2309W (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): DELL SP2309W (DFP-0): Native FlatPanel Scaling is supported
(--) NVIDIA(0): DELL SP2309W (DFP-0): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): DELL SP2309W (DFP-0): DFP is not internal to notebook
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for DELL SP2309W (DFP-0) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : DEL
(--) NVIDIA(0): Monitor Name                 : DELL SP2309W
(--) NVIDIA(0): Product ID                   : 53276
(--) NVIDIA(0): 32-bit Serial Number         : 811160659
(--) NVIDIA(0): Serial Number String         : U783F97V0YTS
(--) NVIDIA(0): Manufacture Date             : 2009, week 31
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 510mm x 290mm
(--) NVIDIA(0): Valid HSync Range            : 30.0 kHz - 92.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 56 Hz - 85 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 170.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1152 x 864  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 60 Hz
(--) NVIDIA(0):   1680 x 1050 @ 60 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   2048 x 1152 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 156.75 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2048, 2096
(--) NVIDIA(0):     HSyncEnd, HTotal : 2128, 2208
(--) NVIDIA(0):     VRes, VSyncStart : 1152, 1155
(--) NVIDIA(0):     VSyncEnd, VTotal : 1160, 1185
(--) NVIDIA(0):     H/V Polarity     : +/-
(--) NVIDIA(0): 
(--) NVIDIA(0): 
(--) NVIDIA(0): Raw EDID bytes:
(--) NVIDIA(0): 
(--) NVIDIA(0):   00 ff ff ff ff ff ff 00  10 ac 1c d0 53 54 59 30
(--) NVIDIA(0):   1f 13 01 03 80 33 1d 78  ea 18 55 a9 53 37 ad 25
(--) NVIDIA(0):   13 50 54 a5 4b 00 71 4f  81 80 b3 00 01 01 01 01
(--) NVIDIA(0):   01 01 01 01 01 01 3b 3d  00 a0 80 80 21 40 30 20
(--) NVIDIA(0):   35 00 fe 22 11 00 00 1a  00 00 00 ff 00 55 37 38
(--) NVIDIA(0):   33 46 39 37 56 30 59 54  53 0a 00 00 00 fd 00 38
(--) NVIDIA(0):   55 1e 5c 11 00 0a 20 20  20 20 20 20 00 00 00 fc
(--) NVIDIA(0):   00 44 45 4c 4c 20 53 50  32 33 30 39 57 0a 00 bc
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DELL SP2309W (DFP-0) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Mode Validation Overrides for DELL SP2309W (DFP-0):
(II) NVIDIA(0):     NoMaxPClkCheck
(II) NVIDIA(0): Frequency information for DELL SP2309W (DFP-0):
(II) NVIDIA(0):   HorizSync   : 30.000-92.000 kHz
(II) NVIDIA(0):   VertRefresh : 56.000-85.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for DELL SP2309W (DFP-0) ---
(II) NVIDIA(0):   Validating Mode "2048x1152":
(II) NVIDIA(0):     2048 x 1152 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 156.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2096
(II) NVIDIA(0):       HSyncEnd, HTotal : 2128, 2208
(II) NVIDIA(0):       VRes, VSyncStart : 1152, 1155
(II) NVIDIA(0):       VSyncEnd, VTotal : 1160, 1185
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for DELL SP2309W (DFP-0):
(II) NVIDIA(0):   2048 x 1152 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 156.750 MHz
(II) NVIDIA(0):     HRes, HSyncStart : 2048, 2096
(II) NVIDIA(0):     HSyncEnd, HTotal : 2128, 2208
(II) NVIDIA(0):     VRes, VSyncStart : 1152, 1155
(II) NVIDIA(0):     VSyncEnd, VTotal : 1160, 1185
(II) NVIDIA(0):     H/V Polarity     : +/-
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1152":
(II) NVIDIA(0):     2048 x 1152 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 156.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2096
(II) NVIDIA(0):       HSyncEnd, HTotal : 2128, 2208
(II) NVIDIA(0):       VRes, VSyncStart : 1152, 1155
(II) NVIDIA(0):       VSyncEnd, VTotal : 1160, 1185
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1152":
(II) NVIDIA(0):     2048 x 1152 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Configuration file ModeLine
(II) NVIDIA(0):       Pixel Clock      : 156.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2096
(II) NVIDIA(0):       HSyncEnd, HTotal : 2128, 2208
(II) NVIDIA(0):       VRes, VSyncStart : 1152, 1155
(II) NVIDIA(0):       VSyncEnd, VTotal : 1160, 1185
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "2048x1152": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "640x350": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x175": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "640x400": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x200": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "720x400": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "360x200": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (56.000-85.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (56.000-85.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1024x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 1152x864
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x512": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x512": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x512": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 2048 x 1152); mode will not be allowed to scale
(II) NVIDIA(0):         to the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DELL SP2309W (DFP-0);
(WW) NVIDIA(0):         cannot compute backend DFP timings (mode is larger
(WW) NVIDIA(0):         than native backend 2048 x 1152).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "896x672": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "928x696": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "960x720": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "832x624": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "416x312": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1152x864": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (100.0 Hz) out of range
(WW) NVIDIA(0):     (56.000-85.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (100.1 Hz) out of range
(WW) NVIDIA(0):     (56.000-85.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1360x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "680x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1360x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "680x384": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1400x1050": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1400x1050": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1400x1050": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (179.3 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1440x900": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "720x450": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1600x1024": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "800x512": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1680x1050": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1680x1050": 1680x1050
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (174.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (187.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (214.8 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1920x1080": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "960x540": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1920 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 2048 x 1152); mode will not be allowed to scale
(II) NVIDIA(0):         to the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1920x1200" for DELL SP2309W (DFP-0);
(WW) NVIDIA(0):         cannot compute backend DFP timings (mode is larger
(WW) NVIDIA(0):         than native backend 2048 x 1152).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "960x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (170.7 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (267.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (30.000-92.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (170.2 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (194.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "640x350": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "640x400": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "720x400": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (56.000-85.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1024x768": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 1152x864
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 2048x1152
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 2048 x 1152); mode will not be allowed to scale
(II) NVIDIA(0):         to the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DELL SP2309W (DFP-0);
(WW) NVIDIA(0):         cannot compute backend DFP timings (mode is larger
(WW) NVIDIA(0):         than native backend 2048 x 1152).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 170.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for DELL SP2309W (DFP-0) ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for DELL SP2309W (DFP-0) ---
(II) NVIDIA(0): "nvidia-auto-select" : 2048 x 1152 @  59.9 Hz  (from: X Configuration file ModeLine, EDID)
(II) NVIDIA(0): "2048x1152"          : 2048 x 1152 @  59.9 Hz  (from: X Configuration file ModeLine, EDID)
(II) NVIDIA(0): "2048x1152_60"       : 2048 x 1152 @  59.9 Hz  (from: X Configuration file ModeLine, EDID)
(II) NVIDIA(0): "1920x1080"          : 1920 x 1080 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1920x1080_60"       : 1920 x 1080 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  60.0 Hz  (from: X Server, EDID)
(II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server, EDID)
(II) NVIDIA(0): "1680x1050_60_0"     : 1680 x 1050 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  74.8 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_75"       : 1400 x 1050 @  74.8 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_70"       : 1400 x 1050 @  70.0 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
(II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x1024_85"       : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x1024_75"       : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_85"        : 1280 x  960 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1152x864"           : 1152 x  864 @  85.1 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_85"        : 1152 x  864 @  85.1 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_85_0"      : 1152 x  864 @  85.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_75"        : 1152 x  864 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1152x864_75_0"      : 1152 x  864 @  75.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_70"        : 1152 x  864 @  70.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_85"        : 1024 x  768 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "960x720"            :  960 x  720 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x720d60"         :  960 x  720 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "928x696"            :  928 x  696 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "928x696d60"         :  928 x  696 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "896x672"            :  896 x  672 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "896x672d60"         :  896 x  672 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525"            :  840 x  525 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d75"         :  840 x  525 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d70"         :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60_0"       :  840 x  525 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.6 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.6 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600d70"         :  800 x  600 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600_85"         :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x400"            :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x400_85"         :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512"            :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d85"         :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d75"         :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  85.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d85"         :  640 x  480 @  85.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_85"         :  640 x  480 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x400"            :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x400_85"         :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x350"            :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x350_85"         :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d85"         :  576 x  432 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d85_0"       :  576 x  432 @  85.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d85"         :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d85"         :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200"            :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200d85"         :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d85"         :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200"            :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200d85"         :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175"            :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175d85"         :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for DELL SP2309W (DFP-0): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "2048x1152"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "2048x1152":
(II) NVIDIA(0):     Bounding Box: [0, 0, 2048, 1152]
(II) NVIDIA(0):     DELL SP2309W (DFP-0): "2048x1152"
(II) NVIDIA(0):         Size          : 2048 x 1152
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 2048 x 1152
(II) NVIDIA(0):         Position      : [0, 0, 2048, 1152]
(II) NVIDIA(0): Virtual screen size determined to be 2048 x 1152
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "1920x1080"      : 1920 x 1080 @  59.9 Hz 
(II) NVIDIA(0): "1680x1050"      : 1680 x 1050 @  60.0 Hz 
(II) NVIDIA(0): "1680x1050_60_0" : 1680 x 1050 @  59.9 Hz 
(II) NVIDIA(0): "1600x1024"      : 1600 x 1024 @  60.2 Hz 
(II) NVIDIA(0): "1440x900"       : 1440 x  900 @  59.9 Hz 
(II) NVIDIA(0): "1400x1050"      : 1400 x 1050 @  74.8 Hz 
(II) NVIDIA(0): "1400x1050_70"   : 1400 x 1050 @  70.0 Hz 
(II) NVIDIA(0): "1400x1050_60"   : 1400 x 1050 @  60.0 Hz 
(II) NVIDIA(0): "1360x768"       : 1360 x  768 @  60.0 Hz 
(II) NVIDIA(0): "1360x768_60_0"  : 1360 x  768 @  59.8 Hz 
(II) NVIDIA(0): "1280x1024"      : 1280 x 1024 @  85.0 Hz 
(II) NVIDIA(0): "1280x1024_75"   : 1280 x 1024 @  75.0 Hz 
(II) NVIDIA(0): "1280x1024_60"   : 1280 x 1024 @  60.0 Hz 
(II) NVIDIA(0): "1280x960"       : 1280 x  960 @  85.0 Hz 
(II) NVIDIA(0): "1280x960_60"    : 1280 x  960 @  60.0 Hz 
(II) NVIDIA(0): "1152x864"       : 1152 x  864 @  85.1 Hz 
(II) NVIDIA(0): "1152x864_85_0"  : 1152 x  864 @  85.0 Hz 
(II) NVIDIA(0): "1152x864_75"    : 1152 x  864 @  75.0 Hz 
(II) NVIDIA(0): "1152x864_75_0"  : 1152 x  864 @  75.0 Hz 
(II) NVIDIA(0): "1152x864_70"    : 1152 x  864 @  70.0 Hz 
(II) NVIDIA(0): "1152x864_60"    : 1152 x  864 @  60.0 Hz 
(II) NVIDIA(0): "1024x768"       : 1024 x  768 @  85.0 Hz 
(II) NVIDIA(0): "1024x768_75"    : 1024 x  768 @  75.0 Hz 
(II) NVIDIA(0): "1024x768_70"    : 1024 x  768 @  70.1 Hz 
(II) NVIDIA(0): "1024x768_60"    : 1024 x  768 @  60.0 Hz 
(II) NVIDIA(0): "960x720"        :  960 x  720 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "960x600"        :  960 x  600 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "960x540"        :  960 x  540 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "928x696"        :  928 x  696 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "896x672"        :  896 x  672 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525"        :  840 x  525 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525d70"     :  840 x  525 @  69.9 Hz DoubleScan 
(II) NVIDIA(0): "840x525d60"     :  840 x  525 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525d60_0"   :  840 x  525 @  59.9 Hz DoubleScan 
(II) NVIDIA(0): "832x624"        :  832 x  624 @  74.6 Hz 
(II) NVIDIA(0): "800x600"        :  800 x  600 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "800x600d65"     :  800 x  600 @  65.0 Hz DoubleScan 
(II) NVIDIA(0): "800x600d60"     :  800 x  600 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "800x600_85"     :  800 x  600 @  85.1 Hz 
(II) NVIDIA(0): "800x600_75"     :  800 x  600 @  75.0 Hz 
(II) NVIDIA(0): "800x600_72"     :  800 x  600 @  72.2 Hz 
(II) NVIDIA(0): "800x600_60"     :  800 x  600 @  60.3 Hz 
(II) NVIDIA(0): "800x600_56"     :  800 x  600 @  56.2 Hz 
(II) NVIDIA(0): "800x512"        :  800 x  512 @  60.2 Hz DoubleScan 
(II) NVIDIA(0): "720x450"        :  720 x  450 @  59.9 Hz DoubleScan 
(II) NVIDIA(0): "720x400"        :  720 x  400 @  85.0 Hz 
(II) NVIDIA(0): "680x384"        :  680 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "680x384d60_0"   :  680 x  384 @  59.8 Hz DoubleScan 
(II) NVIDIA(0): "640x512"        :  640 x  512 @  85.0 Hz DoubleScan 
(II) NVIDIA(0): "640x512d75"     :  640 x  512 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "640x512d60"     :  640 x  512 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480"        :  640 x  480 @  85.1 Hz DoubleScan 
(II) NVIDIA(0): "640x480d60"     :  640 x  480 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480_85"     :  640 x  480 @  85.0 Hz 
(II) NVIDIA(0): "640x480_75"     :  640 x  480 @  75.0 Hz 
(II) NVIDIA(0): "640x480_73"     :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480_60"     :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "640x400"        :  640 x  400 @  85.1 Hz 
(II) NVIDIA(0): "640x350"        :  640 x  350 @  85.1 Hz 
(II) NVIDIA(0): "576x432"        :  576 x  432 @  85.2 Hz DoubleScan 
(II) NVIDIA(0): "576x432d85_0"   :  576 x  432 @  85.1 Hz DoubleScan 
(II) NVIDIA(0): "576x432d75"     :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d75_0"   :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d70"     :  576 x  432 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d60"     :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"        :  512 x  384 @  85.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d75"     :  512 x  384 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d70"     :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"     :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"        :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"        :  400 x  300 @  85.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d75"     :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"     :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"     :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"     :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "360x200"        :  360 x  200 @  85.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240"        :  320 x  240 @  85.2 Hz DoubleScan 
(II) NVIDIA(0): "320x240d75"     :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"     :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"     :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "320x200"        :  320 x  200 @  85.3 Hz DoubleScan 
(II) NVIDIA(0): "320x175"        :  320 x  175 @  85.3 Hz DoubleScan 
(II) NVIDIA(0): 
(II) NVIDIA(0): Computing DPI using physical size from DELL SP2309W (DFP-0)'s
(II) NVIDIA(0):     EDID and first mode to be programmed on DELL SP2309W
(II) NVIDIA(0):     (DFP-0):
(II) NVIDIA(0):   width  : 2048 pixels  510  mm (DPI: 101)
(II) NVIDIA(0):   height : 1152 pixels  290  mm (DPI: 100)
(--) NVIDIA(0): DPI set to (101, 100); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): GPU initialized
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "2048x1152"
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(II) NVIDIA(0): Composite wrapper disabled.
(**) NVIDIA(0): Option "BackingStore" "true"
(**) NVIDIA(0): Backing store enabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "XAANoOffscreenPixmaps" is not used
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
(II) NVIDIA(0): Setting mode "1680x1050"


```

---

### Post by funmler on 2009-10-18
Oops, turns out the last little bit had nothing to do with xorg.conf. 

The Configure Display had the size set to 1680x1050 so when I logged in it changed back. 

Guess I don't need that VGA cabal after all :P

---

### Post by lordbah on 2009-12-15
> **forestcomber said:**
> I'm running Ubuntu 9.04 on an Asus eee PC 901.  The resolution is perfect at 2048 x 1152.  The webcam works perfectly.  But I can't get the microphones to work !!

Anyone have any luck ?

Just hooked one up on 9.10 and the webcam is not working.

Cheese 2.28.1 
Probing devices with HAL...
Found device 05a9:2649, getting capabilities...
Detected v4l2 device: Monitor Webcam
Driver: uvcvideo, version: 256
Capabilities: 0x04000001

Probing supported video formats...
libv4l2: error turning on stream: Input/output error


Other programs have the same basic error. I found one bug which suggested removing and re-enabling uvcvideo via modprobe, but that didn't help.

UPDATE:
I downloaded latest stuff from [http://linuxtv.org/hg/~pinchartl/uvcvideo/rev/033b5968aa1a](http://linuxtv.org/hg/~pinchartl/uvcvideo/rev/033b5968aa1a) and rebuilt it. Compile error. Per [http://ubuntuforums.org/showthread.php?t=1337146&highlight=v4l-dvb](http://ubuntuforums.org/showthread.php?t=1337146&highlight=v4l-dvb) I ran "make config", answered no to the Firewire stuff and accepted defaults for everything else (and man is there a lot), now it builds, sudo make install okay, sudo make reload logged lots of errors about lots of modules either having unknown symbols or files not existing. lsmod showed uvcvideo not loaded. sudo modprobe uvcvideo loaded it, it did appear to be the new build. But cheese has the same error, and still says

Driver: uvcvideo, version: 256

I don't know where that version number is coming from. If it's from uvcvideo.ko I would have expected it to change.

---

### Post by katp on 2010-09-07
please help me, I'm completely new to this and have just set up a Dell mini10v on Linux (it's actually CentOS which I gather is not the same as Ubuntu, but I'm hoping someone here can help me anyway).  When I plug in my SP2309W Monitor I can't make it display at any resolution other then 600x800, which is ridiculous as you can imagine.  All I could think of to do was to go into Administration > Display > change the settings, but it just ignores whatever i put and displays it at minimal settings regardless!  Plus there is no option the correct settings or even any with the correct dimensions.

Please help, its driving me crazy! :)

---

