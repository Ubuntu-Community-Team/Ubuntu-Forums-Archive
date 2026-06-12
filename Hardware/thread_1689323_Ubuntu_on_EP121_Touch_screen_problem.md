---
title: "Ubuntu on EP121 Touch screen problem"
date: 2011-02-16
forum: Hardware
---

### Post by eugenet on 2011-02-16
Hi there,

I just got myself an Asus EP121 tablet PC ([http://promos.asus.com/US/ASUS_EeeSlate/index.htm](http://promos.asus.com/US/ASUS_EeeSlate/index.htm)) and put Ubuntu 10.10 on it :)
All works quite well out of the box, except for the touch screen :/
The wacom digitizer works perfectly there, but the eGalax finger touch does not, no matter what I do.
So far I followed every single tutorial I could find on the web with eGalax in it's name, but no luck anywhere. The most I achieved is I managed to make the touch screen work like a mousepad, meaning that the touch coordinates are not absolute, but relative :/ and I have no touch click (not to mention multitouch).
The xinput list call the device like so:
eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller id=15

lsusb shows this:
oeef:a001 D-WAV Scientific Co., Ltd

so far I tried to get eGalax driver from the website and installed it, but once activated the driver does nothing as it can not find the device :?

I tried simple evdev, then it works as regular touchpade with relative coordinates. Xorg log says that it finds it (event8) to have absolute axes, and registers as absolute touchpad, but it still behaves as a relative one :/
xorg also finds it as a mouse8, but initializing svdev on it resilts in an error, so I disabled it.

Also, I had to disable the synaptics detection because using synaptics driver with this device results in it registering mouse wheel scroll at all times :O making the desktop unusable :/

Does anyone have one experience with eGalax, and behavior like that.

---

### Post by MoGa on 2011-02-17
very nice device, I wonder if this issue will be solved,
I  hate windows and im buying this computer only if it runs ubuntu.

So please keep us updated

---

### Post by mookiemu on 2011-02-21
Please let us know if you get this working as I will only get this if it runs Ubuntu as well.

---

### Post by eugenet on 2011-02-22
Ok I got it working with evtouch driver. Had to configure it manually tough :/ Bluetooth does not work. no matter what I do, and the special keys only work partly *sigh*
Other then that all is well.

---

### Post by mookiemu on 2011-02-23
> **eugenet said:**
> Ok I got it working with evtouch driver. Had to configure it manually tough :/ Bluetooth does not work. no matter what I do, and the special keys only work partly *sigh*
Other then that all is well.

That's awesome! Too bad about the bluetooth.
Bet the battery life is better than with windows.

---

### Post by arkahn on 2011-03-20
> **eugenet said:**
> Ok I got it working with evtouch driver. Had to configure it manually tough :/ Bluetooth does not work. no matter what I do, and the special keys only work partly *sigh*
Other then that all is well.

eugenet, could you post your evtouch config?  I just got an asus ep121 myself and have yet to get the touchscreen working properly.

Beyond an install of Ubuntu Netbook 10.10 I installed xserver-xorg-input-evtouch and tried to follow the author's instructions [*here*]("http://www.conan.de/touchscreen/evtouch.html").

Currently, the tablet works fine as long as I don't touch the screen.  ;)  After an initial install the screen would act like a big touchpad, registering finger movements as relative mouse pointer control except for tapping that doesn't produce mouse clicks.  Now, (after tinkering in /usr/share/X11/xorg.conf.d/) if I accidentally touch the screen it messes up mouse input by always wanting to scroll up.

For the curious, here's a copy of my /var/log/Xorg.0.log
```
[     3.920] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[     3.920] X Protocol Version 11, Revision 0
[     3.920] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[     3.920] Current Operating System: Linux xxxxxxxx 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686
[     3.920] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e1d0e55-6d1e-43ba-9db8-2af79b6d0f81 ro quiet splash
[     3.920] Build Date: 09 January 2011  12:14:58PM
[     3.920] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[     3.920] Current version of pixman: 0.18.4
[     3.920] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     3.920] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.920] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 20 08:26:51 2011
[     3.965] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.966] (==) No Layout section.  Using the first Screen section.
[     3.966] (==) No screen section available. Using defaults.
[     3.966] (**) |-->Screen "Default Screen Section" (0)
[     3.966] (**) |   |-->Monitor "<default monitor>"
[     3.966] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     3.966] (==) Automatically adding devices
[     3.966] (==) Automatically enabling devices
[     3.966] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.966] 	Entry deleted from font path.
[     3.966] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     3.966] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.966] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.966] (II) Loader magic: 0x81f9b00
[     3.966] (II) Module ABI versions:
[     3.966] 	X.Org ANSI C Emulation: 0.4
[     3.966] 	X.Org Video Driver: 8.0
[     3.966] 	X.Org XInput driver : 11.0
[     3.966] 	X.Org Server Extension : 4.0
[     3.968] (--) PCI:*(0:0:2:0) 8086:0046:1043:1be2 rev 24, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x0000e080/8
[     3.968] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.968] (II) LoadModule: "extmod"
[     3.969] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     3.969] (II) Module extmod: vendor="X.Org Foundation"
[     3.969] 	compiled for 1.9.0, module version = 1.0.0
[     3.969] 	Module class: X.Org Server Extension
[     3.969] 	ABI class: X.Org Server Extension, version 4.0
[     3.969] (II) Loading extension MIT-SCREEN-SAVER
[     3.969] (II) Loading extension XFree86-VidModeExtension
[     3.969] (II) Loading extension XFree86-DGA
[     3.969] (II) Loading extension DPMS
[     3.969] (II) Loading extension XVideo
[     3.969] (II) Loading extension XVideo-MotionCompensation
[     3.969] (II) Loading extension X-Resource
[     3.970] (II) LoadModule: "dbe"
[     3.970] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     3.970] (II) Module dbe: vendor="X.Org Foundation"
[     3.970] 	compiled for 1.9.0, module version = 1.0.0
[     3.970] 	Module class: X.Org Server Extension
[     3.970] 	ABI class: X.Org Server Extension, version 4.0
[     3.970] (II) Loading extension DOUBLE-BUFFER
[     3.970] (II) LoadModule: "glx"
[     3.970] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.970] (II) Module glx: vendor="X.Org Foundation"
[     3.970] 	compiled for 1.9.0, module version = 1.0.0
[     3.970] 	ABI class: X.Org Server Extension, version 4.0
[     3.970] (==) AIGLX enabled
[     3.970] (II) Loading extension GLX
[     3.970] (II) LoadModule: "record"
[     3.971] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     3.971] (II) Module record: vendor="X.Org Foundation"
[     3.971] 	compiled for 1.9.0, module version = 1.13.0
[     3.971] 	Module class: X.Org Server Extension
[     3.971] 	ABI class: X.Org Server Extension, version 4.0
[     3.971] (II) Loading extension RECORD
[     3.971] (II) LoadModule: "dri"
[     3.971] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     3.971] (II) Module dri: vendor="X.Org Foundation"
[     3.971] 	compiled for 1.9.0, module version = 1.0.0
[     3.971] 	ABI class: X.Org Server Extension, version 4.0
[     3.971] (II) Loading extension XFree86-DRI
[     3.971] (II) LoadModule: "dri2"
[     3.972] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     3.972] (II) Module dri2: vendor="X.Org Foundation"
[     3.972] 	compiled for 1.9.0, module version = 1.2.0
[     3.972] 	ABI class: X.Org Server Extension, version 4.0
[     3.972] (II) Loading extension DRI2
[     3.972] (==) Matched intel as autoconfigured driver 0
[     3.972] (==) Matched vesa as autoconfigured driver 1
[     3.972] (==) Matched fbdev as autoconfigured driver 2
[     3.972] (==) Assigned the driver to the xf86ConfigLayout
[     3.972] (II) LoadModule: "intel"
[     3.973] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.973] (II) Module intel: vendor="X.Org Foundation"
[     3.973] 	compiled for 1.9.0, module version = 2.12.0
[     3.973] 	Module class: X.Org Video Driver
[     3.973] 	ABI class: X.Org Video Driver, version 8.0
[     3.973] (II) LoadModule: "vesa"
[     3.973] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.973] (II) Module vesa: vendor="X.Org Foundation"
[     3.973] 	compiled for 1.8.99.905, module version = 2.3.0
[     3.973] 	Module class: X.Org Video Driver
[     3.973] 	ABI class: X.Org Video Driver, version 8.0
[     3.973] (II) LoadModule: "fbdev"
[     3.974] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.974] (II) Module fbdev: vendor="X.Org Foundation"
[     3.974] 	compiled for 1.8.99.905, module version = 0.4.2
[     3.974] 	ABI class: X.Org Video Driver, version 8.0
[     3.974] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[     3.975] (II) VESA: driver for VESA chipsets: vesa
[     3.975] (II) FBDEV: driver for framebuffer: fbdev
[     3.975] (++) using VT number 7

[     3.975] (WW) Falling back to old probe method for vesa
[     3.975] (WW) Falling back to old probe method for fbdev
[     3.975] (II) Loading sub module "fbdevhw"
[     3.975] (II) LoadModule: "fbdevhw"
[     3.975] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.975] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.975] 	compiled for 1.9.0, module version = 0.0.2
[     3.975] 	ABI class: X.Org Video Driver, version 8.0
[     3.978] drmOpenDevice: node name is /dev/dri/card0
[     3.978] drmOpenDevice: open result is 9, (OK)
[     3.978] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     3.978] drmOpenDevice: node name is /dev/dri/card0
[     3.978] drmOpenDevice: open result is 9, (OK)
[     3.978] drmOpenByBusid: drmOpenMinor returns 9
[     3.978] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     3.978] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     3.978] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     3.978] (==) intel(0): RGB weight 888
[     3.978] (==) intel(0): Default visual is TrueColor
[     3.978] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[     3.978] (--) intel(0): Chipset: "Arrandale"
[     3.978] (==) intel(0): video overlay key set to 0x101fe
[     3.995] (II) intel(0): Output VGA1 has no monitor section
[     3.995] (II) intel(0): Output LVDS1 has no monitor section
[     3.995] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[     4.005] (II) intel(0): Output HDMI1 has no monitor section
[     4.006] (II) intel(0): Output DP1 has no monitor section
[     4.023] (II) intel(0): EDID for output VGA1
[     4.023] (II) intel(0): EDID for output LVDS1
[     4.023] (II) intel(0): Manufacturer: BOE  Model: 4011  Serial#: 0
[     4.023] (II) intel(0): Year: 2009  Week: 0
[     4.023] (II) intel(0): EDID Version: 1.3
[     4.023] (II) intel(0): Digital Display Input
[     4.023] (II) intel(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[     4.023] (II) intel(0): Gamma: 2.20
[     4.023] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[     4.023] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     4.023] (II) intel(0): First detailed timing is preferred mode
[     4.023] (II) intel(0): redX: 0.539 redY: 0.346   greenX: 0.339 greenY: 0.562
[     4.023] (II) intel(0): blueX: 0.148 blueY: 0.095   whiteX: 0.313 whiteY: 0.329
[     4.023] (II) intel(0): Manufacturer's mask: 0
[     4.023] (II) intel(0): Supported detailed timing:
[     4.023] (II) intel(0): clock: 75.2 MHz   Image Size:  261 x 163 mm
[     4.023] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1412 h_blank_end 1522 h_border: 0
[     4.023] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[     4.023] (II) intel(0): Supported detailed timing:
[     4.023] (II) intel(0): clock: 75.2 MHz   Image Size:  261 x 163 mm
[     4.023] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1412 h_blank_end 1522 h_border: 0
[     4.023] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[     4.023] (II) intel(0): Unknown vendor-specific block f
[     4.023] (II) intel(0):  HV121WX6-111
[     4.023] (II) intel(0): EDID (in hex):
[     4.023] (II) intel(0): 	00ffffffffffff0009e5114000000000
[     4.023] (II) intel(0): 	00130103801a1078ea2f158a58568f26
[     4.023] (II) intel(0): 	18505400000001010101010101010101
[     4.023] (II) intel(0): 	0101010101015c1d00f2502017303054
[     4.023] (II) intel(0): 	360005a3100000195c1d00f250201730
[     4.023] (II) intel(0): 	3054360005a3100000190000000f0081
[     4.023] (II) intel(0): 	0a3c810a3c1e0a0000009e08000000fe
[     4.023] (II) intel(0): 	0048563132315758362d3131310a0003
[     4.024] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[     4.024] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[     4.024] (II) intel(0): Printing probed modes for output LVDS1
[     4.024] (II) intel(0): Modeline "1280x800"x60.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[     4.024] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     4.024] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     4.024] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     4.024] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     4.035] (II) intel(0): EDID for output HDMI1
[     4.036] (II) intel(0): EDID for output DP1
[     4.036] (II) intel(0): Output VGA1 disconnected
[     4.036] (II) intel(0): Output LVDS1 connected
[     4.036] (II) intel(0): Output HDMI1 disconnected
[     4.036] (II) intel(0): Output DP1 disconnected
[     4.036] (II) intel(0): Using exact sizes for initial modes
[     4.036] (II) intel(0): Output LVDS1 using initial mode 1280x800
[     4.036] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     4.036] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[     4.036] (==) intel(0): DPI set to (96, 96)
[     4.036] (II) Loading sub module "fb"
[     4.036] (II) LoadModule: "fb"
[     4.036] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.036] (II) Module fb: vendor="X.Org Foundation"
[     4.036] 	compiled for 1.9.0, module version = 1.0.0
[     4.036] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.036] (II) UnloadModule: "vesa"
[     4.036] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.036] (II) UnloadModule: "fbdev"
[     4.036] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.037] (II) UnloadModule: "fbdevhw"
[     4.037] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[     4.037] (==) Depth 24 pixmap format is 32 bpp
[     4.037] (II) intel(0): [DRI2] Setup complete
[     4.037] (II) intel(0): [DRI2]   DRI driver: i965
[     4.037] (**) intel(0): Tiling enabled
[     4.037] (**) intel(0): SwapBuffers wait enabled
[     4.037] (==) intel(0): VideoRam: 262144 KB
[     4.037] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[     4.048] (II) UXA(0): Driver registered support for the following operations:
[     4.048] (II)         solid
[     4.048] (II)         copy
[     4.048] (II)         composite (RENDER acceleration)
[     4.048] (II)         put_image
[     4.048] (II)         get_image
[     4.048] (==) intel(0): Backing store disabled
[     4.048] (==) intel(0): Silken mouse enabled
[     4.048] (II) intel(0): Initializing HW Cursor
[     4.084] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.086] (==) intel(0): DPMS enabled
[     4.086] (==) intel(0): Intel XvMC decoder enabled
[     4.086] (II) intel(0): Set up textured video
[     4.087] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     4.087] (II) intel(0): direct rendering: DRI2 Enabled
[     4.087] (--) RandR disabled
[     4.087] (II) Initializing built-in extension Generic Event Extension
[     4.087] (II) Initializing built-in extension SHAPE
[     4.087] (II) Initializing built-in extension MIT-SHM
[     4.087] (II) Initializing built-in extension XInputExtension
[     4.087] (II) Initializing built-in extension XTEST
[     4.087] (II) Initializing built-in extension BIG-REQUESTS
[     4.087] (II) Initializing built-in extension SYNC
[     4.087] (II) Initializing built-in extension XKEYBOARD
[     4.087] (II) Initializing built-in extension XC-MISC
[     4.087] (II) Initializing built-in extension SECURITY
[     4.087] (II) Initializing built-in extension XINERAMA
[     4.087] (II) Initializing built-in extension XFIXES
[     4.087] (II) Initializing built-in extension RENDER
[     4.087] (II) Initializing built-in extension RANDR
[     4.087] (II) Initializing built-in extension COMPOSITE
[     4.087] (II) Initializing built-in extension DAMAGE
[     4.087] (II) Initializing built-in extension GESTURE
[     4.107] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.107] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.107] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.107] (II) AIGLX: enabled GLX_SGI_make_current_read
[     4.107] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.107] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[     4.107] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.108] (II) intel(0): Setting screen physical size to 338 x 211
[     4.132] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.143] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     4.143] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.143] (II) LoadModule: "evdev"
[     4.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.144] (II) Module evdev: vendor="X.Org Foundation"
[     4.144] 	compiled for 1.9.0, module version = 2.3.2
[     4.144] 	Module class: X.Org XInput Driver
[     4.144] 	ABI class: X.Org XInput driver, version 11.0
[     4.144] (**) Power Button: always reports core events
[     4.144] (**) Power Button: Device: "/dev/input/event3"
[     4.176] (II) Power Button: Found keys
[     4.176] (II) Power Button: Configuring as keyboard
[     4.176] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     4.176] (**) Option "xkb_rules" "evdev"
[     4.176] (**) Option "xkb_model" "pc105"
[     4.176] (**) Option "xkb_layout" "us"
[     4.177] (II) config/udev: Adding input device Video Bus (/dev/input/event13)
[     4.181] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.181] (**) Video Bus: always reports core events
[     4.181] (**) Video Bus: Device: "/dev/input/event13"
[     4.204] (II) Video Bus: Found keys
[     4.204] (II) Video Bus: Configuring as keyboard
[     4.204] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[     4.204] (**) Option "xkb_rules" "evdev"
[     4.204] (**) Option "xkb_model" "pc105"
[     4.204] (**) Option "xkb_layout" "us"
[     4.207] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     4.207] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.207] (**) Power Button: always reports core events
[     4.207] (**) Power Button: Device: "/dev/input/event2"
[     4.232] (II) Power Button: Found keys
[     4.232] (II) Power Button: Configuring as keyboard
[     4.232] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     4.232] (**) Option "xkb_rules" "evdev"
[     4.232] (**) Option "xkb_model" "pc105"
[     4.232] (**) Option "xkb_layout" "us"
[     4.233] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     4.233] (II) No input driver/identifier specified (ignoring)
[     4.233] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     4.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     4.233] (**) Sleep Button: always reports core events
[     4.233] (**) Sleep Button: Device: "/dev/input/event1"
[     4.248] (II) Sleep Button: Found keys
[     4.248] (II) Sleep Button: Configuring as keyboard
[     4.248] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[     4.248] (**) Option "xkb_rules" "evdev"
[     4.248] (**) Option "xkb_model" "pc105"
[     4.248] (**) Option "xkb_layout" "us"
[     4.251] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event12)
[     4.251] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[     4.251] (**) USB 2.0 Camera: always reports core events
[     4.251] (**) USB 2.0 Camera: Device: "/dev/input/event12"
[     4.280] (II) USB 2.0 Camera: Found keys
[     4.280] (II) USB 2.0 Camera: Configuring as keyboard
[     4.280] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
[     4.280] (**) Option "xkb_rules" "evdev"
[     4.280] (**) Option "xkb_model" "pc105"
[     4.280] (**) Option "xkb_layout" "us"
[     4.283] (II) config/udev: Adding input device Razer Razer Copperhead Laser Mouse (/dev/input/event8)
[     4.283] (**) Razer Razer Copperhead Laser Mouse: Applying InputClass "evdev pointer catchall"
[     4.283] (**) Razer Razer Copperhead Laser Mouse: always reports core events
[     4.283] (**) Razer Razer Copperhead Laser Mouse: Device: "/dev/input/event8"
[     4.312] (II) Razer Razer Copperhead Laser Mouse: Found 12 mouse buttons
[     4.312] (II) Razer Razer Copperhead Laser Mouse: Found scroll wheel(s)
[     4.312] (II) Razer Razer Copperhead Laser Mouse: Found relative axes
[     4.312] (II) Razer Razer Copperhead Laser Mouse: Found x and y relative axes
[     4.312] (II) Razer Razer Copperhead Laser Mouse: Configuring as mouse
[     4.312] (**) Razer Razer Copperhead Laser Mouse: YAxisMapping: buttons 4 and 5
[     4.312] (**) Razer Razer Copperhead Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.312] (II) XINPUT: Adding extended input device "Razer Razer Copperhead Laser Mouse" (type: MOUSE)
[     4.312] (II) Razer Razer Copperhead Laser Mouse: initialized for relative axes.
[     4.312] (II) config/udev: Adding input device Razer Razer Copperhead Laser Mouse (/dev/input/mouse2)
[     4.313] (II) No input driver/identifier specified (ignoring)
[     4.313] (II) config/udev: Adding input device Razer Razer Copperhead Laser Mouse (/dev/input/event9)
[     4.313] (**) Razer Razer Copperhead Laser Mouse: Applying InputClass "evdev keyboard catchall"
[     4.313] (**) Razer Razer Copperhead Laser Mouse: always reports core events
[     4.313] (**) Razer Razer Copperhead Laser Mouse: Device: "/dev/input/event9"
[     4.332] (II) Razer Razer Copperhead Laser Mouse: Found keys
[     4.332] (II) Razer Razer Copperhead Laser Mouse: Configuring as keyboard
[     4.332] (II) XINPUT: Adding extended input device "Razer Razer Copperhead Laser Mouse" (type: KEYBOARD)
[     4.332] (**) Option "xkb_rules" "evdev"
[     4.332] (**) Option "xkb_model" "pc105"
[     4.332] (**) Option "xkb_layout" "us"
[     4.333] (II) config/udev: Adding input device HID 0566:3013 (/dev/input/event10)
[     4.333] (**) HID 0566:3013: Applying InputClass "evdev keyboard catchall"
[     4.333] (**) HID 0566:3013: always reports core events
[     4.333] (**) HID 0566:3013: Device: "/dev/input/event10"
[     4.348] (II) HID 0566:3013: Found keys
[     4.348] (II) HID 0566:3013: Configuring as keyboard
[     4.348] (II) XINPUT: Adding extended input device "HID 0566:3013" (type: KEYBOARD)
[     4.348] (**) Option "xkb_rules" "evdev"
[     4.348] (**) Option "xkb_model" "pc105"
[     4.348] (**) Option "xkb_layout" "us"
[     4.349] (II) config/udev: Adding input device HID 0566:3013 (/dev/input/event11)
[     4.349] (**) HID 0566:3013: Applying InputClass "evdev keyboard catchall"
[     4.349] (**) HID 0566:3013: always reports core events
[     4.349] (**) HID 0566:3013: Device: "/dev/input/event11"
[     4.368] (II) HID 0566:3013: Found 1 mouse buttons
[     4.368] (II) HID 0566:3013: Found scroll wheel(s)
[     4.368] (II) HID 0566:3013: Found relative axes
[     4.368] (II) HID 0566:3013: Found absolute axes
[     4.368] (II) evdev-grail: failed to open grail, no gesture support
[     4.368] (II) HID 0566:3013: Found keys
[     4.368] (II) HID 0566:3013: Configuring as mouse
[     4.368] (II) HID 0566:3013: Configuring as keyboard
[     4.368] (**) HID 0566:3013: YAxisMapping: buttons 4 and 5
[     4.368] (**) HID 0566:3013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.368] (II) XINPUT: Adding extended input device "HID 0566:3013" (type: KEYBOARD)
[     4.368] (**) Option "xkb_rules" "evdev"
[     4.368] (**) Option "xkb_model" "pc105"
[     4.368] (**) Option "xkb_layout" "us"
[     4.368] (EE) HID 0566:3013: failed to initialize for relative axes.
[     4.368] (II) HID 0566:3013: initialized for absolute axes.
[     4.369] (II) config/udev: Adding input device Wacom ISDv4 90 Pen (/dev/input/event5)
[     4.369] (**) Wacom ISDv4 90 Pen: Applying InputClass "evdev tablet catchall"
[     4.369] (**) Wacom ISDv4 90 Pen: always reports core events
[     4.369] (**) Wacom ISDv4 90 Pen: Device: "/dev/input/event5"
[     4.384] (II) Wacom ISDv4 90 Pen: Found absolute axes
[     4.394] (II) evdev-grail: failed to open grail, no gesture support
[     4.394] (II) Wacom ISDv4 90 Pen: Found x and y absolute axes
[     4.394] (II) Wacom ISDv4 90 Pen: Found absolute tablet.
[     4.394] (II) Wacom ISDv4 90 Pen: Configuring as tablet
[     4.394] (**) Wacom ISDv4 90 Pen: YAxisMapping: buttons 4 and 5
[     4.394] (**) Wacom ISDv4 90 Pen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.394] (II) XINPUT: Adding extended input device "Wacom ISDv4 90 Pen" (type: TABLET)
[     4.394] (II) Wacom ISDv4 90 Pen: initialized for absolute axes.
[     4.394] (II) config/udev: Adding input device Wacom ISDv4 90 Pen (/dev/input/mouse0)
[     4.394] (II) No input driver/identifier specified (ignoring)
[     4.395] (II) config/udev: Adding input device eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller (/dev/input/event7)
[     4.395] (**) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Applying InputClass "evdev touchpad catchall"
[     4.395] (**) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: always reports core events
[     4.395] (**) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Device: "/dev/input/event7"
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Found 8 mouse buttons
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Found absolute axes
[     4.412] (II) evdev-grail: failed to open grail, no gesture support
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Found x and y absolute axes
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Found absolute touchpad.
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: Configuring as touchpad
[     4.412] (**) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: YAxisMapping: buttons 4 and 5
[     4.412] (**) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.412] (II) XINPUT: Adding extended input device "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" (type: TOUCHPAD)
[     4.412] (II) eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller: initialized for absolute axes.
[     4.412] (II) config/udev: Adding input device eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller (/dev/input/mouse1)
[     4.413] (II) No input driver/identifier specified (ignoring)
[     4.415] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event6)
[     4.415] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     4.415] (**) Eee PC WMI hotkeys: always reports core events
[     4.415] (**) Eee PC WMI hotkeys: Device: "/dev/input/event6"
[     4.432] (II) Eee PC WMI hotkeys: Found keys
[     4.432] (II) Eee PC WMI hotkeys: Configuring as keyboard
[     4.432] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD)
[     4.432] (**) Option "xkb_rules" "evdev"
[     4.432] (**) Option "xkb_model" "pc105"
[     4.432] (**) Option "xkb_layout" "us"
[     4.432] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     4.432] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.432] (**) AT Translated Set 2 keyboard: always reports core events
[     4.433] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     4.456] (II) AT Translated Set 2 keyboard: Found keys
[     4.456] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[     4.456] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[     4.456] (**) Option "xkb_rules" "evdev"
[     4.456] (**) Option "xkb_model" "pc105"
[     4.456] (**) Option "xkb_layout" "us"
[     4.831] (II) intel(0): EDID vendor "BOE", prod id 16401
[     4.831] (II) intel(0): Printing DDC gathered Modelines:
[     4.831] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[     4.861] (II) intel(0): EDID vendor "BOE", prod id 16401
[     4.861] (II) intel(0): Printing DDC gathered Modelines:
[     4.861] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[     4.890] (II) intel(0): EDID vendor "BOE", prod id 16401
[     4.890] (II) intel(0): Printing DDC gathered Modelines:
[     4.890] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[     4.920] (II) intel(0): EDID vendor "BOE", prod id 16401
[     4.920] (II) intel(0): Printing DDC gathered Modelines:
[     4.921] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[    10.855] (II) intel(0): EDID vendor "BOE", prod id 16401
[    10.855] (II) intel(0): Printing DDC gathered Modelines:
[    10.855] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1652.958] (II) intel(0): EDID vendor "BOE", prod id 16401
[  1652.958] (II) intel(0): Printing DDC gathered Modelines:
[  1652.958] (II) intel(0): Modeline "1280x800"x0.0   75.16  1280 1328 1412 1522  800 803 809 823 -hsync -vsync (49.4 kHz)

```

---

### Post by klick0 on 2011-03-20
arkhahn,  I too have the ep121 and am trying to get the touchscreen working as I type.  I did an install of 10.10 Desktop i386, the touchscreen works like a large touchpad as yours, look at this line from your log file:[FONT=monospace]

(II) XINPUT: Adding extended input device "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" (type: TOUCHPAD)

Actually that's from mine, but obviously it's identical to yours.  For some reason it's detecting it as a touchpad, I'm attempting to figure out how to force an evdev device to TOUCHSCREEN type, does anyonw know how to do this?  I'm looking through the X11 parser to see what parameter I can use.  I've tried MatchIsTouchscreen "on", but that actually is meant for udev detection, and checks to see if it's touchscreen, which clearly it thinks the hardware is a touchpad.  Option "Touchscreen" "on", true, yes doesn't work.  

I also installed the eGalax driver, which didn't work, it loaded the egalax object, the log said it did, but then their own calibrator said there was no touchscreen.

I tried evtouch, which did nothing, the log file said... i forget, let me redo it:
XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)

Actually, ok it adds it, touching the screen make it move to the lower right, i dunno, i don't even see it.
root@iq-EP121:~# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus                   id=14    [slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                         id=15    [slave  pointer  (2)]
&#9116;   &#8627; eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller    id=16    [slave  pointer  (2)]


EVTouch is the evtouch driver obviously in this case.  Oh yea, if you didn't know, the Wacom digitizer pen works fine, both teh pen and eraser, and was calibrated properly.  Its on the side of your tablet hidden, it uses a digitizer (magnet) so it's a completely different hardware interface, and worked out of the box for me.

back to evtouch:
root@iq-EP121:~# xinput query-state 15
ValuatorClass Mode=Absolute Proximity=In
    valuator[0]=1279
    valuator[1]=799


Those coordinates never change for the EVtouch driver.  evdev can obviously interpret the points, it's just in the wrong mode, touchpad vs touchscreen.  If we could just force evdev into touchscreen mode, everything would be fine.  xinput_calibrator would work i'm sure, doesn't even try to run on touchpads for obvious reasons.  

evtouch is also using the correct input stream, i checked.

I'm gonna continue to figure out a way to force evdev to touchscreen mode.

Ross


[/FONT]

---

### Post by klick0 on 2011-03-20
arkahn:
Actually I just looked at your WACOM output again, i don't think you have the wacom driver installed, perhaps because yer running netbook version and they don't install that by default, i dunno.  

With the desktop version i had to uninstall the synaptics driver as well (well i disabled it) since the eGalax attempts to use that at first, it acted like a touchpad as well though.  Granted evdev driver didn't make it work though...

Ross

---

### Post by klick0 on 2011-03-20
Ok, I got it to work, not very gracefully, but it works.  Forcing evdev to touchscreen mode was the key, i couldn't find a nice way to do this though, so i downloaded the evdev source code v2.5.0 and just disabled the touchpad interface, and forced it to touchscreen.  Here is what I changed in evdev.c:
```

            } else if (TestBit(ABS_PRESSURE, pEvdev->abs_bitmask) ||
                TestBit(BTN_TOUCH, pEvdev->key_bitmask)) {
                //if (has_lmr || TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
                  //  xf86Msg(X_PROBED, "%s: Found absolute touchpad.\n", pInfo->name);
                 //   pEvdev->flags |= EVDEV_TOUCHPAD;
                 //   memset(pEvdev->old_vals, -1, sizeof(int) * pEvdev->num_vals);
                //} else {
                    xf86Msg(X_PROBED, "%s: Found absolute touchscreen\n", pInfo->name);
                    pEvdev->flags |= EVDEV_TOUCHSCREEN;
                    pEvdev->flags |= EVDEV_BUTTON_EVENTS;
                //}
            }

```All the lines with the // in front i put, as you can see what i did was crude, but it proved my point.  There probably is one line of config text I could of added to accomplish this, but I couldn't figure out what it is.  So if anyone knows how to force evdev to touchscreen then that would be the key.

The initial calibration was perfect.  It appears to have multi-touch, but since this version of xwindows doesn't have it, it of course doesn't really work.  The mouse pointer flickers between the 2 positions.  If it didn't have multitouch, or was a resistive touchscreen, it would just goto the point inbetween the 2 points you are touching.  I just checked 3 fingers, and 3 fingers doesn't work, it stops it.  So it seems to be 2 finger multi-touch max.  Ubuntu 11.04 should support that (or so i've read).

My 50-egalax.conf say:
```
Section "InputClass"
        Identifier "eGalax touchscreen"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchDevicePath "/dev/input/event*"
        #MatchIsTouchscreen "on"
        Driver "evdev"
EndSection
```Which is just forcing the evdev driver, nothing else.

Also, I rotate the screen with:
DISPLAY=":0.0"
xrandr -o right
xinput set-prop "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" "Evdev Axes Swap" 1
xinput set-prop "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" "Evdev Axis Inversion" 0 1
xinput set-prop "Wacom ISDv4 90 Pen stylus" "Wacom Rotation" 1

With slight modification you could rotate it anyway you want.  The Wacom is the digitizer interface, it has to be rotated as well, I found that I didn't have to rotate the Pen eraser interface as it follows the stylus interface, which makes sense I guess.

I could post my evdev_drv.so, but there has to be a better way to get the touchscreen mode, so once you get that, the touchscreen will work.

I'm gonna look into multi-touch stuff, I think the netbook version has multi-touch support doesn't it?  perhaps I should re-load with that and try that.

Ross

---

### Post by arkahn on 2011-03-26
klick0, thank you so much for your help!

---

### Post by pastabasta on 2011-03-28
For those of you with bluetooth problems, see this thread:

[http://ubuntuforums.org/showthread.php?p=10612268&posted=1#post10612268](http://ubuntuforums.org/showthread.php?p=10612268&posted=1#post10612268)

You need updated drivers.  I got mine working.

---

### Post by Victormd on 2011-03-29
So, bluetooth is up and running.
> Ok, I got it to work, not very gracefully, but it works. Forcing evdev to touchscreen mode was the key, i couldn't find a nice way to do this though, so i downloaded the evdev source code v2.5.0 and just disabled the touchpad interface, and forced it to touchscreen. Here is what I changed in evdev.c
Klick0, can you post the link from where you downloaded the evdev source?

Thanks,
Victor

---

### Post by klick0 on 2011-04-02
You can download the evdev driver from:

[ftp://xorg.mirrors.pair.com/individual/driver/xf86-input-evdev-2.5.0.tar.gz](ftp://xorg.mirrors.pair.com/individual/driver/xf86-input-evdev-2.5.0.tar.gz)

I just realized, evdev 2.6.0 is out, the mirror I used before only had upto 2.5.0.  You may just want to try 2.6.0.

I'm gonna see if 2.6.0 detects the device as a touchscreen, if it does, then problem solved.  If not, you could still probably use 2.6.0 if you wanted, and just make the same/similiar change as above.

Ubuntu 11.04 beta just came out, has some multi-touch support with their new interface.  I think i'm gonna load that up to see how it works.  

Ross

---

### Post by davim on 2011-04-02
How does 11.04 handle this hardware? Does touch and bluetooth work out of the box?

---

### Post by Victormd on 2011-04-03
> Ubuntu 11.04 beta just came out, has some multi-touch support with their new interface.  I think i'm gonna load that up to see how it works. 

I tried to install 11.04 alpha on the slate but it messed up my grub so I didn't even test it.

I was running 11.04 alpha on my desktop and ran into similar bluetooth issues - not sure if the updated bluez made it to the repos but would imagine it has. I'm going to give it a try later as well.

---

### Post by buraitopengin on 2011-04-03
I'll try it out once I receive the Slate (the slate is Temporarily not available here in France).

So, what about accelerated graphics? Can you play HD videos smoothly?

---

### Post by Victormd on 2011-04-03
haven't tried to play hd in ubuntu but it can handle hd under win7 no problem...

---

### Post by buraitopengin on 2011-04-03
> **Victormd said:**
> haven't tried to play hd in ubuntu but it can handle hd under win7 no problem...

That's good news, but I try to avoid using Windows as much as possible ; I don't feel like home using this Operating System.

Win7 is more shiny than the previous release, but nowadays, we can really do a lot with Linux :

[LIST]
[*] Synfig
[*] Inkscape
[*] Mypaint
[*] The Gimp (really need a new UI)
[*] Blender
[*] Openshot
[*] Scribes
[/LIST]

Gosh! If everything work on the Asus slate it might be a dream come true.

---

### Post by Victormd on 2011-04-03
> That's good news, but I try to avoid using Windows as much as possible ; I don't feel like home using this Operating System.
I agree with you but since I haven't been able to get multi-touch working on the slate, I've relied on Win7 but intend to ditch it as soon as I get ubuntu working!! :)

---

### Post by pastabasta on 2011-04-04
> **klick0 said:**
> arkhahn, 

[FONT=monospace] I tried evtouch, which did nothing, the log file said... i forget, let me redo it:
XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)

Actually, ok it adds it, touching the screen make it move to the lower right, i dunno, i don't even see it.

[/FONT]

Hi Klick0,

what do  you mean exactly when you say you tried evtouch?  I went to synaptics to download xserver-xorg-input-evtouch, but i don't get the output "[FONT=monospace]EVTouch TouchScreen                         id=15    [slave  pointer  (2)]" when I type xinput list.  I tried the next steps you suggested, but they didn't work, so I think i did osmething wrong when installing evtouch drivers.

[/FONT] I'd like to use your solution to get touchscreen working, even if it doesn't have multi touch. 

Thanks

~Paolo

---

### Post by buraitopengin on 2011-04-04
> **Victormd said:**
> I agree with you but since I haven't been able to get multi-touch working on the slate, I've relied on Win7 but intend to ditch it as soon as I get ubuntu working!! :)

Great, don't hesitate to post if you find a reliable solution ;)

---

### Post by Victormd on 2011-04-04
11.04 beta update: bluetooth is broken and no multitouch.
stylus still works out of the box and virtual keyboard usable...

---

### Post by Victormd on 2011-04-04
xinput list:
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=10	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

---

### Post by Victormd on 2011-04-04
ok, second update: finger touch still acts as a big touch pad but you can use both stylus and finger, and not have the same issues as in 10.10 (i.e. scrambled scrolling up, etc.), been using 11.04 now for a few hrs trying different packages and no restart needed yet to restore input. Guess that's a plus, but still no bluetooth-using "onboard" virtual keyboard.

---

### Post by buraitopengin on 2011-04-05
> **Victormd said:**
> ok, second update: finger touch still acts as a big touch pad but you can use both stylus and finger, and not have the same issues as in 10.10 (i.e. scrambled scrolling up, etc.), been using 11.04 now for a few hrs trying different packages and no restart needed yet to restore input. Guess that's a plus, but still no bluetooth-using "onboard" virtual keyboard.

The ppa package mentionned by you earlier (bluez something) don't work for Ubuntu 11.04?

Thanks a lot for tying so hard to make everything working, i ordered mine yesterday. I've got something like 30 days to wait till they refill their stock.

---

### Post by Victormd on 2011-04-05
> The ppa package mentionned by you earlier (bluez something) don't work for Ubuntu 11.04?
no, couldn't even start bluetooth... stick to 10.10 for now.

---

### Post by pastabasta on 2011-04-10
For anyone interested in using evtouch driver, I got it working with the following procedure (I'm using amd64 version of ubuntu 10.10)

From a clean install of 10.10 amd 64, 

1) remove synaptics driver for mouse (I just did this in synaptics pacage manager, but make sure you don't uninstall synaptics package manager!)

2) Download egalax drivers from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

3) Install the egalax driver according to the instructions in the readme file UP TO the point where it asks you to restart the computer.

