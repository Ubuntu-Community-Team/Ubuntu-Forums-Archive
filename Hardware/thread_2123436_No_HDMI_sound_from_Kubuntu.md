---
title: "No HDMI sound from Kubuntu"
date: 2013-03-08
forum: Hardware
---

### Post by Absolute Terror on 2013-03-08
It seems this is a common issue, but none of the fixes I could see solved this.

Using the same hardware, I got some to work in GNOME and Unity but when I boot into KDE there is nothing. 

I have an NVIDIA GeForce GT 545 with nvidia-current-updates driver installed.

---

### Post by papibe on 2013-03-08
> **Absolute Terror said:**
> ... when I boot into KDE there is nothing. 
If you are actually booting into another Linux version, the previous installs won't work in KDE (Kubuntu?).

If you meant login using the KDE desktop in the same version of the OS, let's make sure the driver is properly installed and loaded. Could you post the results of these commands?
```
apt-cache policy nvidia-current-updates

lsmod | grep -i nvidia
```
Regards.

---

### Post by Absolute Terror on 2013-03-08
Ah, sorry for not being clear. I am in fact using Kubuntu. What I meant was that on a SEPERATE install with Ubuntu my sound worked.

```
nvidia-current-updates:
  Installed: 304.64-0ubuntu0.2
  Candidate: 304.64-0ubuntu0.2
  Version table:
 *** 304.64-0ubuntu0.2 0
        500 http://mx.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.49-0ubuntu0.2 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://mx.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages

```

```

nvidia              11283521  42
```

---

### Post by papibe on 2013-03-08
Thanks,

It looks OK (installed and loaded).

Did you set your sound to use the HDMI output on the sound settings (or the KDE equivalent)?

If that is OK, could you post the content of this file?
```
/var/log/Xorg.0.log
```
Paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and post back the link.
Regards.

---

### Post by Absolute Terror on 2013-03-08
There's a lot of stuff. Which lines do you want?

---

### Post by papibe on 2013-03-08
Paste the whole file if you don't mind.

---

### Post by Absolute Terror on 2013-03-08
It won't let paste the file, perhaps it's too long?

EDIT: It seems my copy paste is broken now. I'll try to restart.

---

