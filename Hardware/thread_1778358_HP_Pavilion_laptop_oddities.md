---
title: "HP Pavilion laptop oddities"
date: 2011-06-08
forum: Hardware
---

### Post by rogue1987 on 2011-06-08
I have 11.04 installed on an older 17" HP Pavilion, don't remember the exact model (I think it was a DV something). It has 1 GB RAM, 90 GB HD, a dual core Intel 1.66 Ghz processor, built in Nvidia graphics.

first, it won't run Unity. I briefly had it going but it wouldn't come back up on reboot. When I go to additional drivers it shows the recommended Nvidia accelerated driver (version current) as activated but not currently in use. Version 173 is also installed, choosing it doesn't make a difference and the same message is displayed, activated but not currently in use.

Second, the battery life sucks. It was bad under Windows Media Center that was installed on it when we got it, about 2 hours tops. I don't think I'm even getting that with Ubuntu and I expected it to do a little better. I'm betting I get about 1 1/2 hours or less of batter roughly. I've turned off a few things that I could find, like bluetooth and assistive tech in start up apps.

so right now, I'm just running plain Gnome, with nothing else going. as I'm typing this, I just noticed my top panel has some drop out spots and isn't refreshing. I turned on auto hide and once it shows again, the drop out spots are gone.

I'm guessing most of the issues are centered around the video but certainly don't know how to fix it or if its even possible to fix. Anyone have any thoughts or things to try?

---

### Post by Peter09 on 2011-06-09
Can you tell us the output of
 
```
lshw -C video
```

---

### Post by rogue1987 on 2011-06-09
I certainly will when I get home tonight. Unfortunately, I don't have the laptop with me today.

---

### Post by rogue1987 on 2011-06-09
*-display               
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory:d0000000-d0ffffff

---

### Post by lidex on 2011-06-10
Try running this command to update your xorg.conf:
```
sudo nvidia-xconfig
```
**Reboot**

Now post this output:
```
cat /var/log/Xorg.0.log
```

---