4)  Restart the computer, and instead of following the directions given by readme file in the directory where you downloaded egalax, open a terminal and type (without quotations)

"cd /usr/share/X11/xorg.conf.d"

If you type "ls" then you should see at least (I'm pretty sure this applies to all ep121's)

10-evdev.conf   50-evtouch.conf  50-wacom.conf
50-egalax.conf  

Open up 50-egalax.conf, i.e. "sudo gedit 50-egalax.conf"  (or whatever your favorite text editor is)

I modified mine to look like this:

Section "InputClass"
    Identifier "eGalax touch class"
    MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
    MatchDevicePath "/dev/input/event*"
    Driver "evtouch"
    Option "MinX" "0"
    Option "MinY" "0"
    Option "MaxX" "32768"
    Option "MaxY" "32768"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
   #Option      "TapTimer"  "0"
   Option      "LongTouchTimer"  "350"
   Option      "ReportingMode"   "Raw"
#  Option      "Emulate3Buttons"
#  Option      "Emulate3Timeout" "50"
   Option      "SendCoreEvents"  "On"
#  Option      "maybetapped_action" "click"
#  Option      "maybetapped_button" "3"
  Option      "longtouched_action" "down"
  Option      "longtouched_button" "1"
  Option      "oneandahalftap_action" "click"
  Option      "oneandahalftap_button" "3"
