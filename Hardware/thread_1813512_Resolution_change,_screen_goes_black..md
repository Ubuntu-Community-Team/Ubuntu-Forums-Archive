---
title: "Resolution change, screen goes black."
date: 2011-07-27
forum: Hardware
---

### Post by Metaxa on 2011-07-27
Hello. I have been using Ubuntu since version 8.04. I still consider myself a light user with basic knowledge.

I rescue old laptops, upgrade their hardware install Ubuntu and donate them to people in need. My current project is an HP ZD8215. I started with a fresh install of 11.04, after the install Unity came up with sluggish performance and the wrong resolution. Assuming it might be a driver issue I check the additional driver section and none were listed. I then checked Ubuntu software center and an ATI package was available. Installed and rebooted the machine. Once it came back up, it stated that their was no hardware acceleration and dropped me into classic.

I installed Unity 2d.

The problems:

1) The screen resolution is set to 1440x1023, 1440x900 is listed and the desired setting but when I choose it the screen goes blank until it reverts back on its own.
 
2) The machine will not turn off when powered down, making me have to hold the power button until it turns off.

3) I have spent many weeks reading about problems with ATI, propriety drivers open drivers and the like. Many threads touch on this issue but I am not sure if they completely apply. I would like to have some basic hardware acceleration so the person who gets this machine can play something as simple as SuperTuxCart.

Here are the outputs I think I need to provide:

> hugo@Pavillion:~$ sudo lshw -C display; lsb_release -a
[sudo] password for hugo: 
  *-display               
       description: VGA compatible controller
       product: M24 1P [Radeon Mobility X600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:d0000000-d7ffffff ioport:4000(size=256) memory:c8100000-c810ffff memory:c8120000-c813ffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

> Xandr 

hugo@Pavillion:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 1023, maximum 1440 x 1440
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x1023+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1440x1023      59.8*+
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

hugo@Pavillion:~$ 

> [dri] Disabling DRI.
[    46.475] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    46.475] (II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
[    46.475] (--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
[    46.475] (II) RADEON(0): Color tiling enabled by default
[    46.475] (II) Loading sub module "ddc"
[    46.475] (II) LoadModule: "ddc"
[    46.475] (II) Module "ddc" already built-in
[    46.475] (II) Loading sub module "i2c"
[    46.475] (II) LoadModule: "i2c"
[    46.475] (II) Module "i2c" already built-in
[    46.475] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 23000, sclk: 400.000000, mclk: 230.000000
[    46.475] (II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=40000; xclk=23000
[    46.475] (II) RADEON(0): Panel ID string: LPL                     
[    46.475] (II) RADEON(0): Panel Size from BIOS: 1440x1023
[    46.475] (II) RADEON(0): BIOS provided dividers will be used.
[    46.475] (WW) RADEON(0): LVDS Info:
XRes: 1440, YRes: 1023, DotClock: 0
HBlank: 0, HOverPlus: 0, HSyncWidth: 0
VBlank: 0, VOverPlus: 0, VSyncWidth: 0
[    46.475] (II) RADEON(0): Output VGA-0 has no monitor section
[    46.476] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    46.476] (II) RADEON(0): Output LVDS has no monitor section
[    46.476] (II) RADEON(0): Output S-video has no monitor section
[    46.476] (II) RADEON(0): Default TV standard: NTSC
[    46.476] (II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M NTSC-J 
[    46.476] (II) RADEON(0): Port0:
[    46.476]   XRANDR name: VGA-0
[    46.476]   Connector: VGA
[    46.476]   CRT1: INTERNAL_DAC1
[    46.476]   DDC reg: 0x60
[    46.476] (II) RADEON(0): Port1:
[    46.476]   XRANDR name: LVDS
[    46.476]   Connector: LVDS
[    46.476]   LCD1: INTERNAL_LVDS
[    46.476]   DDC reg: 0x0
[    46.476] (II) RADEON(0): Port2:
[    46.476]   XRANDR name: S-video
[    46.476]   Connector: S-video
[    46.476]   TV1: INTERNAL_DAC2
[    46.476]   DDC reg: 0x0
[    46.477] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    46.487] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    46.487] finished output detect: 0
[    46.487] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.487] finished output detect: 1
[    46.487] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    46.487] finished output detect: 2
[    46.487] finished all detect
[    46.493] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    46.493] (II) RADEON(0): EDID for output VGA-0
[    46.493] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.494] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[    46.494] (II) RADEON(0): Printing probed modes for output LVDS
[    46.494] (II) RADEON(0): Modeline "1440x1023"x59.8  100.75  1440 1488 1520 1600  1023 1026 1036 1053 +hsync -vsync (63.0 kHz)
[    46.494] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    46.494] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[    46.494] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    46.494] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    46.494] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    46.494] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    46.494] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    46.494] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    46.494] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    46.494] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    46.494] (II) RADEON(0): EDID for output S-video
[    46.494] (II) RADEON(0): Output VGA-0 disconnected
[    46.494] (II) RADEON(0): Output LVDS connected
[    46.494] (II) RADEON(0): Output S-video disconnected
[    46.494] (II) RADEON(0): Using exact sizes for initial modes
[    46.494] (II) RADEON(0): Output LVDS using initial mode 1440x1023
[    46.495] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    46.495] (==) RADEON(0): DPI set to (96, 96)
[    46.495] (II) Loading sub module "fb"
[    46.495] (II) LoadModule: "fb"
[    46.496] (II) Loading /usr/lib/xorg/modules/libfb.so
[    46.518] (II) Module fb: vendor="X.Org Foundation"
[    46.518] 	compiled for 1.10.1, module version = 1.0.0
[    46.518] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    46.518] (II) Loading sub module "ramdac"
[    46.518] (II) LoadModule: "ramdac"
[    46.518] (II) Module "ramdac" already built-in
[    46.518] (==) RADEON(0): Using XAA acceleration architecture
[    46.518] (II) Loading sub module "xaa"
[    46.518] (II) LoadModule: "xaa"
[    46.519] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    46.546] (II) Module xaa: vendor="X.Org Foundation"
[    46.546] 	compiled for 1.10.1, module version = 1.2.1
[    46.546] 	ABI class: X.Org Video Driver, version 10.0
[    46.546] (==) RADEON(0): Assuming overlay scaler buffer width is 1920
[    46.546] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    46.546] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    46.546] (II) UnloadModule: "fglrx"
[    46.546] (II) Unloading fglrx
[    46.546] (II) UnloadModule: "fglrxdrm"
[    46.546] (II) Unloading fglrxdrm
[    46.547] (II) UnloadModule: "vesa"
[    46.547] (II) Unloading vesa
[    46.547] (II) UnloadModule: "fbdev"
[    46.547] (II) Unloading fbdev
[    46.547] (II) UnloadModule: "fbdevhw"
[    46.547] (II) Unloading fbdevhw
[    46.547] (--) Depth 24 pixmap format is 32 bpp
[    46.547] (II) RADEON(0): RADEONScreenInit d0000000 0 0
[    46.578] Entering TV Save
[    46.578] Save TV timing tables
[    46.578] saveTimingTables: reading timing tables
[    46.578] TV Save done
[    47.601] (II) RADEON(0): Dynamic Power Management Disabled
[    47.601] (II) RADEON(0): RADEONInitMemoryMap() : 
[    47.601] (II) RADEON(0):   mem_size         : 0x08000000
[    47.601] (II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
[    47.601] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    47.601] (II) RADEON(0): Depth moves disabled by default
[    47.601] (II) RADEON(0): Memory manager initialized to (0,0) (1472,8191)
[    47.601] (II) RADEON(0): Reserved area from (0,1440) to (1472,1442)
[    47.601] (II) RADEON(0): Largest offscreen area available: 1472 x 6749
[    47.634] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    47.634] (II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
[    47.634] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    47.834] (==) RADEON(0): Backing store disabled
[    47.834] (WW) RADEON(0): Direct rendering disabled
[    47.834] (II) RADEON(0): Render acceleration disabled
[    47.834] (II) RADEON(0): num quad-pipes is 1
[    47.834] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    47.834] 	Screen to screen bit blits
[    47.834] 	Solid filled rectangles
[    47.834] 	8x8 mono pattern filled rectangles
[    47.834] 	Indirect CPU to Screen color expansion
[    47.834] 	Solid Lines
[    47.834] 	Scanline Image Writes
[    47.835] 	Setting up tile and stipple cache:
[    47.835] 		32 128x128 slots
[    47.835] 		32 256x256 slots
[    47.835] 		16 512x512 slots
[    47.835] (II) RADEON(0): Acceleration enabled
[    47.835] (==) RADEON(0): DPMS enabled
[    47.835] (==) RADEON(0): Silken mouse enabled
[    47.836] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00818e00
[    47.836] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x0081d300
[    47.836] (II) RADEON(0): Largest offscreen area available: 1472 x 6743
[    47.836] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    47.836] (II) Loading sub module "theatre_detect"
[    47.836] (II) LoadModule: "theatre_detect"
[    47.837] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    47.852] (II) Module theatre_detect: vendor="X.Org Foundation"
[    47.852] 	compiled for 1.10.1, module version = 1.0.0
[    47.852] 	ABI class: X.Org Video Driver, version 10.0
[    47.852] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    47.852] (II) RADEON(0): Set up overlay video
[    47.853] (II) RADEON(0): Set up textured video
[    47.860] disable primary dac
[    48.860] disable TV
[    49.860] init memmap
[    49.860] init common
[    49.860] init crtc1
[    49.860] init pll1
[    49.860] restore memmap
[    49.860] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    49.860] (II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
[    49.860] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    49.960] restore common
[    49.960] restore crtc1
[    49.961] restore pll1
[    49.961] set RMX
[    49.961] set LVDS
[    49.961] enable LVDS
[    50.961] disable primary dac
[    50.961] disable TV
[    50.961] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    50.961] (--) RandR disabled
[    50.961] (II) Initializing built-in extension Generic Event Extension
[    50.961] (II) Initializing built-in extension SHAPE
[    50.961] (II) Initializing built-in extension MIT-SHM
[    50.961] (II) Initializing built-in extension XInputExtension
[    50.961] (II) Initializing built-in extension XTEST
[    50.961] (II) Initializing built-in extension BIG-REQUESTS
[    50.961] (II) Initializing built-in extension SYNC
[    50.961] (II) Initializing built-in extension XKEYBOARD
[    50.961] (II) Initializing built-in extension XC-MISC
[    50.961] (II) Initializing built-in extension SECURITY
[    50.961] (II) Initializing built-in extension XINERAMA
[    50.961] (II) Initializing built-in extension XFIXES
[    50.961] (II) Initializing built-in extension RENDER
[    50.961] (II) Initializing built-in extension RANDR
[    50.961] (II) Initializing built-in extension COMPOSITE
[    50.961] (II) Initializing built-in extension DAMAGE
[    50.961] (II) Initializing built-in extension GESTURE
[    50.967] (EE) GLX error: Can not get required symbols.
[    50.979] (II) RADEON(0): Setting screen physical size to 380 x 270
[    51.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    51.174] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    51.174] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    51.174] (II) LoadModule: "evdev"
[    51.175] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.234] (II) Module evdev: vendor="X.Org Foundation"
[    51.234] 	compiled for 1.10.0.902, module version = 2.6.0
[    51.235] 	Module class: X.Org XInput Driver
[    51.235] 	ABI class: X.Org XInput driver, version 12.3
[    51.235] (II) Using input driver 'evdev' for 'Power Button'
[    51.235] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.235] (**) Power Button: always reports core events
[    51.235] (**) Power Button: Device: "/dev/input/event3"
[    51.235] (--) Power Button: Found keys
[    51.235] (II) Power Button: Configuring as keyboard
[    51.235] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    51.235] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    51.235] (**) Option "xkb_rules" "evdev"
[    51.235] (**) Option "xkb_model" "pc105"
[    51.235] (**) Option "xkb_layout" "us"
[    51.237] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    51.237] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    51.237] (II) Using input driver 'evdev' for 'Video Bus'
[    51.237] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.237] (**) Video Bus: always reports core events
[    51.237] (**) Video Bus: Device: "/dev/input/event9"
[    51.241] (--) Video Bus: Found keys
[    51.241] (II) Video Bus: Configuring as keyboard
[    51.241] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input9/event9"
[    51.241] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    51.241] (**) Option "xkb_rules" "evdev"
[    51.241] (**) Option "xkb_model" "pc105"
[    51.241] (**) Option "xkb_layout" "us"
[    51.245] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    51.245] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    51.245] (II) Using input driver 'evdev' for 'Power Button'
[    51.245] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.245] (**) Power Button: always reports core events
[    51.245] (**) Power Button: Device: "/dev/input/event1"
[    51.245] (--) Power Button: Found keys
[    51.245] (II) Power Button: Configuring as keyboard
[    51.245] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    51.245] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    51.245] (**) Option "xkb_rules" "evdev"
[    51.246] (**) Option "xkb_model" "pc105"
[    51.246] (**) Option "xkb_layout" "us"
[    51.246] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    51.246] (II) No input driver/identifier specified (ignoring)
[    51.247] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    51.247] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    51.247] (II) Using input driver 'evdev' for 'Sleep Button'
[    51.247] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.247] (**) Sleep Button: always reports core events
[    51.247] (**) Sleep Button: Device: "/dev/input/event2"
[    51.247] (--) Sleep Button: Found keys
[    51.247] (II) Sleep Button: Configuring as keyboard
[    51.247] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    51.247] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    51.248] (**) Option "xkb_rules" "evdev"
[    51.248] (**) Option "xkb_model" "pc105"
[    51.248] (**) Option "xkb_layout" "us"
[    51.252] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event5)
[    51.252] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    51.252] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    51.252] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event5"
[    51.253] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    51.253] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    51.253] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    51.253] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    51.253] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    51.253] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    51.253] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input5/event5"
[    51.253] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    51.253] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    51.253] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    51.254] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    51.254] (II) No input driver/identifier specified (ignoring)
[    51.255] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event6)
[    51.255] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    51.255] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    51.255] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.255] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    51.255] (**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event6"
[    51.255] (--) Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    51.256] (II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    51.256] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.3/4-1.3:1.0/input/input6/event6"
[    51.256] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
[    51.256] (**) Option "xkb_rules" "evdev"
[    51.256] (**) Option "xkb_model" "pc105"
[    51.256] (**) Option "xkb_layout" "us"
[    51.257] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event7)
[    51.257] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    51.257] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    51.257] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.257] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    51.257] (**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event7"
[    51.257] (--) Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    51.257] (II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    51.257] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.3/4-1.3:1.1/input/input7/event7"
[    51.257] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
[    51.257] (**) Option "xkb_rules" "evdev"
[    51.258] (**) Option "xkb_model" "pc105"
[    51.258] (**) Option "xkb_layout" "us"
[    51.267] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    51.267] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    51.267] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    51.267] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.267] (**) AT Translated Set 2 keyboard: always reports core events
[    51.267] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    51.267] (--) AT Translated Set 2 keyboard: Found keys
[    51.267] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    51.268] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    51.268] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    51.268] (**) Option "xkb_rules" "evdev"
[    51.268] (**) Option "xkb_model" "pc105"
[    51.268] (**) Option "xkb_layout" "us"
[    51.269] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    51.269] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    51.269] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    51.269] (II) LoadModule: "synaptics"
[    51.269] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    51.282] (II) Module synaptics: vendor="X.Org Foundation"
[    51.282] 	compiled for 1.10.1, module version = 1.3.99
[    51.283] 	Module class: X.Org XInput Driver
[    51.283] 	ABI class: X.Org XInput driver, version 12.3
[    51.283] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    51.283] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    51.283] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    51.283] (**) Option "Device" "/dev/input/event10"
[    51.292] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    51.292] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    51.292] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    51.292] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    51.292] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    51.292] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    51.292] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    51.292] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    51.292] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    51.292] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    51.292] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    51.292] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    51.292] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    51.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    51.293] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    51.293] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    51.293] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    51.293] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    51.293] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    51.293] (II) No input driver/identifier specified (ignoring)
[    51.304] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event8)
[    51.304] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    51.304] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    51.304] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.304] (**) HP WMI hotkeys: always reports core events
[    51.304] (**) HP WMI hotkeys: Device: "/dev/input/event8"
[    51.304] (--) HP WMI hotkeys: Found keys
[    51.304] (II) HP WMI hotkeys: Configuring as keyboard
[    51.304] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    51.305] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    51.305] (**) Option "xkb_rules" "evdev"
[    51.305] (**) Option "xkb_model" "pc105"
[    51.305] (**) Option "xkb_layout" "us"
[    56.354] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    56.354] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    56.354] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[    56.354] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    56.374] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    56.374] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    56.374] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[    56.374] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    56.382] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    56.382] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    56.382] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[    56.382] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    70.204] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    70.204] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    70.204] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[    70.204] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   155.591] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   155.592] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   155.592] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[   155.592] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   161.004] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   161.004] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   161.004] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[   161.004] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   161.025] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   161.025] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   161.025] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[   161.025] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   161.028] disable primary dac
[   161.048] disable TV
[   161.087] init memmap
[   161.087] init common
[   161.087] init crtc1
[   161.087] restore memmap
[   161.087] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[   161.087] (II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
[   161.087] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[   161.107] restore common
[   161.107] restore crtc1
[   161.107] restore pll1
[   161.127] finished PLL1
[   161.127] set RMX
[   161.127] set LVDS
[   161.127] enable LVDS
[   161.147] disable primary dac
[   161.147] disable TV
[   191.459] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   191.459] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   191.459] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[   191.459] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   191.502] init memmap
[   191.503] init common
[   191.503] init crtc1
[   191.503] init pll1
[   191.503] restore memmap
[   191.503] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[   191.503] (II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
[   191.503] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[   191.522] restore common
[   191.522] restore crtc1
[   191.522] restore pll1
[   191.522] set RMX
[   191.523] set LVDS
[   191.523] enable LVDS
[   191.542] disable primary dac
[   191.542] disable TV
[   195.881] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   195.881] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   195.881] (II) RADEON(0): Added native panel mode using CVT: 1440x1023
[   195.882] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
hugo@Pavillion:~$ 