### Post by Absolute Terror on 2013-03-08
```
[    17.564] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    17.564] X Protocol Version 11, Revision 0
[    17.564] Build Operating System: Linux 2.6.42-34-generic x86_64 Ubuntu
[    17.564] Current Operating System: Linux HOSTNAME 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64
[    17.564] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=41d67d0b-21bc-4855-b07b-7e8c92e202de ro quiet splash vt.handoff=7
[    17.564] Build Date: 17 January 2013  06:14:10AM
[    17.564] xorg-server 2:1.11.4-0ubuntu10.11 (For technical support please see http://www.ubuntu.com/support) 
[    17.564] Current version of pixman: 0.24.4
[    17.564] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.564] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.564] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  7 20:39:26 2013
[    17.585] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.635] (==) No Layout section.  Using the first Screen section.
[    17.635] (**) |-->Screen "My Screen" (0)
[    17.635] (**) |   |-->Monitor "<default monitor>"
[    17.635] (==) No device specified for screen "My Screen".
	Using the first device section listed.
[    17.635] (**) |   |-->Device "My Card"
[    17.635] (==) No monitor specified for screen "My Screen".
	Using a default monitor configuration.
[    17.635] (==) Automatically adding devices
[    17.635] (==) Automatically enabling devices
[    17.647] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.647] 	Entry deleted from font path.
[    17.647] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    17.647] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.647] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.647] (II) Loader magic: 0x7ff9c7ab9b00
[    17.647] (II) Module ABI versions:
[    17.647] 	X.Org ANSI C Emulation: 0.4
[    17.647] 	X.Org Video Driver: 11.0
[    17.647] 	X.Org XInput driver : 16.0
[    17.647] 	X.Org Server Extension : 6.0
[    17.648] (--) PCI:*(0:1:0:0) 10de:1243:196e:0901 rev 161, Mem @ 0xfc000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    17.648] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.648] (II) LoadModule: "extmod"
[    17.653] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.661] (II) Module extmod: vendor="X.Org Foundation"
[    17.661] 	compiled for 1.11.3, module version = 1.0.0
[    17.661] 	Module class: X.Org Server Extension
[    17.661] 	ABI class: X.Org Server Extension, version 6.0
[    17.661] (II) Loading extension MIT-SCREEN-SAVER
[    17.661] (II) Loading extension XFree86-VidModeExtension
[    17.661] (II) Loading extension XFree86-DGA
[    17.661] (II) Loading extension DPMS
[    17.661] (II) Loading extension XVideo
[    17.661] (II) Loading extension XVideo-MotionCompensation
[    17.661] (II) Loading extension X-Resource
[    17.661] (II) LoadModule: "dbe"
[    17.661] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.665] (II) Module dbe: vendor="X.Org Foundation"
[    17.665] 	compiled for 1.11.3, module version = 1.0.0
[    17.665] 	Module class: X.Org Server Extension
[    17.665] 	ABI class: X.Org Server Extension, version 6.0
[    17.665] (II) Loading extension DOUBLE-BUFFER
[    17.665] (II) LoadModule: "glx"
[    17.665] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    17.754] (II) Module glx: vendor="NVIDIA Corporation"
[    17.754] 	compiled for 4.0.2, module version = 1.0.0
[    17.754] 	Module class: X.Org Server Extension
[    17.754] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[    17.755] (II) Loading extension GLX
[    17.755] (II) LoadModule: "record"
[    17.755] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.755] (II) Module record: vendor="X.Org Foundation"
[    17.755] 	compiled for 1.11.3, module version = 1.13.0
[    17.755] 	Module class: X.Org Server Extension
[    17.755] 	ABI class: X.Org Server Extension, version 6.0
[    17.755] (II) Loading extension RECORD
[    17.755] (II) LoadModule: "dri"
[    17.755] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.776] (II) Module dri: vendor="X.Org Foundation"
[    17.776] 	compiled for 1.11.3, module version = 1.0.0
[    17.776] 	ABI class: X.Org Server Extension, version 6.0
[    17.776] (II) Loading extension XFree86-DRI
[    17.776] (II) LoadModule: "dri2"
[    17.776] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.776] (II) Module dri2: vendor="X.Org Foundation"
[    17.776] 	compiled for 1.11.3, module version = 1.2.0
[    17.776] 	ABI class: X.Org Server Extension, version 6.0
[    17.776] (II) Loading extension DRI2
[    17.776] (II) LoadModule: "nvidia"
[    17.776] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.867] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.867] 	compiled for 4.0.2, module version = 1.0.0
[    17.867] 	Module class: X.Org Video Driver
[    17.932] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 10:59:51 PDT 2012
[    17.932] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.954] (++) using VT number 7

[    17.955] (II) Loading sub module "fb"
[    17.955] (II) LoadModule: "fb"
[    17.955] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.960] (II) Module fb: vendor="X.Org Foundation"
[    17.960] 	compiled for 1.11.3, module version = 1.0.0
[    17.960] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.960] (II) Loading sub module "wfb"
[    17.960] (II) LoadModule: "wfb"
[    17.960] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.963] (II) Module wfb: vendor="X.Org Foundation"
[    17.963] 	compiled for 1.11.3, module version = 1.0.0
[    17.963] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.963] (II) Loading sub module "ramdac"
[    17.963] (II) LoadModule: "ramdac"
[    17.963] (II) Module "ramdac" already built-in
[    17.985] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.985] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.985] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.986] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"My Screen" for depth/fbbpp 24/32
[    17.986] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    17.986] (==) NVIDIA(0): RGB weight 888
[    17.986] (==) NVIDIA(0): Default visual is TrueColor
[    17.986] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.986] (**) NVIDIA(0): Option "NoLogo" "True"
[    17.986] (**) NVIDIA(0): Option "RegistryDwords" "EnableBrightnessControl=1"
[    17.986] (**) NVIDIA(0): Enabling 2D acceleration
[    18.650] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    18.650] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    18.679] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    18.679] (II) NVIDIA(GPU-0):     Vision stereo.
[    18.680] (II) NVIDIA(0): NVIDIA GPU GeForce GT 545 (GF116) at PCI:1:0:0 (GPU-0)
[    18.680] (--) NVIDIA(0): Memory: 1572864 kBytes
[    18.680] (--) NVIDIA(0): VideoBIOS: 70.26.28.00.51
[    18.680] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    18.680] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    18.688] (--) NVIDIA(0): Valid display device(s) on GeForce GT 545 at PCI:1:0:0
[    18.688] (--) NVIDIA(0):     CRT-0
[    18.688] (--) NVIDIA(0):     CRT-1
[    18.688] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0) (connected)
[    18.688] (--) NVIDIA(0):     Samsung S23B550 (DFP-1) (connected)
[    18.688] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    18.688] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    18.688] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    18.688] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    18.688] (--) NVIDIA(0): Samsung S23B550 (DFP-1): 165.0 MHz maximum pixel clock
[    18.688] (--) NVIDIA(0): Samsung S23B550 (DFP-1): Internal Single Link TMDS
[    18.688] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    18.688] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    18.688] (**) NVIDIA(0):     has been enabled on all display devices.)
[    18.689] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    18.689] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    18.689] (**) NVIDIA(0):     been enabled on all display devices.)
[    18.691] (==) NVIDIA(0): 
[    18.691] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    18.691] (==) NVIDIA(0):     will be used as the requested mode.
[    18.691] (==) NVIDIA(0): 
[    18.691] (II) NVIDIA(0): Validated MetaModes:
[    18.691] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[    18.691] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1080
[    18.721] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[    18.721] (--) NVIDIA(0):     option
[    18.721] (--) Depth 24 pixmap format is 32 bpp
[    18.721] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    18.721] (II) NVIDIA:     access.
[    18.726] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[    18.798] (II) Loading extension NV-GLX
[    18.918] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.918] (==) NVIDIA(0): Backing store disabled
[    18.918] (==) NVIDIA(0): Silken mouse enabled
[    18.918] (==) NVIDIA(0): DPMS enabled
[    18.918] (II) Loading extension NV-CONTROL
[    18.918] (II) Loading extension XINERAMA
[    18.918] (II) Loading sub module "dri2"
[    18.918] (II) LoadModule: "dri2"
[    18.918] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.918] (II) Module dri2: vendor="X.Org Foundation"
[    18.918] 	compiled for 1.11.3, module version = 1.2.0
[    18.918] 	ABI class: X.Org Server Extension, version 6.0
[    18.918] (II) NVIDIA(0): [DRI2] Setup complete
[    18.918] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.918] (--) RandR disabled
[    18.918] (II) Initializing built-in extension Generic Event Extension
[    18.918] (II) Initializing built-in extension SHAPE
[    18.918] (II) Initializing built-in extension MIT-SHM
[    18.918] (II) Initializing built-in extension XInputExtension
[    18.918] (II) Initializing built-in extension XTEST
[    18.918] (II) Initializing built-in extension BIG-REQUESTS
[    18.918] (II) Initializing built-in extension SYNC
[    18.918] (II) Initializing built-in extension XKEYBOARD
[    18.918] (II) Initializing built-in extension XC-MISC
[    18.918] (II) Initializing built-in extension SECURITY
[    18.918] (II) Initializing built-in extension XINERAMA
[    18.918] (II) Initializing built-in extension XFIXES
[    18.918] (II) Initializing built-in extension RENDER
[    18.918] (II) Initializing built-in extension RANDR
[    18.918] (II) Initializing built-in extension COMPOSITE
[    18.918] (II) Initializing built-in extension DAMAGE
[    18.919] (II) Initializing extension GLX
[    18.970] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.988] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.988] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.988] (II) LoadModule: "evdev"
[    18.988] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.017] (II) Module evdev: vendor="X.Org Foundation"
[    19.017] 	compiled for 1.11.3, module version = 2.7.0
[    19.017] 	Module class: X.Org XInput Driver
[    19.017] 	ABI class: X.Org XInput driver, version 16.0
[    19.017] (II) Using input driver 'evdev' for 'Power Button'
[    19.017] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.017] (**) Power Button: always reports core events
[    19.017] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.018] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.018] (--) evdev: Power Button: Found keys
[    19.018] (II) evdev: Power Button: Configuring as keyboard
[    19.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.018] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.018] (**) Option "xkb_rules" "evdev"
[    19.018] (**) Option "xkb_model" "pc105"
[    19.018] (**) Option "xkb_layout" "us"
[    19.018] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.018] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.018] (II) Using input driver 'evdev' for 'Power Button'
[    19.018] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.018] (**) Power Button: always reports core events
[    19.018] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.018] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.018] (--) evdev: Power Button: Found keys
[    19.018] (II) evdev: Power Button: Configuring as keyboard
[    19.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    19.018] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.018] (**) Option "xkb_rules" "evdev"
[    19.018] (**) Option "xkb_model" "pc105"
[    19.018] (**) Option "xkb_layout" "us"
[    19.018] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event13)
[    19.018] (II) No input driver specified, ignoring this device.
[    19.018] (II) This device may have been added with another device file.
[    19.018] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[    19.018] (II) No input driver specified, ignoring this device.
[    19.018] (II) This device may have been added with another device file.
[    19.018] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[    19.018] (II) No input driver specified, ignoring this device.
[    19.018] (II) This device may have been added with another device file.
[    19.018] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event16)
[    19.018] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event10)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event11)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event12)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event4)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.019] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event5)
[    19.019] (II) No input driver specified, ignoring this device.
[    19.019] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[    19.020] (II) No input driver specified, ignoring this device.
[    19.020] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[    19.020] (II) No input driver specified, ignoring this device.
[    19.020] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[    19.020] (II) No input driver specified, ignoring this device.
[    19.020] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[    19.020] (II) No input driver specified, ignoring this device.
[    19.020] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[    19.020] (II) No input driver specified, ignoring this device.
[    19.020] (II) This device may have been added with another device file.
[    19.020] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/event2)
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: Applying InputClass "evdev pointer catchall"
[    19.020] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1025'
[    19.020] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: always reports core events
[    19.020] (**) evdev: Logitech Unifying Device. Wireless PID:1025: Device: "/dev/input/event2"
[    19.020] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Vendor 0x46d Product 0xc52b
[    19.020] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found 20 mouse buttons
[    19.020] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found scroll wheel(s)
[    19.020] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found relative axes
[    19.020] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found x and y relative axes
[    19.020] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Configuring as mouse
[    19.020] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Adding scrollwheel support
[    19.020] (**) evdev: Logitech Unifying Device. Wireless PID:1025: YAxisMapping: buttons 4 and 5
[    19.020] (**) evdev: Logitech Unifying Device. Wireless PID:1025: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.020] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-2/3-2.6/3-2.6:1.2/0003:046D:C52B.0003/input/input2/event2"
[    19.020] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1025" (type: MOUSE, id 8)
[    19.020] (II) evdev: Logitech Unifying Device. Wireless PID:1025: initialized for relative axes.
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: (accel) keeping acceleration scheme 1
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration profile 0
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration factor: 2.000
[    19.020] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration threshold: 4
[    19.021] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/mouse0)
[    19.021] (II) No input driver specified, ignoring this device.
[    19.021] (II) This device may have been added with another device file.
[    19.021] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4004 (/dev/input/event3)
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: Applying InputClass "evdev keyboard catchall"
[    19.021] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4004'
[    19.021] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: always reports core events
[    19.021] (**) evdev: Logitech Unifying Device. Wireless PID:4004: Device: "/dev/input/event3"
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Vendor 0x46d Product 0xc52b
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found 1 mouse buttons
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found scroll wheel(s)
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found relative axes
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing relative x/y axes to exist.
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found absolute axes
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing absolute x/y axes to exist.
[    19.021] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found keys
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as mouse
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as keyboard
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Adding scrollwheel support
[    19.021] (**) evdev: Logitech Unifying Device. Wireless PID:4004: YAxisMapping: buttons 4 and 5
[    19.021] (**) evdev: Logitech Unifying Device. Wireless PID:4004: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.021] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-2/3-2.6/3-2.6:1.2/0003:046D:C52B.0003/input/input3/event3"
[    19.021] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4004" (type: KEYBOARD, id 9)
[    19.021] (**) Option "xkb_rules" "evdev"
[    19.021] (**) Option "xkb_model" "pc105"
[    19.021] (**) Option "xkb_layout" "us"
[    19.021] (II) evdev: Logitech Unifying Device. Wireless PID:4004: initialized for relative axes.
[    19.021] (WW) evdev: Logitech Unifying Device. Wireless PID:4004: ignoring absolute axes.
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: (accel) keeping acceleration scheme 1
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration profile 0
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration factor: 2.000
[    19.021] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration threshold: 4
[    41.242] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    41.242] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    41.242] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.242] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    41.242] (**) NVIDIA(0):     has been enabled on all display devices.)
[    41.273] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    41.273] (II) NVIDIA(GPU-0):     Vision stereo.
[    41.273] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.273] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    41.273] (**) NVIDIA(0):     been enabled on all display devices.)
[    41.378] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +0+0"
[    41.480] (II) NVIDIA(0): Setting mode "DVI-I-1: 1680x1050_60_0 @1680x1050 +240+0"
[    41.548] (II) NVIDIA(0): Setting mode "DVI-I-1: 1680x1050_60_0 @1680x1050 +240+0, HDMI-0: nvidia-auto-select @1920x1080 +0+0"
[    41.701] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    41.701] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    41.701] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.701] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    41.701] (**) NVIDIA(0):     has been enabled on all display devices.)
[    41.732] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    41.732] (II) NVIDIA(GPU-0):     Vision stereo.
[    41.732] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.732] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    41.732] (**) NVIDIA(0):     been enabled on all display devices.)
[    41.782] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    41.782] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    41.782] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.782] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    41.782] (**) NVIDIA(0):     has been enabled on all display devices.)
[    41.813] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    41.813] (II) NVIDIA(GPU-0):     Vision stereo.
[    41.813] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.813] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    41.813] (**) NVIDIA(0):     been enabled on all display devices.)
[    59.870] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    59.870] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    59.870] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.870] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    59.870] (**) NVIDIA(0):     has been enabled on all display devices.)
[    59.901] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    59.901] (II) NVIDIA(GPU-0):     Vision stereo.
[    59.901] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.901] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    59.901] (**) NVIDIA(0):     been enabled on all display devices.)
[    59.953] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    59.953] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    59.953] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.953] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    59.953] (**) NVIDIA(0):     has been enabled on all display devices.)
[    59.983] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    59.983] (II) NVIDIA(GPU-0):     Vision stereo.
[    59.983] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.983] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    59.983] (**) NVIDIA(0):     been enabled on all display devices.)
[    60.432] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    60.432] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    60.432] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    60.432] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    60.432] (**) NVIDIA(0):     has been enabled on all display devices.)
[    60.464] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[    60.464] (II) NVIDIA(GPU-0):     Vision stereo.
[    60.464] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    60.464] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    60.464] (**) NVIDIA(0):     been enabled on all display devices.)
[    60.467] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   735.668] (II) Open ACPI successful (/var/run/acpid.socket)
[  1300.016] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  2806.518] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[  2806.518] (WW) NVIDIA(0):     viewport height 1050; adjusting
[  2806.518] (WW) NVIDIA(0): Specified panning domain height of 945 is smaller than
[  2806.519] (WW) NVIDIA(0):     viewport height 1050; adjusting
[  2806.682] (II) NVIDIA(0): Setting mode "DFP-0:1680x1050_60_0@1680x1050+1920+0,DFP-1:nvidia-auto-select@1920x1080+0+0"
[  2806.848] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  2806.848] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  2806.848] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2806.848] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  2806.848] (**) NVIDIA(0):     has been enabled on all display devices.)
[  2806.879] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[  2806.879] (II) NVIDIA(GPU-0):     Vision stereo.
[  2806.879] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2806.879] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[  2806.879] (**) NVIDIA(0):     been enabled on all display devices.)
[  2806.931] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  2806.931] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  2806.931] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2806.931] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  2806.931] (**) NVIDIA(0):     has been enabled on all display devices.)
[  2806.973] (II) NVIDIA(GPU-0): Display (Samsung S23B550 (DFP-1)) does not support NVIDIA 3D
[  2806.973] (II) NVIDIA(GPU-0):     Vision stereo.
[  2806.973] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2806.973] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[  2806.973] (**) NVIDIA(0):     been enabled on all display devices.)
[  2811.381] (WW) NVIDIA(0): Specified panning domain width of 1280 is smaller than
[  2811.381] (WW) NVIDIA(0):     viewport width 1680; adjusting
[  2811.381] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[  2811.381] (WW) NVIDIA(0):     viewport height 1050; adjusting
[  2811.381] (WW) NVIDIA(0): Specified panning domain height of 945 is smaller than
[  2811.381] (WW) NVIDIA(0):     viewport height 1050; adjusting
[  2811.384] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[  2811.384] (WW) NVIDIA(0):     viewport height 1050; adjusting
[  2811.384] (WW) NVIDIA(0): Specified panning domain height of 945 is smaller than
[  2811.384] (WW) NVIDIA(0):     viewport height 1050; adjusting
[ 14268.893] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

---

### Post by Annycha on 2013-03-08
I am looking for this issue too.

---

### Post by papibe on 2013-03-08
checking the log... in the meantime take a look a this: [Fixing NVIDIA HDMI Audio on Kubuntu 12.04 LTS]("http://www.dahlsys.com/misc/kubuntu_12_04_hdmi_audio/index.html").

Regards.

EDIT: do you have 4 monitors? 2 analogs and 2 digitals for what I can tell. I think the system by itself won't be able to determine which one to use as default. Take a look at the link above to explicitly set the one you want.

---

### Post by Absolute Terror on 2013-03-08
I have two monitors with support for up to 4 I believe.

I tried that fix you just posted earlier and nothing came of it. I try all of the HDMI options listed and nothing.

 EDIT: I definitely have the right sound source selected because it says 'Mixer cannot be found' on anything else.

---

### Post by SeijiSensei on 2013-03-08
Go to System Settings > Multimedia > Phonon and make sure the correct input and output devices are set as the defaults.

If that doesn't work, you may need to install [pavucontrol](http://packages.ubuntu.com/precise/pavucontrol) and check the settings that way.

---

### Post by Absolute Terror on 2013-03-08
That was covered in one of the many fixes. Everything is set to output to the correct HDMI but I still hear nothing.

---

### Post by Absolute Terror on 2013-03-10
bump

---

### Post by Absolute Terror on 2013-03-10
bump again

---

### Post by Absolute Terror on 2013-03-14
I have hooked up some USB speakers to see if sound works at all, it works when I test it in Phonon.

However, kmix crashes when I try to launch it with this error.

```
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

```

In the mixer it says "Mixer cannot be found."

---