#  Option      "ButtonNumber" "4"
#  Option      "Calibrate" "1"
    #original parameters to use with the "void" driver
    #Option "Device" "usbauto"
    #Option "Parameters" "/var/lib/eeti.param"
    #Option "ScreenNo" "0"
    #Option "SkipClick" "0"
EndSection

#Section "InputClass"
#    Identifier "eGalax touch class"
#    MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc.|#eGalaxTouch Virtual Device"
#    MatchDevicePath "/dev/input/mouse*"
#    Driver "void"
#EndSection

#Section "InputClass"
#    Identifier "eGalax touch class"
#    MatchProduct "eGalax Inc.|Touchkit|eGalaxTouch Virtual Device"
#    MatchDevicePath "/dev/input/js*"
#    Driver "void"
#EndSection



Note that the install is originally looking for a void driver at this point.  

Under the section that starts 
Section "InputClass"
    Identifier "eGalax touch class"
    MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."

You will probably have "void" as the driver instead of "evtouch".  I think changing "void" to evtouch as I did just forces the device to use the evtouch driver.  I tried evdev driver, but it recognizes the screen as a touchpad, and I had problems using the solutions posted by others (I thikn b/c i'm using amd64)

Anyways, the minx min y maxx maxy parameters worked for my screen (and in principle, yours)  The other options are specific to how I like to set up my touch screen.  See [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html) for more details on setting up the driver.  I can post my Xorg.0.log if anyone wants.

---

### Post by buraitopengin on 2011-04-11
I'll try i out as soon as I receive the slate!! Tank you so much for your work!

By the way, have you tried utouch drivers from lunchpad?
[https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch)

Interested in your xorg log ;)