Sorry for the long post, First time posting outputs I hope I did it correctly.

Thanks in advance for any help you can provide.

Thank you

Metaxa

---

### Post by Metaxa on 2011-07-29
Bump for any help


Thanks in advance

---

### Post by Metaxa on 2011-08-03
A side note to this, if 11.04 is not a possibility which version should I move this machine to so that it functions properly?



Metaxa

---

### Post by victor1234 on 2011-08-03
black screen on my PC, i went thru Enable VGA mode, press enter, Windows XP loads but then back to black?
something else i could do?

---

### Post by Metaxa on 2011-08-05
Bump for freshness





Metaxa

---

### Post by Furball588 on 2011-08-06
You should be using the radeon module for this.

Not knowing the full story, I'm sort of confused as to why I'm seeing fglrx unloading from your log

In any case, IIRC, 3D is disabled by default with that driver, but to enable it, you would create an xorg.conf to supplment things so glx loads and dri is enabled.

---

### Post by Metaxa on 2011-08-06
Thank you for your response. What additional information would you need to help me fix this issue. Can you point me to a guide for making an xorg.config file? What should I start with? Thanks in advance.


I purged the propriety fglrx drivers and reinstalled the mesa drivers. Then reinstalled xorg core. The problem I have now is when the machine boots, the laptop screen stays blank and I need to connect an external monitor to see my desktop. In " Monitor " it lists dual monitors working in mirrored form. if I de-select it, the main screen still does not turn on. 