### Post by rogue1987 on 2011-06-10
[    26.862] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    26.862] X Protocol Version 11, Revision 0
[    26.862] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    26.862] Current Operating System: Linux hp 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    26.862] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=683d1162-d75f-4aea-870c-7819bca2994a ro quiet splash vt.handoff=7
[    26.862] Build Date: 21 May 2011  11:38:35AM
[    26.862] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.862] Current version of pixman: 0.20.2
[    26.862] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    26.862] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.863] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  9 22:57:06 2011
[    26.863] (==) Using config file: "/etc/X11/xorg.conf"
[    26.863] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.863] (==) No Layout section.  Using the first Screen section.
[    26.863] (==) No screen section available. Using defaults.
[    26.863] (**) |-->Screen "Default Screen Section" (0)
[    26.863] (**) |   |-->Monitor "<default monitor>"
[    26.863] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    26.863] (**) |   |-->Device "Default Device"
[    26.863] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.863] (==) Automatically adding devices
[    26.864] (==) Automatically enabling devices
[    26.864] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.864] 	Entry deleted from font path.
[    26.864] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.864] 	Entry deleted from font path.
[    26.864] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.864] 	Entry deleted from font path.
[    26.864] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.864] 	Entry deleted from font path.
[    26.864] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.864] 	Entry deleted from font path.
[    26.864] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.864] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.864] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.864] (II) Loader magic: 0x81ffde0
[    26.864] (II) Module ABI versions:
[    26.864] 	X.Org ANSI C Emulation: 0.4
[    26.864] 	X.Org Video Driver: 10.0
[    26.864] 	X.Org XInput driver : 12.3
[    26.864] 	X.Org Server Extension : 5.0
[    26.865] (--) PCI:*(0:1:0:0) 10de:01d8:103c:30a5 rev 161, Mem @ 0xd1000000/16777216, 0xc0000000/268435456, 0xd0000000/16777216
[    26.865] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.865] (II) LoadModule: "extmod"
[    26.866] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.866] (II) Module extmod: vendor="X.Org Foundation"
[    26.866] 	compiled for 1.10.1, module version = 1.0.0
[    26.866] 	Module class: X.Org Server Extension
[    26.866] 	ABI class: X.Org Server Extension, version 5.0
[    26.866] (II) Loading extension MIT-SCREEN-SAVER
[    26.866] (II) Loading extension XFree86-VidModeExtension
[    26.866] (II) Loading extension XFree86-DGA
[    26.866] (II) Loading extension DPMS
[    26.866] (II) Loading extension XVideo
[    26.866] (II) Loading extension XVideo-MotionCompensation
[    26.866] (II) Loading extension X-Resource
[    26.866] (II) LoadModule: "dbe"
[    26.867] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.867] (II) Module dbe: vendor="X.Org Foundation"
[    26.867] 	compiled for 1.10.1, module version = 1.0.0
[    26.867] 	Module class: X.Org Server Extension
[    26.867] 	ABI class: X.Org Server Extension, version 5.0
[    26.867] (II) Loading extension DOUBLE-BUFFER
[    26.867] (II) LoadModule: "glx"
[    26.867] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    26.899] (II) Module glx: vendor="NVIDIA Corporation"
[    26.900] 	compiled for 4.0.2, module version = 1.0.0
[    26.900] 	Module class: X.Org Server Extension
[    26.900] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    26.900] (II) Loading extension GLX
[    26.900] (II) LoadModule: "record"
[    26.900] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.900] (II) Module record: vendor="X.Org Foundation"
[    26.900] 	compiled for 1.10.1, module version = 1.13.0
[    26.900] 	Module class: X.Org Server Extension
[    26.900] 	ABI class: X.Org Server Extension, version 5.0
[    26.900] (II) Loading extension RECORD
[    26.900] (II) LoadModule: "dri"
[    26.900] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.901] (II) Module dri: vendor="X.Org Foundation"
[    26.901] 	compiled for 1.10.1, module version = 1.0.0
[    26.901] 	ABI class: X.Org Server Extension, version 5.0
[    26.901] (II) Loading extension XFree86-DRI
[    26.901] (II) LoadModule: "dri2"
[    26.901] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.901] (II) Module dri2: vendor="X.Org Foundation"
[    26.901] 	compiled for 1.10.1, module version = 1.2.0
[    26.901] 	ABI class: X.Org Server Extension, version 5.0
[    26.901] (II) Loading extension DRI2
[    26.901] (==) Matched nvidia as autoconfigured driver 0
[    26.901] (==) Matched nouveau as autoconfigured driver 1
[    26.901] (==) Matched nv as autoconfigured driver 2
[    26.901] (==) Matched vesa as autoconfigured driver 3
[    26.901] (==) Matched fbdev as autoconfigured driver 4
[    26.901] (==) Assigned the driver to the xf86ConfigLayout
[    26.901] (II) LoadModule: "nvidia"
[    26.901] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    26.902] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.902] 	compiled for 4.0.2, module version = 1.0.0
[    26.902] 	Module class: X.Org Video Driver
[    26.902] (II) LoadModule: "nouveau"
[    26.903] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    26.903] (II) Module nouveau: vendor="X.Org Foundation"
[    26.903] 	compiled for 1.10.0, module version = 0.0.16
[    26.903] 	Module class: X.Org Video Driver
[    26.903] 	ABI class: X.Org Video Driver, version 10.0
[    26.903] (II) LoadModule: "nv"
[    26.962] (WW) Warning, couldn't open module nv
[    26.962] (II) UnloadModule: "nv"
[    26.962] (II) Unloading nv
[    26.962] (EE) Failed to load module "nv" (module does not exist, 0)
[    26.962] (II) LoadModule: "vesa"
[    26.962] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.963] (II) Module vesa: vendor="X.Org Foundation"
[    26.963] 	compiled for 1.10.0, module version = 2.3.0
[    26.963] 	Module class: X.Org Video Driver
[    26.963] 	ABI class: X.Org Video Driver, version 10.0
[    26.963] (II) LoadModule: "fbdev"
[    26.963] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.963] (II) Module fbdev: vendor="X.Org Foundation"
[    26.963] 	compiled for 1.10.0, module version = 0.4.2
[    26.963] 	ABI class: X.Org Video Driver, version 10.0
[    26.963] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    26.963] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    26.963] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    26.963] (II) NOUVEAU driver for NVIDIA chipset families :
[    26.963] 	RIVA TNT    (NV04)
[    26.963] 	RIVA TNT2   (NV05)
[    26.963] 	GeForce 256 (NV10)
[    26.963] 	GeForce 2   (NV11, NV15)
[    26.964] 	GeForce 4MX (NV17, NV18)
[    26.964] 	GeForce 3   (NV20)
[    26.964] 	GeForce 4Ti (NV25, NV28)
[    26.964] 	GeForce FX  (NV3x)
[    26.964] 	GeForce 6   (NV4x)
[    26.964] 	GeForce 7   (G7x)
[    26.964] 	GeForce 8   (G8x)
[    26.964] (II) VESA: driver for VESA chipsets: vesa
[    26.964] (II) FBDEV: driver for framebuffer: fbdev
[    26.964] (++) using VT number 7