---

### Post by pastabasta on 2011-04-11
file:///home/paolo/Desktop/Xorg.0.log

i attached only parts where system adds devices to xinput

good luck.  let me know if you have questions

---

### Post by pastabasta on 2011-04-11
So, I tried utouch a little but, but from what I read one really needs the unity interface to use it well (there is something call jinn (...? i think) that allows one to use with gnome, but I didn't try it).  I'm going to wait until 11.04 to try for gesture support, unless someone thinks there's something worth trying.

So, today I've been working on the two buttons on top of the computer beside the power button.  In syslog, they register as follows:


Apr 11 21:46:55 paolo-slate kernel: [ 5553.957930] eeepc_wmi: Unknown key f7 pressed
Apr 11 21:46:55 paolo-slate kernel: [ 5553.960949] eeepc_wmi: Unknown key f3 pressed
Apr 11 21:46:55 paolo-slate kernel: [ 5554.866525] eeepc_wmi: Unknown key f7 pressed
Apr 11 21:46:55 paolo-slate kernel: [ 5554.869479] eeepc_wmi: Unknown key f3 pressed
Apr 11 21:48:37 paolo-slate kernel: [ 5656.106085] eeepc_wmi: Unknown key f7 pressed
Apr 11 21:48:37 paolo-slate kernel: [ 5656.108936] eeepc_wmi: Unknown key f3 pressed
Apr 11 21:48:39 paolo-slate kernel: [ 5657.896325] eeepc_wmi: Unknown key f3 pressed
Apr 11 21:49:33 paolo-slate kernel: [ 5711.774609] eeepc_wmi: Unknown key f3 pressed
Apr 11 21:49:35 paolo-slate kernel: [ 5714.295383] eeepc_wmi: Unknown key f3 pressed

(this is for the push button with the keyboard symbol by it.  the slide button that locks (not the power button) registers as combinations of f7 and f5.  I'm thinking the f7 is some idle state (?) and f3 / f5 is where the computer registers the button event (I don't know anything about computers, sorry for the mangled interpretation).  

Anyways, what is wmi and how to I attach a script to these events?  I'd like to have one button rotate the screen, and the other bring up onboard.

Also, does anyone know where events associated with the accelerometer appear?  are they acpi events?  I'd like to enable that feature as well.

Thanks!

~Paolo

---

### Post by buraitopengin on 2011-04-12
I saw some accelerometer interaction on this thread or in some other thread related to the slate, you sould check them out.

I think Unity is well designed for slate's hardware, you might give it a try someday. Multitouch integration is very tricky on linux, hope developpers will make improvements to support a larger scale of hardware.

I'm not a "real" developper, I made my way straight to PHP, I can't take a single line of low-level programming language, that's a shame :) So I won't be a great coding partner but I can deal with drivers and pray to get something work the way it should xD

In 10 days or so, I'll be able mess around with packages and sources codes.

Let's make it happend!

EDIT!

I found some guy's post on the Internet regarding multitouch, and he's working on supporting more than one finger using the evdev driver : 
[http://blogs.gnome.org/carlosg/2010/06/09/getting-multitouch-to-just-work/](http://blogs.gnome.org/carlosg/2010/06/09/getting-multitouch-to-just-work/)

You should check this out and report if it work ;)

---

### Post by pastabasta on 2011-04-24
buraito

did you receive your slate yet?

The accelerometer is definitely acpi.  Found that on a Windows forum.  The signal is not detected directly by any of the common tools like "acpitool", so forth

I can't find any devices associated with the accelerometer in /proc/acpi/    ... but the signal must be there.  Is there an easy way to access the contents of "/proc/acpi/event"?

That file contains information on all acpi events, and i'm pretty sure something will be logged there from the accelerometer.  From there it should be easy to make a fix so that the screen rotates automatically.

The file is busy because it is being read by acpid.  I tried killing apcid with "kill #", where the # was the process number associated with acpid, but no luck.  it keeps respawning.  

I read something about the same information (and more) being ... sent to (?) ... netlink?  Couldn't make heads or tails of it.  any suggestions?

---

### Post by buraitopengin on 2011-04-30
> **pastabasta said:**
> did you receive your slate yet?

I didn't receive the slate yet, I should receive it the 11th of March.
Anyway, if I manage to get everything to work, I will post an article on this forum ;)

---

### Post by computerwiz_222 on 2011-05-01
Can anyone provide an update on how Ubuntu 11.04 works with this hardware?

I am seriously considering dropping my Android tablet for the EP121 running Ubuntu.

---

### Post by pastabasta on 2011-05-10
wiz_222

Check out the following link

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/156093](https://answers.launchpad.net/ubuntu/+source/xorg/+question/156093)

It looks like a bug report has been filed for 11.04, and the touch screen doesn't work.

---

### Post by Victormd on 2011-05-11
> **computerwiz_222 said:**
> Can anyone provide an update on how Ubuntu 11.04 works with this hardware?

I am seriously considering dropping my Android tablet for the EP121 running Ubuntu.

I haven't been able to get ubuntu running smoothly on the slate, seems like the touch drivers are flaky at best and there's still a lot of work to be done.

---

### Post by pastabasta on 2011-05-11
Yeah, sounds like 10.10 is one of the better options for now.  

Another piece of the puzzle for anyone running the 64 bit version.  To get the mic working, follow this link.

[http://ubuntuforums.org/showpost.php?p=9486962&postcount=62](http://ubuntuforums.org/showpost.php?p=9486962&postcount=62)

You'll have to adjust the "capture" in alsamixer (I had to set mine to essentially zero, but the mic works alright after that.

---

### Post by buraitopengin on 2011-05-14
I just received the slate today, it's a great piece of hardware if you ask me ^^ Honorable performances ; playing hd videos, coding using JAVA IDE, painting with Artrage, tipping with words, everything work as expected.

Regarding Ubuntu i tried 11.04 : bluetooth & multitouch are not supported at all.PPa's found on the Internet doesn't fix the problem.

I'll try Ubuntu 10.10 with the latests ppa's from utouch...
Then I'll mess with the terminal ^^

---

### Post by Victormd on 2011-05-15
buraitopengin, I thought bluetooth on 10.10 was easy to get working - touchscreen is a different story. good luck and keep us posted.

---

### Post by buraitopengin on 2011-05-15
> **Victormd said:**
> buraitopengin, I thought bluetooth on 10.10 was easy to get working - touchscreen is a different story. good luck and keep us posted.

Bluetooth worked for me out of the box, but after an update, it went down. Sad story T_T By default the touchscreen can only drag the cursor around, utouch drivers wont help at all, but i guess i have to  make some changes in grub...

---

### Post by tsoral on 2011-05-16
> **buraitopengin said:**
> Bluetooth worked for me out of the box, but after an update, it went down. Sad story T_T By default the touchscreen can only drag the cursor around, utouch drivers wont help at all, but i guess i have to  make some changes in grub...

I had the same problem, and it was very frustrating... until I figured it out.
I kept windows 7 and used wubi to install ubuntu (I tried both 10.10 and 11.04). After the installation, bluetooth worked out of the box, as well as after some reboot. But when I shut down my EP121 and started it again, bluetooth was not working anymore.

So I guessed that it was not a software problem (updates on bluez did not work) but a hardware problem (ubuntu could not activate the bluetooth device, it was windows that activated it and was never shut down during the reboot)

If you think this is your case too, try this:
   on 11.04, install the package linux-headers-lbm-2.6.38-9-generic
   otherwise look for a linux-backport-modules package.

then reboot. If its not working, then go to the Linux Wireless webpage:
  [http://wireless.kernel.org](http://wireless.kernel.org)
  Download the last version of compat-wireless
  extract it
  run ./script/driver-select ath3k (the driver for the bluetooth device)
  make bt
  sudo make btinstall
  sudo reboot

After that, it should be working on both 11.04 and 10.10.

---

### Post by buraitopengin on 2011-05-17
Nice one Tsoral!
I'll give it a try

Now, we really have to focus on the dualtouch interface.
Wubi helped me a lot as well, i can't even image to do a clean install each time i receive a kernel panic (I mess really hard with grub'n'stuff and i don't make backup files quite often xD)

First step is to blacklist the touchpad, it seems that the driver create conflicts with eGalax drivers.

---

### Post by CSkau on 2011-05-20
Hi,

I been fighting Ubuntu for a while since getting my EP121, and couldn't quite accept the fact that I had to run 10.10 to make it work just partially.

So, after looking a bit into *why* it works on one and not the other I came up with a couple of leads.

Now, the short story is that I've managed to actually get most things working now, and have been happily running Natty for the past week or so.

I hacked up a "driver" myself and fixed a couple of minor things. The result is available here:
[https://github.com/cskau/EP121-fixes-for-Ubuntu-11.04-Natty]("https://github.com/cskau/EP121-fixes-for-Ubuntu-11.04-Natty")

For the eager ones you can go ahead and download the install script (ep121.sh) or alternatively download all the files at once and do it semi manually.

What this collection of scripts is supposed to do is essentially two things: 1) modify and add the necessary settings, 2) act as a makeshift driver for touch input.

**ep121.sh** is the install script which is supposed to do the following:
- Disable evdev for the touch screen.
- Remove buggy bluez 4.91 and replace it with bluez 4.60
- Download the "driver"
- Make sure the driver can read the input/event files
- Set up the driver for login execution

**ep121_drv.py** is the so called "driver" - a quickly hacked together Python script to interpret the input events and send them on to X.
There are still a bunch of things that need fine tuning by the following things work (somewhat) at the moment:
- Single click
- Two-finger right clicking (like on Windows)
- Two-finger scrolling
The last one is by far the most buggy of the above.
However, it should be fairly easy to modify the script to tune and even add new gestures and what have you.

Further more I decided to add a small snippet to interpret events from the hotkeys on the machine as well.
This means that the driver also supplies the following functionality:
- Screen button: Toggle touch input (mighty handy for when you're using the pen)
- Flip switch: Toggles left flip of display and input (Pen and Touch)
I was also considering binding the Keyboard button to toggle Onboard (the on-screen keyboard), but I couldn't find a handy way of making that happen at the time.

Hmm.. did I forget something ? .. Oh well.

EDIT: Now I know what I forgot - the disclaimer:
DISCLAIMER: I did *NOT* test this script on it's entirety, I simply hacked it together after fixing all these small thing manually by trial and error myself. I most certainly forgot something in there, so proceed with care, and report back with you own experience.

Now, go ahead and download these scripts and finally start taking advantage of your device's full potential ! ;)

Also, feel free to fork me on GitHub, and show me what you can make my little script do.

Cheers

---

### Post by Victormd on 2011-05-21
thanks for this, gonna give it a try asap!

---

### Post by buraitopengin on 2011-05-21
> **CSkau said:**
> Hi, I been fighting Ubuntu for a while [...]

Oh My God! That's fantastic! I've been trying for a while to get things working using a very basic Debian distribution and some drivers here and there...

You have all my gratitude!

Even if I am no longer a huge fan of Ubuntu+Unity (lack of usability for a developper), I'll sure give it a try ASAP. The Slate is for entertainment purpose and drawing, my desktop have a custom debian with AWM (awesome window manager, vim, etc... Pretty hardcore if you ask me xD).

Thanks again!

---

### Post by buraitopengin on 2011-05-21
Sorry for double posting but I really want to make a separate post for feeback purpose ;)

So dear CSkau,

I tried your amazing script and in most part, it worked for me ;)
Behold! Here's my feedback :

