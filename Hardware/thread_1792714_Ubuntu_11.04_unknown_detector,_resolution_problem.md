---
title: "Ubuntu 11.04 unknown detector, resolution problem"
date: 2011-06-28
forum: Hardware
---

### Post by ntlam on 2011-06-28
Hi,

I just installed Ubuntu 11.04 on my desktop. Everything looks fine. But then I have a new monitor. Now the resolution looks bad. When checking monitor, the resolution is already 1920x1080, refresh rate 51 Hz, but UNKNOWN monitor.

In xorg.conf, there is only this section: 

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Any help please. Reading blur text really hurts my eyes.

Thanks,

Lam

---

### Post by wolfen69 on 2011-06-28
What kind of video card is it?

---

### Post by ntlam on 2011-06-28
I have Nvidia G96 [Quadro FX 580].

Lam

---

### Post by Yellow Pasque on 2011-06-28
What kind of monitor do you have? Post your /var/log/Xorg.0.log

---

### Post by ntlam on 2011-06-28
I have Dell P2411Hb.

And the file you need is attached.

Thanks,
Lam

---

### Post by Yellow Pasque on 2011-06-28
PDF? If you're serious, try again in simple text format.

---

### Post by ntlam on 2011-06-28
Sorry, I first tried with txt but the file exceeded the size limit.

Maybe I just need to copy the whole file here:

[    33.328] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    33.328] X Protocol Version 11, Revision 0
[    33.328] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    33.328] Current Operating System: Linux kaly 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    33.328] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=c834bb7b-251c-4e84-9256-ada2e8c9495c ro quiet splash vt.handoff=7
[    33.328] Build Date: 21 May 2011  11:48:41AM
[    33.328] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    33.328] Current version of pixman: 0.20.2
[    33.328] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    33.328] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.328] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 28 12:07:49 2011
[    33.328] (==) Using config file: "/etc/X11/xorg.conf"
[    33.328] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.328] (==) No Layout section.  Using the first Screen section.
[    33.328] (==) No screen section available. Using defaults.
[    33.328] (**) |-->Screen "Default Screen Section" (0)
[    33.328] (**) |   |-->Monitor "<default monitor>"
[    33.328] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    33.328] (**) |   |-->Device "Default Device"
[    33.328] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    33.328] (==) Automatically adding devices
[    33.328] (==) Automatically enabling devices
[    33.328] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.328] 	Entry deleted from font path.
[    33.328] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.328] 	Entry deleted from font path.
[    33.328] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.328] 	Entry deleted from font path.
[    33.328] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.328] 	Entry deleted from font path.
[    33.328] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.328] 	Entry deleted from font path.
[    33.328] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    33.328] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.328] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.328] (II) Loader magic: 0x7e0280
[    33.328] (II) Module ABI versions:
[    33.328] 	X.Org ANSI C Emulation: 0.4
[    33.328] 	X.Org Video Driver: 10.0
[    33.328] 	X.Org XInput driver : 12.3
[    33.328] 	X.Org Server Extension : 5.0
[    33.329] (--) PCI:*(0:3:0:0) 10de:0659:10de:063a rev 161, Mem @ 0xf6000000/16777216, 0xa0000000/536870912, 0xf4000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
[    33.330] (--) PCI: (0:4:0:0) 10de:0659:10de:063a rev 161, Mem @ 0xf1000000/16777216, 0xc0000000/536870912, 0xf2000000/33554432, I/O @ 0x0000cc80/128, BIOS @ 0x????????/524288
[    33.330] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.330] (II) LoadModule: "extmod"
[    33.330] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.330] (II) Module extmod: vendor="X.Org Foundation"
[    33.330] 	compiled for 1.10.1, module version = 1.0.0
[    33.330] 	Module class: X.Org Server Extension
[    33.330] 	ABI class: X.Org Server Extension, version 5.0
[    33.330] (II) Loading extension MIT-SCREEN-SAVER
[    33.330] (II) Loading extension XFree86-VidModeExtension
[    33.330] (II) Loading extension XFree86-DGA
[    33.330] (II) Loading extension DPMS
[    33.330] (II) Loading extension XVideo
[    33.330] (II) Loading extension XVideo-MotionCompensation
[    33.330] (II) Loading extension X-Resource
[    33.330] (II) LoadModule: "dbe"
[    33.330] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.330] (II) Module dbe: vendor="X.Org Foundation"
[    33.330] 	compiled for 1.10.1, module version = 1.0.0
[    33.330] 	Module class: X.Org Server Extension
[    33.330] 	ABI class: X.Org Server Extension, version 5.0
[    33.330] (II) Loading extension DOUBLE-BUFFER
[    33.330] (II) LoadModule: "glx"
[    33.330] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    33.338] (II) Module glx: vendor="NVIDIA Corporation"
[    33.338] 	compiled for 4.0.2, module version = 1.0.0
[    33.338] 	Module class: X.Org Server Extension
[    33.338] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    33.338] (II) Loading extension GLX
[    33.338] (II) LoadModule: "record"
[    33.338] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.338] (II) Module record: vendor="X.Org Foundation"
[    33.338] 	compiled for 1.10.1, module version = 1.13.0
[    33.338] 	Module class: X.Org Server Extension
[    33.338] 	ABI class: X.Org Server Extension, version 5.0
[    33.338] (II) Loading extension RECORD
[    33.338] (II) LoadModule: "dri"
[    33.339] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.339] (II) Module dri: vendor="X.Org Foundation"
[    33.339] 	compiled for 1.10.1, module version = 1.0.0
[    33.339] 	ABI class: X.Org Server Extension, version 5.0
[    33.339] (II) Loading extension XFree86-DRI
[    33.339] (II) LoadModule: "dri2"
[    33.339] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.339] (II) Module dri2: vendor="X.Org Foundation"
[    33.339] 	compiled for 1.10.1, module version = 1.2.0
[    33.339] 	ABI class: X.Org Server Extension, version 5.0
[    33.339] (II) Loading extension DRI2
[    33.339] (==) Matched nvidia as autoconfigured driver 0
[    33.339] (==) Matched nouveau as autoconfigured driver 1
[    33.339] (==) Matched nv as autoconfigured driver 2
[    33.339] (==) Matched vesa as autoconfigured driver 3
[    33.339] (==) Matched fbdev as autoconfigured driver 4
[    33.339] (==) Assigned the driver to the xf86ConfigLayout
[    33.339] (II) LoadModule: "nvidia"
[    33.339] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    33.339] (II) Module nvidia: vendor="NVIDIA Corporation"
[    33.339] 	compiled for 4.0.2, module version = 1.0.0
[    33.339] 	Module class: X.Org Video Driver
[    33.340] (II) LoadModule: "nouveau"
[    33.352] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    33.353] (II) Module nouveau: vendor="X.Org Foundation"
[    33.353] 	compiled for 1.10.0, module version = 0.0.16
[    33.353] 	Module class: X.Org Video Driver
[    33.353] 	ABI class: X.Org Video Driver, version 10.0
[    33.353] (II) LoadModule: "nv"
[    33.353] (WW) Warning, couldn't open module nv
[    33.353] (II) UnloadModule: "nv"
[    33.353] (II) Unloading nv
[    33.353] (EE) Failed to load module "nv" (module does not exist, 0)
[    33.353] (II) LoadModule: "vesa"
[    33.353] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.353] (II) Module vesa: vendor="X.Org Foundation"
[    33.353] 	compiled for 1.10.0, module version = 2.3.0
[    33.353] 	Module class: X.Org Video Driver
[    33.353] 	ABI class: X.Org Video Driver, version 10.0
[    33.353] (II) LoadModule: "fbdev"
[    33.354] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.354] (II) Module fbdev: vendor="X.Org Foundation"
[    33.354] 	compiled for 1.10.0, module version = 0.4.2
[    33.354] 	ABI class: X.Org Video Driver, version 10.0
[    33.354] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    33.354] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    33.354] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    33.354] (II) NOUVEAU driver for NVIDIA chipset families :
[    33.354] 	RIVA TNT    (NV04)
[    33.354] 	RIVA TNT2   (NV05)
[    33.354] 	GeForce 256 (NV10)
[    33.354] 	GeForce 2   (NV11, NV15)
[    33.354] 	GeForce 4MX (NV17, NV18)
[    33.354] 	GeForce 3   (NV20)
[    33.354] 	GeForce 4Ti (NV25, NV28)
[    33.354] 	GeForce FX  (NV3x)
[    33.354] 	GeForce 6   (NV4x)
[    33.354] 	GeForce 7   (G7x)
[    33.354] 	GeForce 8   (G8x)
[    33.354] (II) VESA: driver for VESA chipsets: vesa
[    33.354] (II) FBDEV: driver for framebuffer: fbdev
[    33.354] (++) using VT number 7