My current xrandr output is:

> hugo@Pavillion:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   75.1     70.1  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1440x1023      59.8 +
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

Recent update:

I have installed the edgers ppa to my system, not sure if it auto choose the right driver for me but nothing has changed.


Metaxa

---

### Post by Metaxa on 2011-08-08
Bump for updates to the question.

---

### Post by Metaxa on 2011-08-10
Current state of this project:

1) using latest Mesa drivers from edgers ppa

2) xrandr output reports LVDS as being 0mm x 0mm

3) external monitor works fine main screen will not come alive

4) Main screen turns peruple right before it boots into desktop then goes blanks

5) How to get ubuntu to register the correct physical size of the laptop screen.

5b) I have tried xrandr --output LVDS --fbmm 307x203, screen blinks but does not display anything


Thanks for any help.


Metaxa

---

### Post by Metaxa on 2011-08-14
Bump

---

### Post by Metaxa on 2011-08-23
I have cleared this machine and installed 8.04. I installed the proprietary ATI drivers. My main screen turns on but it is 3/4" lower than it is supposed to be, what I mean by this is remember the old CRT screen that would allow you to use an OSC to move the image up down left right or otherwise manipulate how it comes out? Well I need to move the image up a bit and everything will be OK. I found a link to somoenes xorg.conf files for my specific machine but nothing has changed after using it, any help?



Metaxa

---

