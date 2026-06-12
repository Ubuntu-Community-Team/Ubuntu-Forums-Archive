---
title: "Impossible to enable AGP"
date: 2008-11-07
forum: Hardware
---

### Post by russose on 2008-11-07
Hello,

I am having some problems with my AGP modules... I am running Ubuntu 8.10 and I have a NVIDIA 6200 AGP graphic card... I had some problems to ennable the NVIDIA drivers and I finally get it using the the following option in xorg.cof:
```
Option "NvAGP" "1"
```

In this way, I force linux to use the nvidia agp (nv_agp).

Until here, everything is ok but when I write in a terminal:
```
cat /proc/driver/nvidia/agp/status

it says me that AGP is disable:

Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.
```

And here my problems begin: I spent hours and hours in trying to make it run,  searching in forums, declaring nvidia and agp_nvidia in /etc/modules, blacklisting agpgart in /etc/modprobe.d/blacklist but it still doesn't work, my AGP is still disable and when running glxgears -info, it is around 700fps which seems low...

Does anyone have any idea to help me?

Thanks for your help,

Salvatore

---

### Post by russose on 2008-11-09
no idea at all ;) ?

---

### Post by dread on 2008-12-25
Yea I am also currently wrestling with this issue. Still no ideas on this issue?

---

### Post by mrowth on 2009-01-10
Me, too *bump*

I get ~11700 FPS in glxgears without Compiz, ~6300 with. 

No need to tell me glxgears is not a be-all-end-all benchmark ;) 

And it's enough for what I'm doing, usually. 

Still, browsing the forums here I see people "overtake" my current and previous Nvidia cards with slower/older video cards, slower CPUs, less RAM, and older mainboards. And I'm starting to wonder why. If Geforce 6 series folks get the same (glxgears) performance than my 7950 GT - seems wasteful.

```
**/proc/driver/nvidia/agp/status**
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

**/proc/driver/nvidia/agp/card**
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f000302
```

What's with the disabled "Fast Writes"? And is there even any point in trying to get rid of AGPGART?

GeForce 7950 GT (512MB), ASUS A8V Deluxe Mobo (AGP 8x), AMD X2 4800+ (2x 2.4GHz), 3GB RAM (DDR1), Kubuntu 8.04 (32 bit).

---

### Post by mrowth on 2009-01-11
$ sudo bump
[sudo] password: pretty please?

Have nvidia driver 173
Have kernel 2.6.24

---

### Post by mrowth on 2009-01-25
Doesn't anyone have any idea? It would be a start if I knew what's the matter, or how to find out more

---

### Post by martinbaselier on 2009-01-25
I have an ATI card, so I can't help you with nvidea, but I can tell you some troubleshooting tips. I think you should at leat post your log-file here, so people can see what the issues are: 

So post the output of the commands below, and cut the pieces of the log file that are not about the problem. 
```

glxinfo | grep render
cat /var/log/Xorg.0.log

```

---

### Post by mrowth on 2009-01-25
Hi, thanks for the suggestion.

```
[~]$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 7950 GT/AGP/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
```

Xorg.0.log -- I can't identify any problems in the log and don't want to cut anything that might I simply might not know is important. But I'll snip the bits about fonts, mouse and keyboard.

