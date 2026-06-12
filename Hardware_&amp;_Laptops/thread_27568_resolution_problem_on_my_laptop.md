---
title: "resolution problem on my laptop"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by dwevita on 2005-04-16
Hi Ihave problem wtih my screen resolution, i just install Ubantu in my laptop and it set to defult 640X800. did any one know how to confuget this to 1024X740.
 
Thanks in advance
D.

---

### Post by mendicant on 2005-04-16
Have you checked the following? 

[http://ubuntuforums.org/showthread.php?t=26284](http://ubuntuforums.org/showthread.php?t=26284)

---

### Post by dwevita on 2005-04-16
I checked that site and did come changers but still system pinking up my default configuration "640X800"

---

### Post by mendicant on 2005-04-16
Okay, can you post your /etc/X11/xorg.conf and /var/log/Xorg.0.log?  As an attachment instead of inline, preferably.

---

### Post by dwevita on 2005-04-16
Here is my xorg file

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Silicon Motion, Inc. SM712 LynxEM+"
        Driver          "siliconmotion"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Motion, Inc. SM712 LynxEM+"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection

EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by dwevita on 2005-04-16
here is my /var/log/Xorg.0.log file


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux dwevita 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686


(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 6.8.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "siliconmotion"
(II) Loading /usr/X11R6/lib/modules/drivers/siliconmotion_drv.o
(II) Module siliconmotion: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.3.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
        compiled for 4.2.0, module version = 1.0.0
        Module class: XFree86 XInput Driver
        ABI class: XFree86 XInput driver, version 0.3
(II) Silicon Motion: driver (version 1.3.1) for Silicon Motion Lynx chipsets:        Lynx, LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR
(II) Primary Device is: PCI 00:02:0
(--) Chipset LynxEM+ found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x07ffffff (0x7f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x08000000 - 0x08ffffff (0x1000000) MX[B](B)
        [6] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [7] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [8] -1  0       0x00008000 - 0x0000801f (0x20) IX[B]
        [9] -1  0       0x00008040 - 0x0000804f (0x10) IX[B]
        [10] -1 0       0x00007c00 - 0x00007c7f (0x80) IX[B]
        [11] -1 0       0x00007800 - 0x000078ff (0x100) IX[B]
        [12] -1 0       0x00007400 - 0x0000743f (0x40) IX[B]
        [13] -1 0       0x00007000 - 0x000070ff (0x100) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x07ffffff (0x7f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x08000000 - 0x08ffffff (0x1000000) MX[B](B)
        [6] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [7] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [8] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [9] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [10] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [11] -1 0       0x00008000 - 0x0000801f (0x20) IX[B]
        [12] -1 0       0x00008040 - 0x0000804f (0x10) IX[B]
        [13] -1 0       0x00007c00 - 0x00007c7f (0x80) IX[B]
        [14] -1 0       0x00007800 - 0x000078ff (0x100) IX[B]
        [15] -1 0       0x00007400 - 0x0000743f (0x40) IX[B]
        [16] -1 0       0x00007000 - 0x000070ff (0x100) IX[B]
        [17] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [18] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(**) Silicon MotionDepth 24, (--) framebuffer bpp 24
(==) Silicon MotionRGB weight 888
(==) Silicon MotionDefault visual is TrueColor
(==) Silicon MotionUsing Hardware Cursor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Silicon MotionPrimary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Silicon MotionVESA BIOS detected
(II) Silicon MotionVESA VBE Version 2.0
(II) Silicon MotionVESA VBE Total Mem: 1664 kB
(II) Silicon MotionVESA VBE OEM: Silicon Motion SM712 VGA BIOS
(II) Silicon MotionVESA VBE OEM Software Rev: 2.0
(II) Silicon MotionVESA VBE OEM Vendor: SM712
(II) Silicon MotionVESA VBE OEM Product: SM712
(II) Silicon MotionVESA VBE OEM Product Rev: SM712
(--) Silicon MotionChipset: "LynxEM+"
(II) Silicon MotionCursor Offset: FFFFFC00 Reserved: 001AF800
(II) Silicon MotionDSTN Panel Size = 800x600
(II) Silicon MotionvgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Silicon MotionI2C bus "I2C bus" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Silicon MotionVESA VBE DDC supported
(II) Silicon MotionVESA VBE DDC Level none
(II) Silicon MotionVESA VBE DDC transfer in appr. 0 sec.
(II) Silicon MotionVESA VBE DDC read successfully
(==) Silicon MotionUsing gamma correction (1.0, 1.0, 1.0)
(--) Silicon Motionvideoram: 2048kB
(--) Silicon MotionDetected current MCLK value of 128.864 MHz
(II) Silicon MotionGeneric Monitor: Using default hsync range of 28.00-33.00 kHz
(II) Silicon MotionGeneric Monitor: Using default vrefresh range of 43.00-72.00 Hz
(II) Silicon MotionClock range:  20.00 to 135.00 MHz
(II) Silicon MotionMode: 640x350 24-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x350" (hsync out of range)
(II) Silicon MotionNot using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x400 24-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x400" (hsync out of range)
(II) Silicon MotionNot using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 720x400 24-bpp, 85.038902Hz
(II) Silicon MotionNot using default mode "720x400" (hsync out of range)
(II) Silicon MotionNot using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 60.000000Hz
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 72.808800Hz
(II) Silicon MotionNot using default mode "640x480" (hsync out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "640x480" (hsync out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 85.008308Hz
(II) Silicon MotionNot using default mode "640x480" (hsync out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 56.250000Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 60.316540Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 72.187569Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 85.136887Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x864" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x960" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x960" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 832x624 24-bpp, 74.551270Hz
(II) Silicon MotionNot using default mode "832x624" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x800" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x864" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1440x900" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1680x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using mode "1024x768" (no mode of this name)
(II) Silicon MotionNot using mode "800x600" (no mode of this name)
(II) Silicon MotionMode: 640x480 24-bpp, 60.000000Hz
(--) Silicon MotionVirtual size is 640x480 (pitch 640)
(**) Silicon Motion Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) Silicon MotionModeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) Silicon MotionDPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 24 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0x08000000 - 0x08ffffff (0x1000000) MX[B]
        [1] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [2] -1  0       0x00100000 - 0x07ffffff (0x7f00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0x08000000 - 0x08ffffff (0x1000000) MX[B](B)
        [7] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [8] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [9] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x00008000 - 0x0000801f (0x20) IX[B]
        [13] -1 0       0x00008040 - 0x0000804f (0x10) IX[B]
        [14] -1 0       0x00007c00 - 0x00007c7f (0x80) IX[B]
        [15] -1 0       0x00007800 - 0x000078ff (0x100) IX[B]
        [16] -1 0       0x00007400 - 0x0000743f (0x40) IX[B]
        [17] -1 0       0x00007000 - 0x000070ff (0x100) IX[B]
        [18] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [19] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(==) Silicon MotionWrite-combining range (0x8000000,0x200000)
(II) Silicon MotionCursor Offset: 001FFC00 Reserved: 001AF800
(II) Silicon MotionDSTN Panel Size = 800x600
(II) Silicon MotionvgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Silicon MotionPrimary V_BIOS segment is: 0xc000
(II) Silicon MotionCurrent mode 0x03.
(II) Silicon MotionSetting mode 0x53
(II) Silicon MotionFrameBuffer Box: 0,0 - 640,920
(II) Silicon MotionUsing XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        8x8 color pattern filled rectangles
        CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                15 128x128 slots
                32 8x8 color pattern slots
(**) Option "dpms"
(**) Silicon MotionDPMS enabled
(II) Silicon MotionI2C device "I2C bus:SAA 7111A" registered at address 0x48.(II) Silicon MotionI2C device "I2C bus:SAA 7111A" removed.
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8

---

### Post by mendicant on 2005-04-16
It looks like you should be able to do at least 800x600, but your monitor isn't telling X the correct timings to use.  You can try installing read-edid:
% aptitude install read-edid
Then go to a console using alt-ctrl-f1 and turn off X:
% /etc/init.d/gdm stop ## assumes you are using Ubuntu, not Kubuntu
Then check the output of edid:
% get-edid | parse-edid

Then let us know what the output of that is.
Other things that will help:
What laptop is this (make & model)?  Do you know the min/max horizontal frequencies of your laptop panel display?  The manual may have it.

---

### Post by mendicant on 2005-04-16
Some googling reveals you may have an old thinkpad.  If it's a 240x, you can try (from [http://cs.baylor.edu/~rgm/thinkpad/thinkpad240x.html):](http://cs.baylor.edu/~rgm/thinkpad/thinkpad240x.html):)

Section "Monitor"
	Identifier   "LCD Panel"
	VendorName   "IBM"
	ModelName    "Thinkpad 240x"

	HorizSync    31.5-57
	VertRefresh  50-90
EndSection

You may also be able to find info on IBM's website.

---

### Post by dwevita on 2005-04-17
Yes I have old IBM laptop i Seriers

---

### Post by dwevita on 2005-04-17
here is my laptop product specification

Celeron 500MHz (128KB), 32MB RAM, 6.0GB HDD, 12.1 SVGA(800x600) HPA LCD, 24x-10x CD-ROM, Modem, NiMH battery,


Powerful Intel Mobile Celeron processor at 550 MHz(1) or 500 MHz with 128 KB L2 cache, depending on model 
64 or 32 MB SDRAM, expandable with optional 32, 64, and 128 MB(2) memory up to 160 MB or 192 MB maximum 
6.0 GB(3) hard-disk drive (HDD) 
12.0 GB hard-disk drive (HDD) also available in Japan (AP)

Integrated 56 K V.90(4) modem 
Optional Ethernet support 
Integrated Ethernet support for Japan (AP)

High-speed 24x-10x(6) CD-ROM 

Your choice of display, depending on model:

338-mm (13.3-in) XGA TFT active matrix 
330-mm (13.0-in) SVGA enhanced high-performance addressing (HPA) 
308-mm (12.1-in) SVGA TFT active matrix 
308-mm (12.1-in) SVGA HPA active matrix

---

### Post by laka on 2005-04-17
What happens if you try to remove "800x600" from xorg.conf?

---

### Post by mendicant on 2005-04-17
Okay, based on your information, I suspect you have an IBM i1200.  In this case, your monitor section should have:

Modeline "800x600" 40.35 800 816 928 1040 600 600 606 626

This info from:
[http://www.bioinf.uni-hannover.de/~mhothorn/i1200pic/](http://www.bioinf.uni-hannover.de/~mhothorn/i1200pic/)
[http://perso.wanadoo.fr/lionel_delattre/gentoo.html](http://perso.wanadoo.fr/lionel_delattre/gentoo.html)
via [http://www.linux-laptop.net](http://www.linux-laptop.net)

So your xorg.conf should have:
Section "Monitor"	
  Identifier	"Generic Monitor"
  VendorName	"IBM"
  ModelName	"SVGA 800X600@60HZ"
  HorizSync	31.5-40
  VertRefresh	58-62
  Modeline "640x480" 25.79 640 656 720 832 480 480 484 501
Modeline "800x600" 40.35 800 816 928 1040 600 600 606 626
EndSection

The 1024x768 mode is available with 16 bit color and is a virtual mode (you'll have to pan around).

---

### Post by dwevita on 2005-04-17
now is working properly. I make changers according to your information

thanks every one.

Now I need to configuer my wierless network card - I have Dlink - g650. 

did any one have any Idea.. how to configure...

Thanks again for your help.........

---

### Post by mendicant on 2005-04-17
[QUOTE=dwevita]
Now I need to configuer my wierless network card - I have Dlink - g650. 

did any one have any Idea.. how to configure...
[/QUOTE]

A quick google on that reveals that you might have luck installing the correct version of linux-restricted-modules-<xxx> for your kernel (<xxx> == 386 if you have linux-image-386 installed, for instance and 686 for linux-image-686).

---

### Post by dwevita on 2005-04-18
How do i find that my correct linux module

---

### Post by mendicant on 2005-04-18
% uname -a
Linux ubuntu 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

This tells me that I have linux-image-686 installed, and would need to install:
% sudo aptitude install linux-restricted-modules-686

Note that if you had installed linux-686, you would have automatically gotten linux-restricted-modules-686.  Then, you just need to make sure you load ath_pci, for instance:

% sudo gedit /etc/modules ## and append ath_pci

To initially test if it works, use:

% sudo modprobe ath_pci

---

### Post by dwevita on 2005-04-20
When I run uname -a it's shows

Linux 2.6.10-5-383

This mean ai dont have Linux 686 . Do I need to down load that . Please tell what my next step.

Thanks

---

### Post by dwevita on 2005-04-20
I isntall linux-restricted-modules-686 and run linux-restricted-modules-686
then i tested with sudo modprobe ath_pci

When i ran sudo modprobe ath_pci command it dint say any thing and came back to new command line ( it is normal)

what should I do in next step.

---

### Post by mendicant on 2005-04-20
[QUOTE=dwevita]When I run uname -a it's shows

Linux 2.6.10-5-383

This mean ai dont have Linux 686 . Do I need to down load that . Please tell what my next step.[/QUOTE]

Right--so you need the 386 version of the packages, not the 686 ones.  Just replace 686 with 386 in the commands I gave.

---

### Post by dwevita on 2005-04-21
actually I install 686 kernel and the modual as you mention befor. Good new is my wierless connection start to woke now. I am relly thanks full for you help.
D.

---

