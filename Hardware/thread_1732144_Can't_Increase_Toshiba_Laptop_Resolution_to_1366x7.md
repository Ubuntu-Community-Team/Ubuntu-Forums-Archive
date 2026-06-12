---
title: "Can't Increase Toshiba Laptop Resolution to 1366x768"
date: 2011-04-17
forum: Hardware
---

### Post by Mr. Tux on 2011-04-17
I'm running 10.04 Ubuntu, and I can't increase the resolution of my Toshbia Satellite[SIZE=1] L650-ST3N01X[/SIZE] laptop from 1024x768 to 1366x768.  Here's a link to my[ laptop's specs]("http://www.toshibadirect.com/td/b2c/pdet.to?poid=505771"), I also posted the output of lshw for my system.  I tried following these [instructions]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html"), but it didn't work.  I know that the hardware is capable of the resolution, the specs say so.

```

jared@jared-laptop:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
jared@jared-laptop:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
jared@jared-laptop:~$ xrandr --addmode default 1368x768_60.00
jared@jared-laptop:~$ xrandr --output default --mode 1368x768_60.00
xrandr: screen cannot be larger than 1024x768 (desired size 1368x768)
```Help?

---

### Post by K_45 on 2011-04-17
Post the Xorg log:

```
gedit /var/log/Xorg.0.log
```

inbetween the code tags.

---

### Post by Mr. Tux on 2011-04-17
Here's my Xorg log:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux jared-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=a2dfcc67-2b1c-488c-a275-0b471db49278 ro quiet splash nomodeset acpi_backlight=vendor
Build Date: 10 December 2010  05:52:57PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 17 21:35:54 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0116:1179:fc50 Intel Corporation rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00003000/64
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32704 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
(II) VESA(0): Year: 2009  Week: 1
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
(II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
(II) VESA(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
(II) VESA(0): Unknown vendor-specific block f
(II) VESA(0):  AUO
(II) VESA(0):  B156XW02 V2
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff0006afec2200000000
(II) VESA(0):     01130103802213780ac8959e57549226
(II) VESA(0):     0f505400000001010101010101010101
(II) VESA(0):     010101010101121b5642500026302018
(II) VESA(0):     340058c1100000180000000f00000000
(II) VESA(0):     00000000000000000020000000fe0041
(II) VESA(0):     554f0a202020202020202020000000fe
(II) VESA(0):     004231353658573032205632200a00c0
(II) VESA(0): EDID vendor "AUO", prod id 8940
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 169 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16d (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16e (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16f (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 170 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 171 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 14d (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 15c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 14b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 15a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 107 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 11a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 11b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 9
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 9
    LinNumberOfImagePages: 9
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 25
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 25
    LinNumberOfImagePages: 25
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 62
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 62
    LinNumberOfImagePages: 62
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00083b5
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xb0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 511 64KB banks (32704kB)
(II) VESA(0): <default monitor>: Using hsync value of 48.39 kHz
(II) VESA(0): <default monitor>: Using vrefresh value of 60.04 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync value of 48.39 kHz
(II) VESA(0): <default monitor>: Using vrefresh value of 60.04 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-48.39 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 50.00-60.04 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): Display dimensions: (340, 190) mm
(**) VESA(0): DPI set to (76, 102)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32704 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f19edb74000,
    physical address = 0xb0000000, size = 33488896
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CNF9055 (/dev/input/event5)
(**) CNF9055: Applying InputClass "evdev keyboard catchall"
(**) CNF9055: always reports core events
(**) CNF9055: Device: "/dev/input/event5"
(II) CNF9055: Found keys
(II) CNF9055: Configuring as keyboard
(II) XINPUT: Adding extended input device "CNF9055" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by K_45 on 2011-04-17
Try

```
gksu jockey-gtk
```

Activate the driver and reboot. X is using the VESA driver.

---

### Post by Yellow Pasque on 2011-04-17
OP is using Sandybridge Intel graphics, so no proprietary driver will show in jockey. Instead, I would suggest running Ubuntu 11.04, as that's the first Ubuntu to support Sandybridge out of the box.

---

### Post by K_45 on 2011-04-17
> **Temüjin said:**
> OP is using Sandybridge Intel graphics, so no proprietary driver will show in jockey. Instead, I would suggest running Ubuntu 11.04, as that's the first Ubuntu to support Sandybridge out of the box.

I noticed the Sandy Bridge, but nothing in Jockey? Then 11.04 will have support with an updated kernel . . .

---

### Post by Mr. Tux on 2011-04-18
[K_45]("http://ubuntuforums.org/member.php?u=1277503"): Good idea, but jockey-gtk couldn't find any proprietary drivers for my integrated graphics card.
 

 [Temüjin]("http://ubuntuforums.org/member.php?u=327594"): I'll give 11.04 a shot, and I'll let you know what happens.
 

 Thank you both for the ideas.

---

### Post by Mr. Tux on 2011-04-18
The Ubuntu 11.04 beta let me access my full resolution.  Is there anyway to make 10.04 work with my graphics card?  I'd rather not install a beta release.  I'm afraid it will have glitches, or some software package like VMware Player won't play nicely with it.

---

### Post by Mr. Tux on 2011-04-22
I upgrade my system to 11.04 beta.  That fixed my resolution problem; however, VMplayer broken last night after I updated the packages on my system.  Hopefully, I'll be able to fix that somehow too.

Thanks everybody!    :P

---