I made a nice and clean Install of Ubuntu Natty using Wubi installer for Windows.
First things that blew my mind : Bluetooth worked out of the box oO' so I commented out the bluez driver replacement in your shell script before running it.
So, Bluez 4.91 work for our sweet EeeSlate, that's good news.

I managed to pair 3 bluetooth devices :
The keyboard
A Mouse
An audio headset with a2dp profile

When pairing the headset, i got some issues with the mouse been too slow moving around the screen but i although spotted this problem under Windows7, it's seems that bluetooth audio devices are consuming a lot of bandwidth.

So after that, I unpacked the archive on my Desktop (lazy way)
sudowed right into it (sudo sh /home/buraitopengin/Desktop/cskau-EP121-fixes-for-Ubuntu-11.04-Natty-1d83ab4/ep121.sh) answered "Yes" every time the terminal prompted for user input and rebooted the device.

Back on Ubuntu, I tried to touch the screen nothing happened. Reading your post, i learned that you've mapped the hardware buttons so I tried to press the main one and i gave it another try... Nothing...

Seems that your
<code>echo "ep121_drv.py &" >> ~/.profile</code>
won't load the python script at startup

Running ep121_drv.py in the terminal make everything work **a lot** better!


--------------------------------------

And now for the questions ;3

How did you manage to map the slate special buttons?
How can I be sure that the driver is implementing dual-touch?
Do you know any virtual keyboard that support more that one finger input?


-------------------------------------- 

And thanks a lot for your work m-_-m

---

### Post by CSkau on 2011-05-23
Great to hear it :)

I should start out by making a few notes on Bluetooth.
I honestly don't know too certainly what exactly is wrong with Bluetooth as its behaving rather random. Even with bluez 4.60.

My initial guess was that the kernel lacks drivers for the internal, on-board Bluetooth receiver, and on top of that that there is a bug in bluez, effectively crippling remaining devices.
On my own machine I'm actually using a USB Bluetooth dongle to make it work.
However, this dongle only seems to work with bluez 4.60, while neither receiver works with 4.91.

But the fact that you are now reporting the on-board receiver working with 4.91, cast some serious doubt on that theory :)


Also, with my own setup I've simply put that one-liner into the '~/.profile' file to make it load at login.
However, there are a few exceptions to this usage. For one there exists several other files like '~/.profile' that will prevent it from loading. So if you have any of those files in your home dir, then they will have to be used instead.

I'll try expand the "install script" to take these exceptions into account.


As stated earlier the "driver" basically just reads and interpret the events through the '/dev/input/event..' interface (see 'ep121_drv.py' for details).
So getting the hotkey input is simply a matter of reading their events, and responding on them.

And finally you can test if 'ep121_drv.py' lets you do dual-touch by holding one finger on the screen, and then clicking with the other. This should trigger a right click.
Also holding two fingers on the screen and dragging them vertically swiftly, should trigger scrolling events.

EDIT: Update..
I've added a couple of lines to the install script now, so it should function better now.
I forgot to copy over the XAut lib that is needed, plus making the script executable. My bad.
Thanks and please keep the feedback coming :)

---

### Post by buraitopengin on 2011-06-02
Hi there, it's been a while since i logged in!
The reason is, my EP121 went down! I got that fans issue, they were operating at full blast quite frequently. So I decided to downgrade the bios to 401 to see if it fix the cooling policy but guess what? It won't start anymore...

So, i send it back to the reseller to get a new one ^^
I guess the slate came from a bad series, better luck next time.

I'll track your github repository as soon as I can ;)

---

### Post by buraitopengin on 2011-06-11
I just got my slate back!
No more fans issues, that's a relief!

I'll try yournew script this afternoon, thanks again for your work.

---

### Post by pirohmaniac on 2011-06-24
So I finally got mine! Battery had never even been charged yet, took about 30 minutes before it went above 0. 
First, for all those who are sticking with windows until ubuntu works right, check out rt7lite.com
It lets you add or remove stuff from the windows 7 install. AFAIK home premium 64bit can be cut down to around 7gigs installed. I'll be trying it with my acer restore disks tomorrow.

I downloaded the android-x86 for asus laptops/tablets live cd and it worked right away. As soon as the gui starts the "TSLIB calibration utility" starts. 5 touches later and the touchscreen works fine with single touch. I'm not good enough with linux yet to find out how it works. :( Unless I just have to install the tslib stuff and use it.

The eGalax driver posted earlier sees no xorg.conf and rolls back any changes it made. I'll have to make one and see what it does.

I tried the script CSkau made too. The ep121_drv.py does make the touchscreen work when it's run from the terminal, but putting it in rc.local doesn't make it start so I'm stuck there too.

Thats about as far as I've managed to figure out. I've got a couple more things to try and I'll post results tomorrow.

edit:
Forgot to mention, I think our bluetooth problem might be module  related. I dont remember anyone mentioning that it's bluetooth 3.0 if  that matters. On the bottom edge of my tablet in small letters is "IEEE  802.11 b/g/n + 802.15 BT combo card: NB037" Under that even smaller is  "AR5B195".

Anyway I found a bunch of stuff on google but haven't tried anything yet.

---

### Post by pirohmaniac on 2011-06-24
okay, this used to be a post about bluetooth but it ended up on a new page meaning my first post would have gone unnoticed.

SO READ THE POST BEFORE THIS!

---

### Post by nikitis on 2011-06-24
> **CSkau said:**
> Hi,

I been fighting Ubuntu for a while since getting my EP121, and couldn't quite accept the fact that I had to run 10.10 to make it work just partially.

So, after looking a bit into *why* it works on one and not the other I came up with a couple of leads.

Now, the short story is that I've managed to actually get most things working now, and have been happily running Natty for the past week or so.

I hacked up a "driver" myself and fixed a couple of minor things. The result is available here:
[https://github.com/cskau/EP121-fixes-for-Ubuntu-11.04-Natty]("https://github.com/cskau/EP121-fixes-for-Ubuntu-11.04-Natty")

For the eager ones you can go ahead and download the install script (ep121.sh) or alternatively download all the files at once and do it semi manually.

What this collection of scripts is supposed to do is essentially two things: 1) modify and add the necessary settings, 2) act as a makeshift driver for touch input.

**ep121.sh** is the install script which is supposed to do the following:
- Disable evdev for the touch screen.
- Remove buggy bluez 4.91 and replace it with bluez 4.60
- Download the "driver"
- Make sure the driver can read the input/event files
- Set up the driver for login execution

**ep121_drv.py** is the so called "driver" - a quickly hacked together Python script to interpret the input events and send them on to X.
There are still a bunch of things that need fine tuning by the following things work (somewhat) at the moment:
- Single click
- Two-finger right clicking (like on Windows)
- Two-finger scrolling
The last one is by far the most buggy of the above.
However, it should be fairly easy to modify the script to tune and even add new gestures and what have you.