[    33.354] (II) Loading sub module "fb"
[    33.354] (II) LoadModule: "fb"
[    33.354] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.354] (II) Module fb: vendor="X.Org Foundation"
[    33.354] 	compiled for 1.10.1, module version = 1.0.0
[    33.354] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.354] (II) Loading sub module "wfb"
[    33.354] (II) LoadModule: "wfb"
[    33.355] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.355] (II) Module wfb: vendor="X.Org Foundation"
[    33.355] 	compiled for 1.10.1, module version = 1.0.0
[    33.355] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.355] (II) Loading sub module "ramdac"
[    33.355] (II) LoadModule: "ramdac"
[    33.355] (II) Module "ramdac" already built-in
[    33.355] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    33.355] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.355] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.355] (WW) Falling back to old probe method for vesa
[    33.355] (WW) Falling back to old probe method for fbdev
[    33.355] (II) Loading sub module "fbdevhw"
[    33.355] (II) LoadModule: "fbdevhw"
[    33.355] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.355] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.355] 	compiled for 1.10.1, module version = 0.0.2
[    33.355] 	ABI class: X.Org Video Driver, version 10.0
[    33.355] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    33.355] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    33.355] (==) NVIDIA(0): RGB weight 888
[    33.355] (==) NVIDIA(0): Default visual is TrueColor
[    33.355] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    33.355] (**) NVIDIA(0): Option "NoLogo" "True"
[    34.734] (II) NVIDIA(GPU-0): Display (DELL P2411H (DFP-0)) does not support NVIDIA 3D
[    34.734] (II) NVIDIA(GPU-0):     Vision stereo.
[    34.735] (II) NVIDIA(0): NVIDIA GPU Quadro FX 580 (G96GL) at PCI:3:0:0 (GPU-0)
[    34.735] (--) NVIDIA(0): Memory: 524288 kBytes
[    34.735] (--) NVIDIA(0): VideoBIOS: 62.94.96.00.05
[    34.735] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    34.735] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    34.735] (--) NVIDIA(0): Connected display device(s) on Quadro FX 580 at PCI:3:0:0
[    34.735] (--) NVIDIA(0):     DELL P2411H (DFP-0)
[    34.735] (--) NVIDIA(0): DELL P2411H (DFP-0): 330.0 MHz maximum pixel clock
[    34.735] (--) NVIDIA(0): DELL P2411H (DFP-0): Internal Dual Link TMDS
[    34.825] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    34.825] (==) NVIDIA(0): 
[    34.825] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    34.825] (==) NVIDIA(0):     will be used as the requested mode.
[    34.825] (==) NVIDIA(0): 
[    34.825] (II) NVIDIA(0): Validated modes:
[    34.825] (II) NVIDIA(0):     "nvidia-auto-select"
[    34.825] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    34.855] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    34.855] (--) NVIDIA(0):     option
[    34.855] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[    34.855] (WW) NVIDIA(0):     UBB.
[    34.855] (II) UnloadModule: "nouveau"
[    34.855] (II) Unloading nouveau
[    34.855] (II) UnloadModule: "vesa"
[    34.855] (II) Unloading vesa
[    34.855] (II) UnloadModule: "fbdev"
[    34.855] (II) Unloading fbdev
[    34.855] (II) UnloadModule: "fbdevhw"
[    34.855] (II) Unloading fbdevhw
[    34.855] (--) Depth 24 pixmap format is 32 bpp
[    37.303] (II) NVIDIA(GPU-1): NVIDIA GPU Quadro FX 580 (G96GL) at PCI:4:0:0 (GPU-1)
[    37.303] (--) NVIDIA(GPU-1): Memory: 524288 kBytes
[    37.303] (--) NVIDIA(GPU-1): VideoBIOS: 62.94.96.00.05
[    37.303] (II) NVIDIA(GPU-1): Detected PCI Express Link width: 16X
[    37.303] (--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
[    37.303] (--) NVIDIA(GPU-1): Connected display device(s) on Quadro FX 580 at PCI:4:0:0
[    37.303] (--) NVIDIA(GPU-1):     none
[    37.303] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    37.319] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    37.342] (II) Loading extension NV-GLX
[    37.396] (==) NVIDIA(0): Disabling shared memory pixmaps
[    37.396] (==) NVIDIA(0): Backing store disabled
[    37.396] (==) NVIDIA(0): Silken mouse enabled
[    37.396] (==) NVIDIA(0): DPMS enabled
[    37.396] (II) Loading extension NV-CONTROL
[    37.397] (II) Loading extension XINERAMA
[    37.397] (II) Loading sub module "dri2"
[    37.397] (II) LoadModule: "dri2"
[    37.397] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    37.397] (II) Module dri2: vendor="X.Org Foundation"
[    37.397] 	compiled for 1.10.1, module version = 1.2.0
[    37.397] 	ABI class: X.Org Server Extension, version 5.0
[    37.397] (II) NVIDIA(0): [DRI2] Setup complete
[    37.397] (==) RandR enabled
[    37.397] (II) Initializing built-in extension Generic Event Extension
[    37.397] (II) Initializing built-in extension SHAPE
[    37.397] (II) Initializing built-in extension MIT-SHM
[    37.397] (II) Initializing built-in extension XInputExtension
[    37.397] (II) Initializing built-in extension XTEST
[    37.397] (II) Initializing built-in extension BIG-REQUESTS
[    37.397] (II) Initializing built-in extension SYNC
[    37.397] (II) Initializing built-in extension XKEYBOARD
[    37.397] (II) Initializing built-in extension XC-MISC
[    37.397] (II) Initializing built-in extension SECURITY
[    37.397] (II) Initializing built-in extension XINERAMA
[    37.397] (II) Initializing built-in extension XFIXES
[    37.397] (II) Initializing built-in extension RENDER
[    37.397] (II) Initializing built-in extension RANDR
[    37.397] (II) Initializing built-in extension COMPOSITE
[    37.397] (II) Initializing built-in extension DAMAGE
[    37.397] (II) Initializing built-in extension GESTURE
[    37.398] (II) Initializing extension GLX
[    37.417] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.424] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    37.425] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.425] (II) LoadModule: "evdev"
[    37.425] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.425] (II) Module evdev: vendor="X.Org Foundation"
[    37.425] 	compiled for 1.10.0.902, module version = 2.6.0
[    37.425] 	Module class: X.Org XInput Driver
[    37.425] 	ABI class: X.Org XInput driver, version 12.3
[    37.425] (II) Using input driver 'evdev' for 'Power Button'
[    37.425] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.425] (**) Power Button: always reports core events
[    37.425] (**) Power Button: Device: "/dev/input/event1"
[    37.425] (--) Power Button: Found keys
[    37.425] (II) Power Button: Configuring as keyboard
[    37.425] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    37.425] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.425] (**) Option "xkb_rules" "evdev"
[    37.425] (**) Option "xkb_model" "pc105"
[    37.425] (**) Option "xkb_layout" "us"
[    37.427] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.427] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.427] (II) Using input driver 'evdev' for 'Power Button'
[    37.427] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.427] (**) Power Button: always reports core events
[    37.427] (**) Power Button: Device: "/dev/input/event0"
[    37.427] (--) Power Button: Found keys
[    37.427] (II) Power Button: Configuring as keyboard
[    37.427] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    37.427] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.427] (**) Option "xkb_rules" "evdev"
[    37.427] (**) Option "xkb_model" "pc105"
[    37.427] (**) Option "xkb_layout" "us"
[    37.432] (II) config/udev: Adding input device DELL Dell USB Entry Keyboard (/dev/input/event2)
[    37.432] (**) DELL Dell USB Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[    37.432] (II) Using input driver 'evdev' for 'DELL Dell USB Entry Keyboard'
[    37.432] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.432] (**) DELL Dell USB Entry Keyboard: always reports core events
[    37.432] (**) DELL Dell USB Entry Keyboard: Device: "/dev/input/event2"
[    37.432] (--) DELL Dell USB Entry Keyboard: Found keys
[    37.432] (II) DELL Dell USB Entry Keyboard: Configuring as keyboard
[    37.432] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.1/2-5.1:1.0/input/input2/event2"
[    37.432] (II) XINPUT: Adding extended input device "DELL Dell USB Entry Keyboard" (type: KEYBOARD)
[    37.432] (**) Option "xkb_rules" "evdev"
[    37.432] (**) Option "xkb_model" "pc105"
[    37.432] (**) Option "xkb_layout" "us"
[    37.433] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[    37.433] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    37.433] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    37.433] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.433] (**) Logitech USB Optical Mouse: always reports core events
[    37.433] (**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
[    37.433] (--) Logitech USB Optical Mouse: Found 12 mouse buttons
[    37.433] (--) Logitech USB Optical Mouse: Found scroll wheel(s)
[    37.433] (--) Logitech USB Optical Mouse: Found relative axes
[    37.433] (--) Logitech USB Optical Mouse: Found x and y relative axes
[    37.433] (II) Logitech USB Optical Mouse: Configuring as mouse
[    37.433] (II) Logitech USB Optical Mouse: Adding scrollwheel support
[    37.433] (**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    37.433] (**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.433] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.2/2-5.2:1.0/input/input3/event3"
[    37.433] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
[    37.433] (II) Logitech USB Optical Mouse: initialized for relative axes.
[    37.433] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    37.433] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    37.433] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    37.433] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    37.434] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    37.434] (II) No input driver/identifier specified (ignoring)
[    37.439] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event4)
[    37.439] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    37.439] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    37.439] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.439] (**) Dell WMI hotkeys: always reports core events
[    37.439] (**) Dell WMI hotkeys: Device: "/dev/input/event4"
[    37.440] (--) Dell WMI hotkeys: Found keys
[    37.440] (II) Dell WMI hotkeys: Configuring as keyboard
[    37.440] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    37.440] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    37.440] (**) Option "xkb_rules" "evdev"
[    37.440] (**) Option "xkb_model" "pc105"
[    37.440] (**) Option "xkb_layout" "us"
[    44.738] (II) NVIDIA(0): Setting mode "1920x1080_60_0"


Lam

---

### Post by Yellow Pasque on 2011-06-28
Thanks,, that's better. What resolution and refreshrate are you aiming for?

---

### Post by ntlam on 2011-06-28
I would want highest resolution and refresh rate. The resolution is already 1920x1080. But the refresh rate is different in Monitor setting and in Nvidia X server setting. In monitor setting, three options are 149, 51 and 50 Hz. In Nvidia X server display configuration, refresh rate options are auto and 60 Hz. 
Also, Dell P2411H is shown in Nvidia setting, but in monitor setting, it is unknown.

Lam

---

### Post by ntlam on 2011-07-08
So you haven't got any suggestion yet?

---