```
...
(**) Option "BlankTime" "10"
(**) Option "StandbyTime" "15"
(**) Option "SuspendTime" "16"
(**) Option "OffTime" "17"
(**) Option "NoPM" "false"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
...
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 2.0
        X.Org XInput driver : 2.0
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0282 card 1043,80a3 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0e:0: chip 109e,036e card 0070,13eb rev 02 class 04,00,00 hdr 80
(II) PCI: 00:0e:1: chip 109e,0878 card 0070,13eb rev 02 class 04,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,812a rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,02e4 card 0000,042a rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xf9f00000 - 0xfbffffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xf8ffffff (0x19000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:14:0) Brooktree Corporation Bt878 Video Capture rev 2, Mem @ 0xdfe00000/12
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x02e4) rev 162, Mem @ 0xfb000000/24, 0xe0000000/28, 0xfa000000/24, BIOS @ 0xf9f00000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [1] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [2] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [3] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [4] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [5] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [6] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [7] -1  0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [8] -1  0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [9] -1  0       0x00001000 - 0x000010ff (0x100) IX[B]
        [10] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [11] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [13] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [15] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [16] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [17] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [18] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [19] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [20] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [21] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [22] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [1] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [2] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [3] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [4] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [5] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [6] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [7] -1  0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [8] -1  0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [9] -1  0       0x00001000 - 0x000010ff (0x100) IX[B]
        [10] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [11] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [13] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [15] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [16] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [17] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [18] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [19] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [20] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [21] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [22] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [5] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [6] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [7] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [8] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [9] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [10] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [16] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [17] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [19] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [21] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [22] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [23] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [24] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [25] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [26] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [27] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [28] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 0.1.1
        ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.1.0
        ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.12  Thu Jul 17 18:36:35 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.4.0.90, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
...
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  173.14.12  Thu Jul 17 18:15:54 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [5] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [6] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [7] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [8] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [9] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [10] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [16] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [17] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [19] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [21] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [22] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [23] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [24] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [25] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [26] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [27] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [28] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [5] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [6] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [7] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [8] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [9] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [10] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [19] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [23] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [24] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [27] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [29] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [30] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [31] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [32] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [33] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "3"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1400x1050 +0+0, CRT-1: 1152x864 +1400+0; CRT-0: 1280x1024 +0+0, CRT-1: NULL; CRT-0: 1280x960 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1024x768 +0+0, CRT-1: NULL; CRT-0: 800x600 +0+0, CRT-1: NULL"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7950 GT (G71) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.56.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7950 GT at PCI:1:0:0:
(--) NVIDIA(0):     AOC Spectrum7K (CRT-0)
(--) NVIDIA(0):     TPV A1770NSL (CRT-1)
(--) NVIDIA(0): AOC Spectrum7K (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TPV A1770NSL (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1400x1050+0+0,CRT-1:1152x864+1400+0"
(II) NVIDIA(0):     "CRT-0:1280x1024+0+0,CRT-1:NULL"
(II) NVIDIA(0):     "CRT-0:1280x960+0+0,CRT-1:nvidia-auto-select+1280+0"
(II) NVIDIA(0):     "CRT-0:1024x768+0+0,CRT-1:NULL"
(II) NVIDIA(0):     "CRT-0:800x600+0+0,CRT-1:NULL"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1050
(--) NVIDIA(0): DPI set to (111, 111); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf9e00000 - 0xf9e000ff (0x100) MX[B]
        [5] -1  0       0xdff00000 - 0xdff00fff (0x1000) MX[B]
        [6] -1  0       0xf9c00000 - 0xf9c03fff (0x4000) MX[B]
        [7] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [8] -1  0       0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
        [9] -1  0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [10] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xdfe00000 - 0xdfe00fff (0x1000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [19] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [23] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [24] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [27] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
        [29] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
        [30] -1 0       0x0000d000 - 0x0000d007 (0x8) IX[B]
        [31] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [32] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [33] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "CRT-0:1400x1050+0+0,CRT-1:1152x864+1400+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
...
```

(If it matters, I have "noapic" in my menu.lst kernel parameters. I found I could no longer use optical drives (reliably) without that option (from Feisty or Gutsy on?). And ever since I first used "noapic", the NVIDIA driver will no longer runs without it. It'll complain about an edge-detected interrupt ..or something like that. Although it used to run without "noapic" for at least six years. Another mystery to me.)

---

### Post by nick09 on 2009-01-25
Go into the BIOS and set either the integrated video disabled or enable AGP.

---

### Post by mrowth on 2009-01-25
> **nick09 said:**
> Go into the BIOS and set either the integrated video disabled or enable AGP.
I don't know about the OP, but AGP isn't disabled in the BIOS in my case (and there's no integrated video). AGP Fast Writes aren't disabled in the BIOS either.

To repeat:
/proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

Thing is - I'd like to 
1) enable Fast Writes, if that's a good idea at all - don't know how
2) try NvAGP instead of AGP GART - but it will either leave me with no AGP, or fall back to AGPGART depending on the xorg.conf options
3) more generally, get the kind of performance I would've thought I could get - see my first post

---

### Post by mrowth on 2009-02-06
[quote="me"]I get ~11700 FPS in glxgears without Compiz, ~6300 with. 

No need to tell me glxgears is not a be-all-end-all benchmark ;) 

And it's enough for what I'm doing, usually. 

Still, browsing the forums here I see people "overtake" my current and previous Nvidia cards with slower/older video cards, slower CPUs, less RAM, and older mainboards. And I'm starting to wonder why. If Geforce 6 series folks get the same (glxgears) performance than my 7950 GT - seems wasteful.

```
**/proc/driver/nvidia/agp/status**
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

**/proc/driver/nvidia/agp/card**
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f000302
```

What's with the disabled "Fast Writes"? And is there even any point in trying to get rid of AGPGART?

GeForce 7950 GT (512MB), ASUS A8V Deluxe Mobo (AGP 8x), AMD X2 4800+ (2x 2.4GHz), 3GB RAM (DDR1), Kubuntu 8.04 (32 bit).[/quote]

I also have horrible tearing in vertical lines both on the desktop (window borders, etc.) and in movies. 

I've tried all the sync-to-vblank options in nvidia-settings, to no avail (though OpenGL vblank syncing reduces glxgears FPS to the screen's refresh rate). I'm loading the settings with nvidia-settings --load-config-only in .kde/Autostart. I've also actived vblank sync in Compiz Config Settings Manager. Changes nothing...?

When I use two separate X screens instead of Twinview (85 Hz CRT + 75 Hz CRT), the tearing in movies stops. But the desktop stays choppy. Compiz or regular kwin makes no difference.

---

### Post by mrowth on 2009-02-07
It's better in whatever KDE 4.1 release is available for Hardy from [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/). Although I can't get separate X screens to work in KDE 4. All I get on the right screen is a "busy" mouse cursor over a black background with no panel, no menus, and nothing to "do". (Known bug, it seems.) Twinview works, but since it syncs to one screen only the other's still choppy. Or is there a way to smooth that out?

Holding out for KDE 4.2, then. Or 4.3.

---