Further more I decided to add a small snippet to interpret events from the hotkeys on the machine as well.
This means that the driver also supplies the following functionality:
- Screen button: Toggle touch input (mighty handy for when you're using the pen)
- Flip switch: Toggles left flip of display and input (Pen and Touch)
I was also considering binding the Keyboard button to toggle Onboard (the on-screen keyboard), but I couldn't find a handy way of making that happen at the time.

Hmm.. did I forget something ? .. Oh well.

EDIT: Now I know what I forgot - the disclaimer:
DISCLAIMER: I did *NOT* test this script on it's entirety, I simply hacked it together after fixing all these small thing manually by trial and error myself. I most certainly forgot something in there, so proceed with care, and report back with you own experience.

Now, go ahead and download these scripts and finally start taking advantage of your device's full potential ! ;)

Also, feel free to fork me on GitHub, and show me what you can make my little script do.

Cheers


I've been working with cskau and have modified his script.  Not to take away credit from his amazing driver that just works, but to add to it. 

I've added to the install script a pre-login onscreen keyboard so that you won't even need a keyboard or stylus to login to ubuntu.  You can use touchscreen only if you wish.  It will ask you which onscreen keyboard you wish to use. 

Florence - A nice clean very responsive keyboard.
or
Onboard - A reliable not as responsive keyboard, but nice once you learn how to use it correctly.

The install script before was not able to enable touch screen for logging in purposes, but now it does.

Another feature i've added was a ep121-stealth.sh script which accomplishes the same thing as cksau's but hides the driver in a ~/.bin/ folder for those who do not wish to install their drivers in a non-hidden folder ~/bin making it visible in your home directory.  Run either script, but NOT both.

ep121.sh - installs to ~/bin/ep121/  
ep121-stealth.sh installs to ~/.bin/ep121/

I've forked the project in hopes cskau will add it to his master branch.  But for now you can grab them at:
[https://github.com/nikitis/EP121-fixes-for-Ubuntu-11.04-Natty/](https://github.com/nikitis/EP121-fixes-for-Ubuntu-11.04-Natty/)

or clone it at:

Make sure you have git installed:
sudo apt-get install git-core

then

git clone git://github.com/nikitis/EP121-fixes-for-Ubuntu-11.04-Natty.git 

These haven't been fully tested.  So please if you find any bugs, post the contents of your terminal.

Thanks and enjoy!

PS. Bluetooth still doesn't quite work right for me even with 4.60 bluez.  It's a driver thing i'm sure of it so if you wish to install 4.60 you can or just ignore it.



Also more features to come:

Adding keyboard enabling via 2nd top key on Asus EP121 like in windows.  

Possible orientation drivers.

---

### Post by slef on 2011-06-28
Thanks CSkau and nikitis for this great script/driver.
Here are a few notes from my installation (I had to repeat the process a few times to make this work):

I installed 11.04 from wubi, 
- Bluetooth worked fine out of the box, however if I let the script "fix" it, it stops working.
- before running the script, I had to pay attention not to touch the screen with my fingers otherwise the focus of windows would get messed up.
- I tried the fork from nikitis first but I ran into some problems: the script tries to install files in the ~/bin/ep121/ dir which doesn't exist. Creating the dir allowed the script to run without errors, however the path stored in .profile does not correspond to /bin/ep121. It is nice to have onboard in the login screen, however notice there is an option in the lower right button of the login screen (universal access) to do the same.
- I resorted to used the original CSkau script. I guess I will use the stylus to login for now. I had to create the ~/bin directory (it would be nice if the script would check that and create it) and then most things worked (screen button to toggle pen etc). However, screen rotation rotates the screen and pen, but only the lower half of the screen, the dock and the menu bar work, the upper half of the screen are black. Is anyone having the same problem?
also the rotation acts bizarrely if the swich is in "unlocked" position at login.

About bluetooth, I noticed a strange thing: bt in ubuntu seems to only be working if it works first in windows: In the last installation, I installed ubuntu with wubi without pairing the keyboard, and ubuntu wouldn't let me add a device. So I swiched back to Windows, paired the keyboard, swithed back to ubuntu and then I could pair the keyboard again. I don't know if this is repeatable.

S.

---

### Post by pirohmaniac on 2011-07-01
So much for posting tomorrow. Long story short, everything I tried failed, including CSkau and nikitis scripts. I forgot to post my console but hopefullty I have some free time tomorrow.

Still using Windows. Still hate Windows. There's only one thing I like about it. Know what that is? All our customers use it! A week ago we got a 911 call from one of our customers because a bunch of computers weren't working. Some dumbass was using his work computer to visit porn sites (most of the others did the facebook thing), got some malware and it infected the rest of the computers in the sector. Go Windows, right.

Also something a little odd...
Went to Asus 2-3 days ago to see the downloads for our tablet. Android was listed where you choose the OS. They offered the bios updates and the manual. Sent an email through their support section asking if they planned on supporting linux too basically. Went to the downloads page again today and Android is gone from the list.

---

### Post by slef on 2011-07-04
Ok so after  while my Bluetooth broke down again. Here is how I make it work again:
- Boot into Windows, pair the keyboard (remove old pairing if existed)
- reboot into ubuntu, pair the keyboard (remove old pairing if existed)
Now bluetooth works properly until the computer is shut down or put to sleep. For some reason just a reboot is fine. It seems like the bluetooth just needs to be woken up somehow.

Another tip: I got the eraser to act as a right click by typing:
% xinput set-button-map "Wacom ISDv4 90 Pen eraser" 3
in the terminal. I am looking for the proper file to put this in now. It needs to be run after every login, reboot, wake up from sleep etc. I think there should be an equivalent setting in xorg.config but I haven't looked into that yet. Suggestions are welcome.

The half-black screen after rotation was a known but of Unity. The fix was to
% sudo apt-get install unity
to get the latest version.
I swiched to the calssic environment anyway. It plays better with onboard anyway and I find it easier to use for now.

I still need to figure out how to calibrate the pen. It is a few pixels off. Ideas?

S.

---

### Post by pirohmaniac on 2011-07-06
So  the thing piled up on me. Quit while l was watching a movie. Took it back to bestbuy and got another one. Dad wont let me run linux on it until "they figure it out" as he puts it. So 11.10 probably.
Still to show my support, and that I will be running it as soon as I can...
Damn. Picture didn't work. Ive got a "Powered by Ubuntu" sticker right in the middle under the exhaust.
[IMG]https://sites.google.com/site/pirohmaniacwebstuff/home/DSC_0007.jpg?attredirects=0[/IMG]

---

### Post by cheshirekow on 2011-07-13
Hi all, I was thinking of picking up an EP121 and stumbled across your thread. It sounds like everyone is trying to use the evtouch driver for the egalax, has anyone tried evdev instead? It should come with 11.04, but you may need to configure x a bit to get the driver to load. From a bit of reading, it sounds like it should support the hardware.

Also, any news on the bluetooth issue? Does anyone know what the hardware model number is? Is it an atheros?

Lastly, what's the graphics chip? Is it a GMA?

---

### Post by pirohmaniac on 2011-07-13
> **cheshirekow said:**
> Hi all, I was thinking of picking up an EP121 and stumbled across your thread. It sounds like everyone is trying to use the evtouch driver for the egalax, has anyone tried evdev instead? It should come with 11.04, but you may need to configure x a bit to get the driver to load. From a bit of reading, it sounds like it should support the hardware.

Also, any news on the bluetooth issue? Does anyone know what the hardware model number is? Is it an atheros?

Lastly, what's the graphics chip? Is it a GMA?

according to the multitouch devs, evdev is what we're supposed to use now but I tried almost every tutorial I could find and couldn't get it working. time to try again soon. the biggest problem is that it sees the touchscreen as a touchpad, if i find out how to change that i might be okay.

AR5B195 is the model number. its a wifi b/g/n bluetooth combo card. i googled and got some results but i never bothered with it.

The graphics is simply called Intel HD Graphics. as i understand it it's built in to the i5. It's not very powerful. Can barely play morrowind. That's mostly Windows fault, them and their directX crap. I know for sure that after a slow startup, Blender runs very nicely on Windows so It should run like a race car in Ubuntu.

also Windows 7 only has 2 finger touch. Ubuntu plans on at least four for utouch capabilities. asus claims 10 fingers in an article i read but others say only 2. may be a firmware thing, who knows?

---

### Post by pirohmaniac on 2011-07-17
So after the latest updates and some tweaking, it's working better. It almost follows my finger but when I touch it, it stops registering mouse clicks even with a USB mouse.
I might post settings later.

---

### Post by pirohmaniac on 2011-07-20
So I'm stuck going from memory. Had Ubuntu installed under Wubi. Where did it go? No idea. More Magic Windows Bullcrap.
Anyway,  I followed the instrictions here  ```
http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html
```  but adapting it for our tablet. I also had to remove the Synaptics Xorg  files to stop the touchscreen from loading as a Synaptics touchpad, and  comment the touchpad part of 10-evdev.conf. Tough to remember but not  important.

I tried the daily build of oneiric yesterday and  they've fixed the issue where there is a constant scroll up when you  touch so you can touch it now but it still acts like a giant touchpad.  Commenting the touchpad part makes it work with absolute coords but  touching the screen breaksclicking until I restart.

It's getting there! :grin:

---

### Post by deadland on 2011-10-02
Hi there, I am using Oneiric. Could you, pirohmaniac, or someone else provide me working evdev rules to get this [-o< touchscreen [-o< working.

There is already a Bug Report, it would be great if all of you could vote for this Bug by logging into the Launchpad an press "This bug affects you".

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445)

Thanks

---

### Post by deadland on 2011-10-15
Hi there, it is working :D (Ubuntu 11.10 64 bit)

You have to ask the EETI-Support (touch_fae at eeti.com) for a special driver (Asus EP121; ubuntu 11.10 64bit). They will send you a archive called "eGTouch_v1.00.0812.L-x64.tar.gz" (Note: the driver provided on the driver page of EETI is not working properly ).

You just have to run the setup.sh as sudo and add to the "52-egalax-virtual.conf" file the option InvertY, that it looks like this:

> Section "InputClass"
	Identifier "eGalax virtual class"
	MatchProduct "eGalaxTouch Virtual Device"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	**[COLOR="Red"]Option "InvertY" "true"[/COLOR]**
EndSection

And finally reboot you system.

Observations:
1.) I asked the EETI Support if I could share their drive in the ubuntu forum, they said "NO" it is a project (I do not understand what this means, but anyway, please do not upload the driver)
2.) Multi-touch does not work, they told me "If you want to have multi-touch function, the user-space (application) must be able to receive our multi report data from our controller." Well, I also do not understand what this means ...

What does not work:
1.) As i mentioned already, Multitouch does not work
2.) Microphone
3.) Specialkeys "show on-screen keyboard" etc.
4.) Accelerometer

Bye

---

### Post by slef on 2011-10-17
Thanks Deadland! That's good news. I have a few questions:
Does the bluetooth work better in 11.10? if not, what is the advantage of running 11.10 rather than 11.04?
Can you still run the CSkau script or a variant to get the buttons (mainly the rotate switch and home button) working?

I emailed EETI-support as you suggested but got the following answer:

> Dear Sir,
 
Please download EETI driver from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
 
Thanks,
Best Regards,
Derrick Lai


And the driver on that page is from august. Definitely not the one you mentioned. Is there any magic word you used get the real thing?

Cheers,
Stefan.

---

### Post by deadland on 2011-10-17
> Does the bluetooth work better in 11.10?

Sorry, I can't answer you this question, since I do not use bluetooth.

> if not, what is the advantage of running 11.10 rather than 11.04?

Well, thats a difficult question. I guess unity is more matured in 11.10 as in 11.04 :cool:. But I actually switched directly from Lucid to 11.10 ... so I am not the most indicated person to answer you this question... 

> Can you still run the CSkau script or a variant to get the buttons (mainly the rotate switch and home button) working?

I did not try it on 11.10 ...

> Is there any magic word you used get the real thing?

Well, I do not think so ... I wrote:

[INDENT]*it would be greate, if you could provide a comprehensive guide how to install your driver correctly on ubuntu with a linux 3.0 64bit kernel. I Also would like to public your advices on the ubuntuforums.org because there are a few people who cannot compile your driver. I do have a Asus Slate EP121.*[/INDENT]

Perhaps it helps to mention directly the file name "eGTouch_v1.00.0812.L-x64.tar.gz". If it doesn't help, I would send you via PN the Email-adress of the EETI-person, who addended me.

Best regards

---

### Post by samakkon on 2011-10-19
I got also the eGalax driver from the support for 11.10 (32bit). However the Option "InvertY" didn't seem to work for me. I modified the /etc/eGTouchd.ini with:

Direction 2

and that fixed the Y coordinate problem.

BT seems to be working, at least Magic Trackpad works.

---

### Post by pirohmaniac on 2011-10-20
I got v1.01.0825.L. Had to edit the eGTouchd.ini too. Seems this version has multitouch or partial multitouch anyway. There's interesting mention of it inside the files...
ReportPoint 5  [COLOR=DarkRed]Why would it report on 5 points? :D[/COLOR]
MultiTouchEnable 1

[NOTE]
ReportPoint [0]Disable, [1] Single-touch, [>=2] multi-touch  
MultiTouchEnable [0] Disable, [1] Enable MultiTouch report _which can report uTouch Gesture_ [COLOR=DarkRed]Yay! Or it will be if I can get it working.[/COLOR]

---

### Post by deadland on 2011-10-25
I just would like to mention, that Bluetooth doesn’t work reliable (for me) on Oneiric.

---

### Post by pirohmaniac on 2011-10-25
> **deadland said:**
> I just would like to mention, that Bluetooth doesn’t work reliable (for me) on Oneiric.
Reliable or at all?

---

### Post by deadland on 2011-10-25
Well sometimes it works and sometime it doesn't at all ... So it is not predictable if it works or not, hope that’s clearer.

---

### Post by buraitopengin on 2011-10-26
For those how have troubles running bluetooth on the Asus slate just do the following :
```

sudo aptitude install ar3011-dkms
sudo /usr/sbin/service bluetooth restart

```

It install the atheros driver and restart the bluetooth service.
Simple isn't it? ;)

Still no reliable support for multitouch on the Slate i'm afraid T___T

---

### Post by buraitopengin on 2011-10-26
> **deadland said:**
> Well sometimes it works and sometime it doesn't at all ... So it is not predictable if it works or not, hope that&#8217;s clearer.

This is when you boot on Windows and then on Ubuntu.
Here's my theory : Windows first activate the  bluetooth device and when you restart the slate on ubuntu the device still active so it can be used on Ubuntu. I used to do that trick quite a lot to make it work XD But when the device is turned off, when you try to boot in Ubuntu the bluetooth won't work at all.

---

### Post by Favux on 2011-10-28
Hi all,

It looks like over on linuxwacom-devel they have figured out how to get the touchscreen running on evdev without the "forcing" hack in post #9.  This was on the 3.1 kernel but it should apply to at least a few previous kernel versions.  See:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_ag7KWkF4uDa7rd3rrtq75B4bwkn7vA26YAsS2EEJebag%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_ag7KWkF4uDa7rd3rrtq75B4bwkn7vA26YAsS2EEJebag%40mail.gmail.com&forum_name=linuxwacom-devel)

You have to make minor modifications to the following files (basically whitelist and blacklist) before compiling the module(s)/kernel. To summarize (I think):
> **Chris]The reason its using this driver is because, like I mentioned earlier,
your device has to be white listed to be used by a non-generic driver.

To start with, someone will need to add your new product ID of 0xa001
to this file:

[url]http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git said:**
> 

It needs to be added around line 234.  Then it needs to be add to
white list in the hid-multitouch.c file:

[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=blob;f=drivers/hid/hid-multitouch.c;h=fa5d7a1ffa9e97e81a8785a5d96c4f1af59cd47d;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=blob;f=drivers/hid/hid-multitouch.c;h=fa5d7a1ffa9e97e81a8785a5d96c4f1af59cd47d;hb=HEAD)

Look around line 682 for example of registering a resistive eGalax
touch screen and around line 690 for registering a capacitive.

This all assumes that eGalax has chosen to be a HID Multitouch
compliant device for this model... probably they did.

> **Chris]OK, found out what I missed.  When you have a driver that is
auto-grabbed by generic-usb then you need to add it to a generic-usb
blacklist in addition to adding it to hid-multitouch's whitelist.

[url]http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git said:**
> 

See around line 1407 where its blacklisting other eGalax touchscreens.
 Add a line for yours.

Hopefully I got the correct bits.

Anyway, once touch is on evdev you should be able to use ginn for multi-touch, see the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492").  N-trigs also have touch on evdev and the stylus on Wacom.

I'm not going to try to figure out how to do the compile but Appendix 1 on the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") should give some hints.


Edit:  Interestingly Chris added that you could use the current xf86-input-wacom for gestures in lieu of evdev + ginn.  Due to his ongoing work on gestures for xf86-input-wacom.

---

### Post by pirohmaniac on 2011-10-29
Looks like I'm going to have to learn how to compile. Maybe. Eventually. This is definatley a motivator.

---

### Post by az_s_za on 2011-10-31
I'm thinking about getting an EP121, but all this sounds way too hard.

Do any of you have Ubuntu running inside VirtualBox (or similar) in Windows 7?
Does that not work well enough?

---

### Post by pirohmaniac on 2011-10-31
> **az_s_za said:**
> I'm thinking about getting an EP121, but all this sounds way too hard.

Do any of you have Ubuntu running inside VirtualBox (or similar) in Windows 7?
Does that not work well enough?

Windows 7 is major bloated, and I read Windows 8 is supposed to be even more so. I don't think you'll leave yourself much space with Virtualbox. It would work but I'd rather get it up and running in Ubuntu at least I think it would work. I tried setting up an Android development environment not too long ago and the Android emulator was sloooooow.
Go Windows...
That was supposed to be sarcastic.

---

