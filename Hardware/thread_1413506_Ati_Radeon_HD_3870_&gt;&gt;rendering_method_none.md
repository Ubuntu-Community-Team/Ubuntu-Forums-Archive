---
title: "Ati Radeon HD 3870 &gt;&gt;rendering method: none"
date: 2010-02-22
forum: Hardware
---

### Post by at_tension on 2010-02-22
Hello i am new in ubuntu,and im having problem getting my drivers (graphics ) work correctly.i have already tried like 5 times the ubuntu help about ati propertionary drivers also tried to unistall fglrx and got my self in a dos like enviroment so i had to reinstall it ok some more info:
this is my 
./compiz-check result 
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon HD 3870
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


```also this is my ```
 sudo gedit /etc/X11/xorg.cong 
``````

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Radeon HD 3870"
    Driver      "ati"
    BusID       "PCI:02:00:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Radeon HD 3870"
    DefaultDepth     24
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
```i get a YES in glxinfo | grep "direct rendering"

so if someone has any advise or needs any more info about my system PLZ reply and most likely i ll answer you pretty quick.One last thing ,in general i can use compiz effects like cube or the mouse and the animation but i cant run 3d run with no glitches or no crashing ex. Heroes of Newerth(this is a linux game also) .Also im not able to run 3d application like zbrush or 3dmax in Virtual Box(running windows xp sp.2)

---

### Post by Yellow Pasque on 2010-02-22
> i get a YES in glxinfo | grep "direct rendering"
..but do you get "ATI ..." for the "OpenGL renderer string" or do you get "Mesa Software Rasterizer" when using the "fglrxinfo" command? If the latter, your driver isn't installed correctly.

Also, maybe you need this in your xorg.conf:
```
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
        Option        "AIGLX"            "On"
EndSection

```

---

### Post by at_tension on 2010-02-22
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.9016

```

i ll try asap the sonr.conf you wrote and inform ou if it worked thnx :D

---

### Post by at_tension on 2010-02-22
> **at_tension said:**
> ```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.9016

```i ll try asap the sonr.conf you wrote and inform ou if it worked thnx :D

i copied / pasted the xorg.conf staff you gaved me and save and exit the gedit ,then restart but nothing new :S

---

### Post by Yellow Pasque on 2010-02-22
That's odd. You might want to try a fresh install of the driver: [http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)
If that doesn't help, can you post/pastebin your /var/log/Xorg.0.log ?

---

### Post by at_tension on 2010-02-22
i re-install folowing the link and nothing new still no rendering mode
tho my xorg.conf looks different now


```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "AIGLX" "On"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Radeon HD 3870"
    Driver      "ati"
    BusID       "PCI:02:00:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

```


 , do i simply paste 
/var/log/Xorg.0.log 
in my terminal ?? cause that's what im doing and i get a 
bash: /var/log/Xorg.0.log: Permission denied 
even after sudo su

---

### Post by Yellow Pasque on 2010-02-22
No, it's a text file.
```
gedit /var/log/Xorg.0.log
```

---

### Post by at_tension on 2010-02-22
excuse me for that im pretty new in linux 
there you go :

```
 X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux dentatous-desktop 2.6.31-19-generic-pae #56-Ubuntu SMP Thu Jan 28 02:29:51 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=0eeac791-de8b-4b2c-9a0a-11abbab2e313 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 23 00:08:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(**) Option "AIGLX" "On"
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
(**) Extension "Composite" is enabled
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
(++) using VT number 7

(--) PCI:*(0:2:0:0) 1002:9501:1043:024c ATI Technologies Inc Radeon HD 3870 rev 0, Mem @ 0xe0000000/268435456, 0xfdce0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 02@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:19
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9501) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x9e6c358
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [17] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [18] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [20] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [21] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [22] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Loading extension XFree86-DRI
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(--) fglrx(0): Chipset: "ATI Radeon HD 3870" (Chipset = 0x9501)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x024c)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfdce0000
(--) fglrx(0): I/O port at 0x0000dc00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.81
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV670
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 2:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
(II) fglrx(0): Interrupt handler installed at IRQ 30.
(II) fglrx(0): IRQ 30 Enabled.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000008, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 56dc  Serial#: 249309
(II) fglrx(0): Year: 2009  Week: 5
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 138.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
(II) fglrx(0): Monitor name: W2253
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff001e6ddc56ddcd0300
(II) fglrx(0):     0513010380301b78ea3d85a6564a9a24
(II) fglrx(0):     125054a76b80b30081808140714f0101
(II) fglrx(0):     0101010101011a3680a070381f403020
(II) fglrx(0):     3500dd0c1100001a023a801871382d40
(II) fglrx(0):     582c4500dd0c1100001e000000fd0038
(II) fglrx(0):     4b1e530f000a202020202020000000fc
(II) fglrx(0):     0057323235330a20202020202020005a
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output TV has no monitor section
(II) fglrx(0): Output COMPONENT_VIDEO has no monitor section
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using EDID range info for horizontal sync
(II) fglrx(0): Using EDID range info for vertical refresh
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Output DFP1 connected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Output TV disconnected
(II) fglrx(0): Output COMPONENT_VIDEO disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP1 using initial mode 1920x1080
(II) fglrx(0): Display dimensions: (480, 270) mm
(II) fglrx(0): DPI set to (101, 101)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [17] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [18] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [20] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [21] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [22] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb73a1000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.66.10
(II) fglrx(0):     Date: Sep  3 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.31-19-generic-pae
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0102c000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,2208)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 288
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid Horizontal and Vertical Lines
    Driver provided ScreenToScreenBitBlt replacement
    Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(--) RandR disabled
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
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 477 x 268
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) config/hal: Adding input device Logitech USB Gaming Mouse
(**) Logitech USB Gaming Mouse: always reports core events
(**) Logitech USB Gaming Mouse: Device: "/dev/input/event5"
(II) Logitech USB Gaming Mouse: Found 20 mouse buttons
(II) Logitech USB Gaming Mouse: Found x and y relative axes
(II) Logitech USB Gaming Mouse: Found scroll wheel(s)
(II) Logitech USB Gaming Mouse: Configuring as mouse
(**) Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE)
(**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Gaming Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Gaming Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Gaming Mouse: (accel) set acceleration profile 0
(II) Logitech USB Gaming Mouse: initialized for relative axes.
(II) config/hal: Adding input device WALTOP International Corp. Media Tablet
(**) WALTOP International Corp. Media Tablet: always reports core events
(**) WALTOP International Corp. Media Tablet: Device: "/dev/input/event6"
(II) WALTOP International Corp. Media Tablet: Found 9 mouse buttons
(II) WALTOP International Corp. Media Tablet: Found x and y relative axes
(II) WALTOP International Corp. Media Tablet: Found scroll wheel(s)
(II) WALTOP International Corp. Media Tablet: Found x and y absolute axes
(II) WALTOP International Corp. Media Tablet: Found absolute touchpad
(II) WALTOP International Corp. Media Tablet: Found keys
(II) WALTOP International Corp. Media Tablet: Configuring as touchpad
(II) WALTOP International Corp. Media Tablet: Configuring as keyboard
(**) WALTOP International Corp. Media Tablet: YAxisMapping: buttons 4 and 5
(**) WALTOP International Corp. Media Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "WALTOP International Corp. Media Tablet" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(WW) WALTOP International Corp. Media Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Media Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Media Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Media Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Media Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Media Tablet: initialized for absolute axes.
(II) fglrx(0): EDID vendor "GSM", prod id 22236
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
```

---

### Post by Yellow Pasque on 2010-02-22
I don't see any problem there. Report your bug on Launchpad.

---