[    26.964] (II) Loading sub module "fb"
[    26.964] (II) LoadModule: "fb"
[    26.965] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.965] (II) Module fb: vendor="X.Org Foundation"
[    26.965] 	compiled for 1.10.1, module version = 1.0.0
[    26.965] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.965] (II) Loading sub module "wfb"
[    26.965] (II) LoadModule: "wfb"
[    26.965] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.965] (II) Module wfb: vendor="X.Org Foundation"
[    26.965] 	compiled for 1.10.1, module version = 1.0.0
[    26.965] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.965] (II) Loading sub module "ramdac"
[    26.965] (II) LoadModule: "ramdac"
[    26.965] (II) Module "ramdac" already built-in
[    26.965] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    26.965] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.965] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.965] (WW) Falling back to old probe method for vesa
[    26.965] (WW) Falling back to old probe method for fbdev
[    26.965] (II) Loading sub module "fbdevhw"
[    26.965] (II) LoadModule: "fbdevhw"
[    26.966] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.966] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.966] 	compiled for 1.10.1, module version = 0.0.2
[    26.966] 	ABI class: X.Org Video Driver, version 10.0
[    26.966] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.966] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    26.966] (==) NVIDIA(0): RGB weight 888
[    26.966] (==) NVIDIA(0): Default visual is TrueColor
[    26.966] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.966] (**) NVIDIA(0): Option "NoLogo" "True"
[    28.066] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    28.066] (II) NVIDIA(GPU-0):     Vision stereo.
[    28.068] (II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 (G72) at PCI:1:0:0 (GPU-0)
[    28.068] (--) NVIDIA(0): Memory: 524288 kBytes
[    28.068] (--) NVIDIA(0): VideoBIOS: 05.72.22.31.04
[    28.068] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    28.068] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    28.068] (--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0
[    28.068] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    28.068] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    28.068] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    28.069] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    28.069] (==) NVIDIA(0): 
[    28.069] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    28.069] (==) NVIDIA(0):     will be used as the requested mode.
[    28.069] (==) NVIDIA(0): 
[    28.069] (II) NVIDIA(0): Validated modes:
[    28.069] (II) NVIDIA(0):     "nvidia-auto-select"
[    28.069] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    28.070] (--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
[    28.070] (--) NVIDIA(0):     option
[    28.070] (II) UnloadModule: "nouveau"
[    28.070] (II) Unloading nouveau
[    28.070] (II) UnloadModule: "vesa"
[    28.070] (II) Unloading vesa
[    28.070] (II) UnloadModule: "fbdev"
[    28.070] (II) Unloading fbdev
[    28.070] (II) UnloadModule: "fbdevhw"
[    28.070] (II) Unloading fbdevhw
[    28.070] (--) Depth 24 pixmap format is 32 bpp
[    28.079] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    28.103] (II) Loading extension NV-GLX
[    28.135] (==) NVIDIA(0): Disabling shared memory pixmaps
[    28.135] (==) NVIDIA(0): Backing store disabled
[    28.135] (==) NVIDIA(0): Silken mouse enabled
[    28.136] (==) NVIDIA(0): DPMS enabled
[    28.136] (II) Loading extension NV-CONTROL
[    28.136] (II) Loading extension XINERAMA
[    28.136] (II) Loading sub module "dri2"
[    28.136] (II) LoadModule: "dri2"
[    28.137] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.137] (II) Module dri2: vendor="X.Org Foundation"
[    28.137] 	compiled for 1.10.1, module version = 1.2.0
[    28.137] 	ABI class: X.Org Server Extension, version 5.0
[    28.137] (II) NVIDIA(0): [DRI2] Setup complete
[    28.137] (==) RandR enabled
[    28.137] (II) Initializing built-in extension Generic Event Extension
[    28.137] (II) Initializing built-in extension SHAPE
[    28.137] (II) Initializing built-in extension MIT-SHM
[    28.137] (II) Initializing built-in extension XInputExtension
[    28.137] (II) Initializing built-in extension XTEST
[    28.137] (II) Initializing built-in extension BIG-REQUESTS
[    28.137] (II) Initializing built-in extension SYNC
[    28.137] (II) Initializing built-in extension XKEYBOARD
[    28.137] (II) Initializing built-in extension XC-MISC
[    28.137] (II) Initializing built-in extension SECURITY
[    28.137] (II) Initializing built-in extension XINERAMA
[    28.137] (II) Initializing built-in extension XFIXES
[    28.137] (II) Initializing built-in extension RENDER
[    28.137] (II) Initializing built-in extension RANDR
[    28.137] (II) Initializing built-in extension COMPOSITE
[    28.137] (II) Initializing built-in extension DAMAGE
[    28.137] (II) Initializing built-in extension GESTURE
[    28.142] (II) Initializing extension GLX
[    28.177] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.190] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    28.190] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.190] (II) LoadModule: "evdev"
[    28.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.191] (II) Module evdev: vendor="X.Org Foundation"
[    28.191] 	compiled for 1.10.0.902, module version = 2.6.0
[    28.191] 	Module class: X.Org XInput Driver
[    28.191] 	ABI class: X.Org XInput driver, version 12.3
[    28.191] (II) Using input driver 'evdev' for 'Power Button'
[    28.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.191] (**) Power Button: always reports core events
[    28.191] (**) Power Button: Device: "/dev/input/event2"
[    28.192] (--) Power Button: Found keys
[    28.192] (II) Power Button: Configuring as keyboard
[    28.192] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    28.192] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.192] (**) Option "xkb_rules" "evdev"
[    28.192] (**) Option "xkb_model" "pc105"
[    28.192] (**) Option "xkb_layout" "us"
[    28.193] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    28.193] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.193] (II) Using input driver 'evdev' for 'Video Bus'
[    28.193] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.193] (**) Video Bus: always reports core events
[    28.194] (**) Video Bus: Device: "/dev/input/event4"
[    28.194] (--) Video Bus: Found keys
[    28.194] (II) Video Bus: Configuring as keyboard
[    28.194] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5/event4"
[    28.194] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.194] (**) Option "xkb_rules" "evdev"
[    28.194] (**) Option "xkb_model" "pc105"
[    28.194] (**) Option "xkb_layout" "us"
[    28.243] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.243] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.243] (II) Using input driver 'evdev' for 'Power Button'
[    28.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.243] (**) Power Button: always reports core events
[    28.243] (**) Power Button: Device: "/dev/input/event1"
[    28.244] (--) Power Button: Found keys
[    28.244] (II) Power Button: Configuring as keyboard
[    28.244] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    28.244] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.244] (**) Option "xkb_rules" "evdev"
[    28.244] (**) Option "xkb_model" "pc105"
[    28.244] (**) Option "xkb_layout" "us"
[    28.244] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.244] (II) No input driver/identifier specified (ignoring)
[    28.254] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    28.254] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.254] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.254] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.254] (**) AT Translated Set 2 keyboard: always reports core events
[    28.254] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    28.254] (--) AT Translated Set 2 keyboard: Found keys
[    28.254] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.254] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event3"
[    28.255] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.255] (**) Option "xkb_rules" "evdev"
[    28.255] (**) Option "xkb_model" "pc105"
[    28.255] (**) Option "xkb_layout" "us"
[    28.256] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    28.256] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    28.256] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    28.256] (II) LoadModule: "synaptics"
[    28.256] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.256] (II) Module synaptics: vendor="X.Org Foundation"
[    28.256] 	compiled for 1.10.0.902, module version = 1.3.99
[    28.256] 	Module class: X.Org XInput Driver
[    28.256] 	ABI class: X.Org XInput driver, version 12.3
[    28.256] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    28.256] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.256] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    28.256] (**) Option "Device" "/dev/input/event6"
[    28.264] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    28.264] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    28.264] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    28.264] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    28.264] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    28.268] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    28.268] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    28.272] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event6"
[    28.272] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    28.272] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    28.272] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    28.272] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    28.272] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    28.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    28.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    28.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    28.284] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    28.284] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    28.284] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    28.284] (II) No input driver/identifier specified (ignoring)
[    28.292] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    28.292] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.292] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    28.292] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.292] (**) HP WMI hotkeys: always reports core events
[    28.293] (**) HP WMI hotkeys: Device: "/dev/input/event5"
[    28.293] (--) HP WMI hotkeys: Found keys
[    28.293] (II) HP WMI hotkeys: Configuring as keyboard
[    28.293] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[    28.293] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    28.293] (**) Option "xkb_rules" "evdev"
[    28.293] (**) Option "xkb_model" "pc105"
[    28.293] (**) Option "xkb_layout" "us"