### Post by buraitopengin on 2011-11-03
> **deadland said:**
> Hi there, it is working :D (Ubuntu 11.10 64 bit)

You have to ask the EETI-Support (touch_fae at eeti.com) for a special driver (Asus EP121; ubuntu 11.10 64bit). They will send you a archive called "eGTouch_v1.00.0812.L-x64.tar.gz" (Note: the driver provided on the driver page of EETI is not working properly ).

You just have to run the setup.sh as sudo and add to the "52-egalax-virtual.conf" file the option InvertY, that it looks like this:



And finally reboot you system.

Observations:
1.) I asked the EETI Support if I could share their drive in the ubuntu forum, they said "NO" it is a project (I do not understand what this means, but anyway, please do not upload the driver)
2.) Multi-touch does not work, they told me "If you want to have multi-touch function, the user-space (application) must be able to receive our multi report data from our controller." Well, I also do not understand what this means ...

What does not work:
1.) As i mentioned already, Multitouch does not work
2.) Microphone
3.) Specialkeys "show on-screen keyboard" etc.
4.) Accelerometer

Bye

I just tested the driver and i must say that it work pretty well!
Just one little correction : To get the Y axis right, just open the following file with administrator right :
```
sudo nano /etc/eGTouchd.ini
```
At line #8 change 0 to 2 to reverse the Y axis, you should have
```

[eGTouchd.ini] 
DebugEnableBits            0 
ShowDebugPosition        0 
RS232Baudrate             0         
MouseMode            0 
ReportPoint            5 
MultiTouchEnable        1 
Direction            2         
Orientation            0
[...]

```

Regarding multitouch, the driver seems to implement the uTouch API, I should give it a try someday, but for now on, simple touch is more than OK.

---

### Post by deadland on 2011-11-03
I know I am making a fool of my self right now, but it would be great if **we** could solve the outstanding problems. 
[B]
1.) Bluetooth[/B]

It works if I turn bluetooth "on" (via the bluetooth icon at the upper right corner) and restart the bluetooth service in a terminal.

```
sudo /etc/init.d/bluetooth restart
```

also I found a tip to connect the bluetooth keyboard before logging  in:

> After you install, login and setup your bluetooth keyboard. Once you have it paired, add a similar line to /etc/default/bluetooth: (Substitute your keyboard MAC) 

HIDD_OPTIONS="-connect 7C:ED:8D:XX:XX:XX -master -server" 

This will allow the bluetooth keyboard to be always connected. (It will sleep now & then. I believe it is configurable.)

Credits to AbeOwitz

**2.) Specialkeys**

No idea...
[B]
3.) Microphone[/B]

No idea...

---

### Post by abeowitz on 2011-11-05
The special keys are handled by the eeepc-wmi kernel module.

Unfortunately the additional keys are relatively new and unmapped. If you really want to use them, you'll have to recompile the eeepc-wmi kernel module.

(I'm not using Ubuntu these days, switched back to Gentoo due to Unity, but there should be some docs around on how to do this.  i.e. download kernel source, edit and rebuild/replace module.)

Edit /usr/src/linux/drivers/platform/x86/eeepc-wmi.c and add three (0xf3,0xf5,0xf6) new codes to the keymap structure:

static const struct key_entry eeepc_wmi_keymap[] = {
/* Sleep already handled via generic ACPI code */
{ KE_KEY, 0x30, { KEY_VOLUMEUP } },
{ KE_KEY, 0x31, { KEY_VOLUMEDOWN } },
{ KE_KEY, 0x32, { KEY_MUTE } },
{ KE_KEY, 0x5c, { KEY_F15 } }, /* Power Gear key */
{ KE_KEY, 0x5d, { KEY_WLAN } },
{ KE_KEY, 0x6b, { KEY_TOUCHPAD_TOGGLE } }, /* Toggle Touchpad */
{ KE_KEY, 0x82, { KEY_CAMERA } },
{ KE_KEY, 0x83, { KEY_CAMERA_ZOOMIN } },
{ KE_KEY, 0x88, { KEY_WLAN } },
{ KE_KEY, 0xbd, { KEY_CAMERA } },
{ KE_KEY, 0xcc, { KEY_SWITCHVIDEOMODE } },
{ KE_KEY, 0xe0, { KEY_PROG1 } }, /* Task Manager */
{ KE_KEY, 0xe1, { KEY_F14 } }, /* Change Resolution */
{ KE_KEY, 0xe8, { KEY_SCREENLOCK } },
{ KE_KEY, 0xe9, { KEY_BRIGHTNESS_ZERO } },
{ KE_KEY, 0xeb, { KEY_CAMERA_ZOOMOUT } },
{ KE_KEY, 0xec, { KEY_CAMERA_UP } },
{ KE_KEY, 0xed, { KEY_CAMERA_DOWN } },
{ KE_KEY, 0xee, { KEY_CAMERA_LEFT } },
{ KE_KEY, 0xef, { KEY_CAMERA_RIGHT } },
[B]{ KE_KEY, 0xf3, { KEY_COMPOSE } },
{ KE_KEY, 0xf5, { KEY_F11 } },
{ KE_KEY, 0xf6, { KEY_TAB } },[/B]
{ KE_END, 0},
};

I've chosen some odd assignments since I'm using mostly Mypaint. However, you can choose other keymaps, and even re-assign them later with udev rules.  --they need to be in that structure to be reassigned.

**0xf3** is the Virtual Keyboard button, which I set for Application Popup Menu since there is no VirtualKeyboard keycode as far as I can tell.

**0xf5** is the Rotate Lock button, which I've assigned for Full Screen F11.  I don't know how Windows detects this being on or off.  0xf5 is sent to the OS when the state changed, but I don't see any state info.

**0xf6** is the front black button, which I've assigned to 'tab', which brings up the MyPaint toolbox.  This button will occasionally emit another keycode.  In Windows, the main press is "Enter", but holding it down brings up Ctrl-alt-delete, as I recall.  Not sure if this is handled by the OS or the BIOS.

If we figure this out, we can send a patch to the eeepc-wmi module maintainer for inclusion in the main kernel.


-=-=-

I got this machine for the built-in Wacom tablet, so I don't use the touchpad at all.  

You can disable the touchpad with a udev rule. Add this to the 99-local.rules.

# USB Device Bus 002 Device 005: ID 0eef:a001 D-WAV Scientific Co., Ltd - eGalax TouchScreen 
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="a001", RUN="/bin/rm /dev/input/event%n", OPTIONS="ignore_device"

This will remove the actual event device node, preventing xorg from talking to it.  (Xorg will still attempt and error out.)

There's probably a better solution out there.  I couldn't get udev to simply ignore the device, so I had to delete the device node.

-=-=-

The Intel driver does support screen rotate via XRandR, but I've not found out how to talk to the sensor hardware.  When I asked Asus tech support for details on hardware, they told me to "reinstall the OS."  :/

Even if we got that working, we'd also have to rotate the touchscreen and wacom drivers.  This can be done for Wacom, but not sure about touch.

---

### Post by abeowitz on 2011-11-05
BTW, this Perl script will turn off the touchscreen temporarily.  When power manager wakes up from blank screen, it will reenable/wake up devices though.  (Which is why I hacked the udev rule above.)

I was hoping to get the touchscreen drivers working so I could use the screen rotate lock button to turn it on/off as needed, but oh well...

> #!/usr/bin/perl 

@lines = `xinput -list | grep eGalax`;
foreach $line (@lines) {
    my ($id) = $line =~ /id=(\d+)/;
    my $line2 = `xinput -list-props $id | grep "Device Enabled"`;
    my ($enabled) = $line2 =~ /:.*(\d+)/;
    system "xinput set-int-prop $id \"Device Enabled\" 8 0";
}


This should probably have been done in bash to avoid loading Perl, but I don't know much bash.

---

### Post by Favux on 2011-11-05
To turn on/off touch you might want a toggle script similar to one of the touch-toggle scripts for the N-trigs.  Part 3 in the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492").
```
#!/bin/bash

## eGalax touch toggle script
##
## For touch state notification use:
##   sudo apt-get install libnotify-bin
## Otherwise comment (#) out the two notify-send lines.
## If installed see 'man notify-send'.

if [ -f /tmp/touch_off ]; then
	xinput set-prop "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" "Device Enabled" 1
	notify-send -t 1500 "eGalax MultiTouch touch ON"
	rm -f /tmp/touch_off && exit 0
else
	xinput set-prop "eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller" "Device Enabled" 0
	notify-send -t 1500 "eGalax MultiTouch touch OFF"
	echo 1 > /tmp/touch_off && exit 0
fi
```
Remember to make it executable and place it in a launcher. You can drag the launcher into a panel for single click.  Or bind it to a button/key.

If it doesn't work check that you have the same "device name".  Run *xinput list* and substitute the <device name> for touch in the output for *eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller*.

---

### Post by abeowitz on 2011-11-06
Wow, great stuff, Favux, thanks! :)

---

### Post by tannalv on 2011-12-09
According to the bug listing on ep121, the problem with the touchscreen lies in the kernel. It will be fixed in linux kernel 3.3 (and I can't wait! =).

[I]The discussion then moved over to linux-input mailing list were it got fully resolved by hid-multitouch developer. A fix will be in Linux 3.3 (its in a hid next branch). The fix is slightly larger than adding new product ID's to hid-multitouch. The touchscreen uses a "MT serial" protocol that happened to be added to hid-multitouch for another touchscreen in November timeframe as well. This version of eGalax touchscreen makes use of that new feature in hid-multitouch.

This issue is pure kernel side issue.[/I]

source: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445")

---

### Post by pirohmaniac on 2011-12-13
> **tannalv said:**
> According to the bug listing on ep121, the problem with the touchscreen lies in the kernel. It will be fixed in linux kernel 3.3 (and I can't wait! =).

[I]The discussion then moved over to linux-input mailing list were it got fully resolved by hid-multitouch developer. A fix will be in Linux 3.3 (its in a hid next branch). The fix is slightly larger than adding new product ID's to hid-multitouch. The touchscreen uses a "MT serial" protocol that happened to be added to hid-multitouch for another touchscreen in November timeframe as well. This version of eGalax touchscreen makes use of that new feature in hid-multitouch.

This issue is pure kernel side issue.[/I]

source: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/854445)

I KNOW! I can't wait to try Blender with gestures! :p And Kubuntu. Unitys unfriendlieness has pushed me back to KDE for a while. Maybe permanently. I like my widgets. Also the netbook interface isn't at all bad. The on screen keyboard however needs work.

---

### Post by deadland on 2011-12-14
I there any way to install Plasma Active Two on ubuntu 11.10?

[http://plasma-active.org/](http://plasma-active.org/)

---

### Post by pirohmaniac on 2011-12-16
probably, but it would be easier with Kubuntu because it's using lots of KDE libraries.

---

### Post by tannalv on 2011-12-19
> **pirohmaniac said:**
> I KNOW! I can't wait to try Blender with gestures! :p And Kubuntu. Unitys unfriendlieness has pushed me back to KDE for a while. Maybe permanently. I like my widgets. Also the netbook interface isn't at all bad. The on screen keyboard however needs work.

You'll be waiting for some time then. Kernel 3.2 won't be released until new years, or just after. Sooo... 12.04 will be based on kernel 3.2. It's not until 12.10 (almost a year from now) that we'll see touch-support for the ep121... :(

---

### Post by pirohmaniac on 2011-12-20
> **tannalv said:**
> You'll be waiting for some time then. Kernel 3.2 won't be released until new years, or just after. Sooo... 12.04 will be based on kernel 3.2. It's not until 12.10 (almost a year from now) that we'll see touch-support for the ep121... :(

Yeah, I figured. At least Blender runs on Windows! :D
Barely...

---

### Post by tannalv on 2012-01-18
So, being impatient I've compiled the latest kernel (latest as of Jan 18th).
You can find it (64-bit) here:

[http://hotfile.com/dl/142433848/be3a0f4/kernel-3.3a-18th-jan-12.tar.bz2.html]("http://hotfile.com/dl/142433848/be3a0f4/kernel-3.3a-18th-jan-12.tar.bz2.html")

PS. Only run this on a test system. You do not know what I have done with it. If you want to be 100% sure and safe, compile your own kernel.

However, here it is. It now supports touch! :D

---

### Post by deadland on 2012-01-18
Does multitouch work?

---

### Post by pirohmaniac on 2012-01-18
:biggrin:\\:D/Oh YAY! Downloading now!:biggrin:\\:D/
Cant wait until I can switch over comfortably. Learning to program on Winblows blows. :lolflag:
Seriously it really sucks. So slow.

---

### Post by tannalv on 2012-01-18
> **deadland said:**
> Does multitouch work?

Well, it's SUPPOSED to work. But even on my TX2's I only get single touch. This one (ep121) is supposed to have two touch points. However, if I touch somewhere on the screen and then touch with a second finger it only registers my first finger.
So, I don't know. Other people will have to experiment and direct further on that question. I just grabbed the latest kernel-stuff, make oldconfig and modulized most (new) stuff, apart from the egalaxy touch (which I built in to the kernel).

If you want to compile the kernel yourself, go to:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary")

Select the top most "snapshot" in the "commit | commitdiff | tree | snapshot" - list.
Then untar/compile as you would any other kernel under ubuntu.

---

### Post by tannalv on 2012-01-18
> **pirohmaniac said:**
> Learning to program on Winblows blows. :lolflag:
Seriously it really sucks. So slow.

I second that. But then again, I think all programming blows.
I'm so glad I don't have to hassle with that... :P

---

### Post by tannalv on 2012-01-19
The things I feel are missing in GNU/Linux are:

- G-sensor, it's a minus to me that I can't just rotate the screen and the screen follows, just like some other OS does.

- Buttons, it'd be *neat* if I could just hit the top button and get an on screen keyboard to flip out. Now I have to start it up and hit the screen to get it out. It's just... simpler to hit the button, in my opinion.
And even if you don't use the button(s) for that they'd still be *neat* to have for some use.

- Multitouch. This is the mecca, the holy Graal, for this thing. After all, multitouch is what it was built for. But all I get is single-touch.
Now, given that I never could get my TX2 to do much more than single touch either, it still is about time it was either a part of the kernel or a simple set up (no, I'm no programming freak, I do not do xml very well, GINN always was a hassle for me to understand what and how, I've tried looking for good configuration-files, but everybody just talks about how this and that is supposed to be a great way of programming GINN, nobody drops a nice config-file that I can get to work).

---

### Post by Favux on 2012-01-19
None on the Ginn scripts on the HOW TO worked for you?  These didn't?:  [http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391](http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391)

There's 2 or 3 Python app.s out there that rotate based on the accelerometer.  So it is doable if the EP121's accelerometer is in the kernel and reporting some place.  We've been thinking we might want to add accelerometer rotation to Magick Rotation at some point.

---

### Post by tannalv on 2012-01-20
> **Favux said:**
> None on the Ginn scripts on the HOW TO worked for you?  These didn't?:  [http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391](http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391)

The greatest problem is always behind the screen. And in this case it is me. Weee...
No, I didn't make much out of any of the config-files from the TX2 howto.
I have two of the TX2's, and still they're mostly just gathering dust by now, so... Anyways.

Here's some info if it's of any use to you.

EDIT: Also, xev and showkey both show ALL extra buttons as keycode 240. Doesn't matter whish one I push, they all give off keycode 240. Seems like the g-sensor lock key isn't a lock per se, it's more of a key that sends a signal. Pushing it either to unlock or to lock gives off keycode 240. Just like all the other buttons. Probably makes sense to someone. Not me...
(Ah, abeowitz has already addressed this issue on page 8 )

---

### Post by tannalv on 2012-01-20
NEW KERNEL COMPILED 19th Jan 2012

Not that there's much of a change. Still, here it is:
[http://hotfile.com/dl/142804266/2f08914/kernel-3.3a-19th-jan-2012.tar.bz2.html]("http://hotfile.com/dl/142804266/2f08914/kernel-3.3a-19th-jan-2012.tar.bz2.html")

(As always, only run this on a test system - you do not know whether or not I have added a rootkit or worse, have really messed up this kernel. If you want to be on the safe side, compile the kernel yourself. It's not very hard nor does it take very long.)

---

### Post by deadland on 2012-01-20
Seems like I will switch to Gnome Shell Soon:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA0NTc]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0NTc")

---

### Post by tannalv on 2012-01-20
Here's the full 3.3.0-rc1. 64-bit.
As always, only run this on a test system. You don't know if I've added some funny surprises, or even worse, if I've messed it up totally.
It runs fine for me, but YMMV.

[http://hotfile.com/dl/142937089/d36ca40/linux-3.3.0-rc1.tar.bz2.html]("http://hotfile.com/dl/142937089/d36ca40/linux-3.3.0-rc1.tar.bz2.html")

(Unless there's a new RC-release I won't build any more kernels. If you wish to compile the kernel yourself, grab it from [kernel.org]("http://www.kernel.org/") and follow this guide to compile it: [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"))

---

### Post by tannalv on 2012-01-20
> **deadland said:**
> Seems like I will switch to Gnome Shell Soon:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA0NTc]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0NTc")

M-mm. I have a feeling the KDE-team have a nice surprise up their sleeve as well. But that sounds nice.

Also, Phoronix, it's a lovely news-site. I like! ; )

---

### Post by pirohmaniac on 2012-01-23
> **tannalv said:**
> M-mm. I have a feeling the KDE-team have a nice surprise up their sleeve as well. But that sounds nice.

Also, Phoronix, it's a lovely news-site. I like! ; )

Plasma Active but so far it seems like they've stripped it too much. However the netbook layout of KDE is supercool. The only problem I had was the on screen keyboard was way too big to use.

I hope KDE widgets respond to multitouch! \\:D/

edit: No wait! What I REALLY hope is that Asus releases an update to allow more than two-#%#$$#-finger touch!

---

### Post by tannalv on 2012-01-24
> **pirohmaniac said:**
> 
I hope KDE widgets respond to multitouch! \\:D/

edit: No wait! What I REALLY hope is that Asus releases an update to allow more than two-#%#$$#-finger touch!

So you haven't been able to get multitouch to work?
There might be an update as Windows 8 comes out. Though, I wouldn't hold my breath.

This is a great device though. It's much more responsive than my TX2's ever were. Yes, I know, capacitive vs. resistive. But still, this feels like a more proper device where the TX2's multitouch was more of a cheap "proof of concept"-thing.

---

### Post by timhoffmann on 2012-01-27
I finally got multitouch (and the buttons) to work on my ep121.
I have precise (12.4) running. Wacom works out of the box of course. For the touch to work I did:
i) install eGalax driver.
It says Kernel 3.0.x but the 3.2 Kernel from ubuntu precise seems to be fine.
It has all the modules the installation instruction asks for, so installation goes smoothly, but still no touch -yet. Problem is: the device is not recognized by the usb-hid driver. So:

ii) install hid-multitouch
modprobe hid-multitouch
(if it works for you put it in /etc/modules)

sudo su -
cd /sys/module/hid_multitouch/drivers/hid: hid-multitouch
echo "3 oeef aoo1 1" > new_id

(this actually  comes from here:
comments.gmane.org/gmane/linux.kernel.input/22516
 I have put it in /etc/rc.local before the starting of the eGTouchd
)

This does the magic:
Now touch should work but with inverted y.
So edit /etc/eGTouchd.ini to have Direction set to 2 (i.e. invert y).
this is single touch so far.
iii) modify and install multitouch_drv for xorg
Now to get multitouch to work I tried the X11 multitouch driver (put it in /usr/share/X11/xorg.conf.d/52-egalax-virtual.conf as the driver instead of evdev).
This gave me some  dual touch, but the driver is made for relative input only and ther seems no way to configure it diffrently. So in the end I had to modify the source and compile it myself to report absolute coordinatees and to make a single touch act as a click.
But now I do have a working dual touch. One finger works as expected and with two I can scroll...

For the buttons you have to recompile the eeepc-wmi kernel driver as mentioned earlier.

Alltogether I am quite happy with the setup
(and that in gimp I can now draw with the pen, erase with its back, and *smear* with the finger is priceless ;) )

---

### Post by pirohmaniac on 2012-01-29
> **tannalv said:**
> So you haven't been able to get multitouch to work?
There might be an update as Windows 8 comes out. Though, I wouldn't hold my breath.

Two-finger multitouch does work in Windows 7 but I've been holding off on Linux until I felt comfortable I could use it without any issues. It's for remote access to our customers so it has to be ready now when I need it.

I think I might follow timhoffmans post there and see what happens. If I can get it so the screen lock rotates the screen instead I'll have everything I need.

As for my multitouch comment, I'm hoping Asus decided to be lazy and limit the capability of the firmware instead of build a full multitouch GUI for Windows.

---

### Post by tannalv on 2012-02-01
So... There's a 3.3-rc2 out. I promised I would post, but there's a better way. Go to ubuntu's own site for experimental kernels:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

There you'll find the latest 3.3-rc2 (with the Ubuntu patches, I'd suppose?).
Also, there you have both i386 and x64 versions of them.

You need to start off with the linux-headers-<numbers>_all.deb. Then you can install the regular two packages for either i386 or x64.

Thanks for the reply, piro. :)

And thank you very much for your guide, timh. :)

---

### Post by pirohmaniac on 2012-02-13
I just tried the 3.3-rc3 on a fresh install. IT WORKS! There's a small issue with right-click but it's good enough. Goodbye Winblows you crappy piece of crapware. Hello awesomeness. :biggrin:
Now my "Powered by Ubuntu" sticker actually means something. I just have to decide if I want Ubuntu... or Kubuntu...

---

### Post by pcit on 2012-02-17
Anyone is tracking down the gsensor driver ?

---

### Post by pirohmaniac on 2012-02-21
> **pcit said:**
> Anyone is tracking down the gsensor driver ?

I don't think anyone has even found it in Linux yet or if they have, they're not telling.

---

### Post by pcit on 2012-02-22
I did some digging and found this particular gsensor is called ATK0201 according to the windows driver. I checked the Linux driver, there is atk0100 which suppose to be hardware temp. Monitor service. I also heard there might be some gsensor related code for wetab/exopc we can use, but haven't spent extensive time yet.

I haven't found atk0201 native Linux driver either..

---

### Post by tannalv on 2012-02-29
So, I played around with Android x86 on the device. It performs really nicely. Only thing is, bluetooth doesn't work on it. So I replace my wireless card with a new Intel 6230. And then bluetooth works! :D  But wireless doesn't. :(

If you're eager to play around with Android, you can find it here:
[http://android-x86.googlecode.com/files/android-x86-4.0-RC1-asus_laptop.iso]("http://android-x86.googlecode.com/files/android-x86-4.0-RC1-asus_laptop.iso")

---

### Post by pirohmaniac on 2012-03-07
> **tannalv said:**
> So, I played around with Android x86 on the device. It performs really nicely. Only thing is, bluetooth doesn't work on it. So I replace my wireless card with a new Intel 6230. And then bluetooth works! :D  But wireless doesn't. :(

If you're eager to play around with Android, you can find it here:
[http://android-x86.googlecode.com/files/android-x86-4.0-RC1-asus_laptop.iso](http://android-x86.googlecode.com/files/android-x86-4.0-RC1-asus_laptop.iso)

I had a Tegra2 tablet for a little while. Took it back because I wanted my Asus instead. Can't use Blender on Android.
Also [http://www.blendernation.com/2012/03/07/non-blender-get-free-unity-licenses-for-ios-and-android/](http://www.blendernation.com/2012/03/07/non-blender-get-free-unity-licenses-for-ios-and-android/)

---

### Post by pirohmaniac on 2012-03-13
Okay I take it back. Maybe you can.
[http://www.ubuntubuzz.com/2012/02/linux-kernel-33-will-let-you-boot-into.html](http://www.ubuntubuzz.com/2012/02/linux-kernel-33-will-let-you-boot-into.html)

---

### Post by pirohmaniac on 2012-03-20
I dumped Ubuntu and installed Plasma Active [http://cdimage.ubuntu.com/kubuntu-active/daily-live/](http://cdimage.ubuntu.com/kubuntu-active/daily-live/)
Other than the few bugs I ran into and not being able to log in with the OSK I think it's what I'm going to go with once it's stable.

---

### Post by RaiGal on 2012-06-09
Hello, I was wondering if anyone have tried running android ICS on this tablet. Thanks :)

---

### Post by tannalv on 2012-06-24
> **RaiGal said:**
> Hello, I was wondering if anyone have tried running android ICS on this tablet. Thanks :)

There sure is! If you look back one page (page 11) you'll see a couple of posts on Android.
[http://ubuntuforums.org/showpost.php?p=11726969&postcount=109]("http://ubuntuforums.org/showpost.php?p=11726969&postcount=109")

---

### Post by deadland on 2012-08-22
Dear all, someone wants to help me reporting hardware related bugs and Ubuntu 12.10 (Quantal Quetzal) to launchpad.

Please check out the following thread:

[http://ubuntuforums.org/showthread.php?t=2046102&highlight=ep121](http://ubuntuforums.org/showthread.php?t=2046102&highlight=ep121)

Best regards

---

### Post by Alan Turing on 2012-09-06
> **timhoffmann said:**
> 
ii) install hid-multitouch
modprobe hid-multitouch
(if it works for you put it in /etc/modules)

sudo su -
cd /sys/module/hid_multitouch/drivers/hid: hid-multitouch
echo "3 oeef aoo1 1" > new_id

(this actually  comes from here:
comments.gmane.org/gmane/linux.kernel.input/22516
 I have put it in /etc/rc.local before the starting of the eGTouchd
)

I have Ubuntu 12.04.1. According to lsmod, the module hid_multitouch is loaded. However, the command
echo "3 oeef aoo1 1" > new_id
gives as response the following line:
-su: echo: write error: Invalid argument

My first guess was the the running eGTouchd could have been the problem. Therefore, I commented the line/ usr/bin/eGTouchD in /etc/rc.local. Then I rebooted, however I received the same error message for echo "3 oeef aoo1 1" > new_id

Do you have any ideas?

---