---

### Post by lidex on 2011-06-10
Nvidia driver seems to be loading fine. Additional drivers doesn't always report correctly. Have you tried booting unity again?

Please, when posting blocks of text, use the code tags - # - in the editing toolbar.

---

### Post by rogue1987 on 2011-06-10
> **lidex said:**
> Nvidia driver seems to be loading fine. Additional drivers doesn't always report correctly. Have you tried booting unity again?


I haven't in a while, I'll try again tonight.

> **lidex said:**
> 
Please, when posting blocks of text, use the code tags - # - in the editing toolbar.

will do!

---

### Post by rogue1987 on 2011-06-10
No Unity and battery life is still dismal

---

### Post by Peter09 on 2011-06-11
Couple of links with solutions, might be worth a tr. The second link looks good.

[http://askubuntu.com/questions/42439/how-can-i-get-compiz-grid-working-again](http://askubuntu.com/questions/42439/how-can-i-get-compiz-grid-working-again)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492)

---

### Post by lidex on 2011-06-11
A reference for HP laptops:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing)

---

### Post by rogue1987 on 2011-06-11
> **Peter09 said:**
> Couple of links with solutions, might be worth a tr. The second link looks good.

[http://askubuntu.com/questions/42439/how-can-i-get-compiz-grid-working-again](http://askubuntu.com/questions/42439/how-can-i-get-compiz-grid-working-again)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492)

so far it appears to work, thanks for the find!

> **lidex said:**
> A reference for HP laptops:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing)

this link doesn't appear to work any more... I can see the Google cache of the index page, but can't get to any of the others.

So now on to figure out the battery issue. Thanks for your help so far guys.

---

