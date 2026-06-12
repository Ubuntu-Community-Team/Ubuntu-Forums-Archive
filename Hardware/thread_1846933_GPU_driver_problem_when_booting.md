---
title: "GPU driver problem when booting"
date: 2011-09-19
forum: Hardware
---

### Post by widggman on 2011-09-19
So, I have that stupid problem and now it's getting really annoying.

When I boot, it doesn't go to the login screen like it should. Instead, it goes in text mode and I have to login that way.

Here's the procedure that I do to manage to start the login screen:
- sudo service gdm stop
- sudo sh <NVidia Driver>
--> Accept the term and whatever then, the next screen it says that this driver is already installed and I can choose to quit the installation, so I do that (anyway, a full reinstallation doesn't solve the problem).
- sudo service gdm start

And then I have the login screen.

I want to go directly to the login screen without have to do that again. It's clearly a waste of time because the (1) driver is installed already and (2) if I don't go in the installation, I cannot restart gdm, it won't work.

So, how do I fix this ?

Thanks

W

---

### Post by widggman on 2011-09-23
I really don't know what to do!

I have the last driver from nVidia... but even if I used the last version, it doesn't work at all!

Please... help me! It's very annoying, particularly for something that has no good reason to happen because I don't need to fully reinstall the driver!

---

### Post by .... on 2011-09-23
Did you remove/blacklist nouveau?

---

### Post by widggman on 2011-09-24
What is that ?

---

### Post by varunendra on 2011-09-25
> **.... said:**
> Did you remove/blacklist nouveau?

> **widggman said:**
> What is that ?
He means to open this file: **/etc/modprobe.d/blacklist.conf**
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add this line at its bottom: **blacklist nouveau**
Then save and close the file, then either restart computer, or enter this command to remove this driver:
```
sudo rmmod nouveau
```

(I assume you have nvidia driver to take its place)

---

### Post by widggman on 2011-09-26
after I used rrmod nouveau, it says:

ERROR: Module nouveau does not exist in /proc/modules

---

### Post by varunendra on 2011-09-27
I'm no expert in graphics issue (not even an amateur troubleshooter), so my approach/suggestions may involve unnecessary and unhelpful steps. But I think the error-log is something that an expert would require too. So please post the contents of your **/var/log/Xorg.0.log** file.

Let's hope some experts find it interesting and jump in to help.

**_Edit_:**

Also, the outputs of following:
```
sudo lshw -C display
lsmod
```

---

### Post by widggman on 2011-09-27
From sudo lshw -C display

       > description: VGA compatible controller
       product: G92 [GeForce 9800 GTX+]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0

from lsmod

> Module                  Size  Used by
nvidia              11713775  40 
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
usb_storage            53538  0 
uas                    17996  0 
cdc_acm                22574  0 
snd_hda_codec_realtek   336771  1 
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18600  2 
psmouse                73535  0 
rtl8180                36351  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
mac80211              294370  1 rtl8180
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
eeprom_93cx6           12725  1 rtl8180
cfg80211              178528  2 rtl8180,mac80211
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
asus_atk0110           17976  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
atl1e                  37715  0 
pata_marvell           12905  0 

For /var/log/Xorg.0.log, I don't know if it's relevant, the date at the top of the file is from last april!

But here it is, sorry of the length:

> [  1643.102] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  1643.102] X Protocol Version 11, Revision 0
[  1643.102] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[  1643.102] Current Operating System: Linux truitebox 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[  1643.102] Kernel command line: root=UUID=9d8c6a42-1830-40c9-9d7d-7523124dd8b0 ro quiet splash 
[  1643.102] Build Date: 11 August 2011  03:43:05PM
[  1643.102] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1643.102] Current version of pixman: 0.20.2
[  1643.102] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  1643.102] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1643.102] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 27 12:28:57 2011
[  1643.103] (==) Using config file: "/etc/X11/xorg.conf"
[  1643.103] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1643.103] (==) ServerLayout "Layout0"
[  1643.103] (**) |-->Screen "Screen0" (0)
[  1643.103] (**) |   |-->Monitor "Monitor0"
[  1643.103] (**) |   |-->Device "Device0"
[  1643.103] (**) |-->Input Device "Keyboard0"
[  1643.103] (**) |-->Input Device "Mouse0"
[  1643.103] (==) Automatically adding devices
[  1643.103] (==) Automatically enabling devices
[  1643.103] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1643.103] 	Entry deleted from font path.
[  1643.103] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1643.103] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1643.103] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  1643.103] (WW) Disabling Keyboard0
[  1643.103] (WW) Disabling Mouse0
[  1643.103] (II) Loader magic: 0x7e17e0
[  1643.103] (II) Module ABI versions:
[  1643.103] 	X.Org ANSI C Emulation: 0.4
[  1643.103] 	X.Org Video Driver: 10.0
[  1643.103] 	X.Org XInput driver : 12.3
[  1643.103] 	X.Org Server Extension : 5.0
[  1643.104] (--) PCI:*(0:1:0:0) 10de:0613:0000:0000 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
[  1643.104] (II) Open ACPI successful (/var/run/acpid.socket)
[  1643.104] (II) LoadModule: "extmod"
[  1643.104] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1643.104] (II) Module extmod: vendor="X.Org Foundation"
[  1643.104] 	compiled for 1.10.1, module version = 1.0.0
[  1643.104] 	Module class: X.Org Server Extension
[  1643.104] 	ABI class: X.Org Server Extension, version 5.0
[  1643.104] (II) Loading extension MIT-SCREEN-SAVER
[  1643.104] (II) Loading extension XFree86-VidModeExtension
[  1643.104] (II) Loading extension XFree86-DGA
[  1643.104] (II) Loading extension DPMS
[  1643.104] (II) Loading extension XVideo
[  1643.104] (II) Loading extension XVideo-MotionCompensation
[  1643.104] (II) Loading extension X-Resource
[  1643.104] (II) LoadModule: "dbe"
[  1643.104] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1643.104] (II) Module dbe: vendor="X.Org Foundation"
[  1643.104] 	compiled for 1.10.1, module version = 1.0.0
[  1643.104] 	Module class: X.Org Server Extension
[  1643.104] 	ABI class: X.Org Server Extension, version 5.0
[  1643.104] (II) Loading extension DOUBLE-BUFFER
[  1643.104] (II) LoadModule: "glx"
[  1643.105] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1643.113] (II) Module glx: vendor="NVIDIA Corporation"
[  1643.113] 	compiled for 4.0.2, module version = 1.0.0
[  1643.113] 	Module class: X.Org Server Extension
[  1643.113] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[  1643.113] (II) Loading extension GLX
[  1643.113] (II) LoadModule: "record"
[  1643.113] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1643.113] (II) Module record: vendor="X.Org Foundation"
[  1643.113] 	compiled for 1.10.1, module version = 1.13.0
[  1643.113] 	Module class: X.Org Server Extension
[  1643.113] 	ABI class: X.Org Server Extension, version 5.0
[  1643.113] (II) Loading extension RECORD
[  1643.113] (II) LoadModule: "dri"
[  1643.113] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1643.113] (II) Module dri: vendor="X.Org Foundation"
[  1643.113] 	compiled for 1.10.1, module version = 1.0.0
[  1643.114] 	ABI class: X.Org Server Extension, version 5.0
[  1643.114] (II) Loading extension XFree86-DRI
[  1643.114] (II) LoadModule: "dri2"
[  1643.114] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1643.114] (II) Module dri2: vendor="X.Org Foundation"
[  1643.114] 	compiled for 1.10.1, module version = 1.2.0
[  1643.114] 	ABI class: X.Org Server Extension, version 5.0
[  1643.114] (II) Loading extension DRI2
[  1643.114] (II) LoadModule: "nvidia"
[  1643.114] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  1643.114] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1643.114] 	compiled for 4.0.2, module version = 1.0.0
[  1643.114] 	Module class: X.Org Video Driver
[  1644.079] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[  1644.079] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1644.079] (--) using VT number 8

[  1644.097] (II) Loading sub module "fb"
[  1644.097] (II) LoadModule: "fb"
[  1644.097] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1644.097] (II) Module fb: vendor="X.Org Foundation"
[  1644.097] 	compiled for 1.10.1, module version = 1.0.0
[  1644.097] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1644.097] (II) Loading sub module "wfb"
[  1644.097] (II) LoadModule: "wfb"
[  1644.098] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1644.098] (II) Module wfb: vendor="X.Org Foundation"
[  1644.098] 	compiled for 1.10.1, module version = 1.0.0
[  1644.098] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1644.098] (II) Loading sub module "ramdac"
[  1644.098] (II) LoadModule: "ramdac"
[  1644.098] (II) Module "ramdac" already built-in
[  1644.098] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  1644.098] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1644.098] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1644.098] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  1644.098] (==) NVIDIA(0): RGB weight 888
[  1644.098] (==) NVIDIA(0): Default visual is TrueColor
[  1644.098] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1644.994] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-1)) does not support NVIDIA
[  1644.994] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  1645.004] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:1:0:0 (GPU-0)
[  1645.004] (--) NVIDIA(0): Memory: 524288 kBytes
[  1645.004] (--) NVIDIA(0): VideoBIOS: 62.92.60.00.00
[  1645.004] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1645.004] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1645.004] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GTX+ at PCI:1:0:0
[  1645.004] (--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
[  1645.004] (--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
[  1645.004] (--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
[  1645.054] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[  1645.054] (**) NVIDIA(0):     enabled on all display devices.
[  1645.086] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  1645.086] (==) NVIDIA(0): 
[  1645.086] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  1645.086] (==) NVIDIA(0):     will be used as the requested mode.
[  1645.086] (==) NVIDIA(0): 
[  1645.086] (II) NVIDIA(0): Validated modes:
[  1645.086] (II) NVIDIA(0):     "nvidia-auto-select"
[  1645.086] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[  1645.121] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[  1645.121] (--) NVIDIA(0):     option
[  1645.121] (--) Depth 24 pixmap format is 32 bpp
[  1645.121] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  1645.128] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1645.174] (II) Loading extension NV-GLX
[  1645.288] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1645.288] (==) NVIDIA(0): Backing store disabled
[  1645.288] (==) NVIDIA(0): Silken mouse enabled
[  1645.291] (**) NVIDIA(0): DPMS enabled
[  1645.291] (II) Loading extension NV-CONTROL
[  1645.291] (II) Loading extension XINERAMA
[  1645.291] (II) Loading sub module "dri2"
[  1645.291] (II) LoadModule: "dri2"
[  1645.291] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1645.291] (II) Module dri2: vendor="X.Org Foundation"
[  1645.291] 	compiled for 1.10.1, module version = 1.2.0
[  1645.291] 	ABI class: X.Org Server Extension, version 5.0
[  1645.291] (II) NVIDIA(0): [DRI2] Setup complete
[  1645.291] (==) RandR enabled
[  1645.291] (II) Initializing built-in extension Generic Event Extension
[  1645.291] (II) Initializing built-in extension SHAPE
[  1645.291] (II) Initializing built-in extension MIT-SHM
[  1645.291] (II) Initializing built-in extension XInputExtension
[  1645.291] (II) Initializing built-in extension XTEST
[  1645.291] (II) Initializing built-in extension BIG-REQUESTS
[  1645.291] (II) Initializing built-in extension SYNC
[  1645.291] (II) Initializing built-in extension XKEYBOARD
[  1645.291] (II) Initializing built-in extension XC-MISC
[  1645.291] (II) Initializing built-in extension SECURITY
[  1645.291] (II) Initializing built-in extension XINERAMA
[  1645.291] (II) Initializing built-in extension XFIXES
[  1645.291] (II) Initializing built-in extension RENDER
[  1645.291] (II) Initializing built-in extension RANDR
[  1645.291] (II) Initializing built-in extension COMPOSITE
[  1645.291] (II) Initializing built-in extension DAMAGE
[  1645.291] (II) Initializing built-in extension GESTURE
[  1645.293] (II) Initializing extension GLX
[  1645.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1645.550] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1645.550] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1645.550] (II) LoadModule: "evdev"
[  1645.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1645.576] (II) Module evdev: vendor="X.Org Foundation"
[  1645.576] 	compiled for 1.10.0.902, module version = 2.6.0
[  1645.576] 	Module class: X.Org XInput Driver
[  1645.577] 	ABI class: X.Org XInput driver, version 12.3
[  1645.577] (II) Using input driver 'evdev' for 'Power Button'
[  1645.577] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1645.577] (**) Power Button: always reports core events
[  1645.577] (**) Power Button: Device: "/dev/input/event1"
[  1645.650] (--) Power Button: Found keys
[  1645.650] (II) Power Button: Configuring as keyboard
[  1645.650] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1645.650] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1645.650] (**) Option "xkb_rules" "evdev"
[  1645.650] (**) Option "xkb_model" "pc105"
[  1645.650] (**) Option "xkb_layout" "us"
[  1645.652] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1645.652] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1645.652] (II) Using input driver 'evdev' for 'Power Button'
[  1645.652] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1645.652] (**) Power Button: always reports core events
[  1645.652] (**) Power Button: Device: "/dev/input/event0"
[  1645.666] (--) Power Button: Found keys
[  1645.666] (II) Power Button: Configuring as keyboard
[  1645.666] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1645.666] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1645.666] (**) Option "xkb_rules" "evdev"
[  1645.667] (**) Option "xkb_model" "pc105"
[  1645.667] (**) Option "xkb_layout" "us"
[  1645.672] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2)
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  1645.672] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  1645.672] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
[  1645.672] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[  1645.672] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  1645.672] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[  1645.672] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  1645.672] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  1645.672] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1645.672] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input2/event2"
[  1645.672] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[  1645.672] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  1645.672] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  1645.673] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[  1645.673] (II) No input driver/identifier specified (ignoring)
[  1645.673] (II) config/udev: Adding input device LITEON Technology USB Multimedia Keyboard (/dev/input/event3)
[  1645.673] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[  1645.673] (II) Using input driver 'evdev' for 'LITEON Technology USB Multimedia Keyboard'
[  1645.673] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1645.673] (**) LITEON Technology USB Multimedia Keyboard: always reports core events
[  1645.673] (**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event3"
[  1645.673] (--) LITEON Technology USB Multimedia Keyboard: Found keys
[  1645.673] (II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
[  1645.673] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input3/event3"
[  1645.673] (II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
[  1645.673] (**) Option "xkb_rules" "evdev"
[  1645.673] (**) Option "xkb_model" "pc105"
[  1645.673] (**) Option "xkb_layout" "us"
[  1662.921] (II) NVIDIA(0): Setting mode "1680x1050_60_0"

I hope it will help!

---

### Post by varunendra on 2011-09-28
Looks like either no expert noticed or none is interested at the moment, so I guess I'll have to try a few things myself.

The date you noticed is the release date of X-server you are using (same as mine), not the date of the log itself. The log creation date is given in the 16th line (27th of Sept.), so it's quite relevant.

Now as per the log, it seems you are using an xorg.config file:
> ....
[  1643.102] (==) **Log file: "/var/log/Xorg.0.log", Time: Tue Sep 27 12:28:57 2011**
[  1643.103] (==) [COLOR=Red]**Using config file: "/etc/X11/xorg.conf"**[/COLOR]
[  1643.103] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1643.103] (==) ServerLayout "Layout0"
[  1643.103] (**) |-->Screen "Screen0" (0)
[  1643.103] (**) |   |-->Monitor "Monitor0"
[  1643.103] (**) |   |-->Device "Device0"....So please confirm if the xorg.config file exists in your **/etc/X11** directory. If it is there, please post its contents.

I am hoping either a simple editing of that file, or adding some boot parameter to the kernel boot line should solve the issue. Although it's weird why these things happen in the first place.

And something just FYI- you can use the 'code' tags (**#** symbol) instead of 'quote' tags to make the output box look smaller (with a scroll-bar) (edit your above post to see the effect). It is recommended for any log or command output. :)

---

### Post by krojew on 2011-09-28
I have the exact problem since yesterday. X.org says: EE failed to load module "nv" (module does not exist,0). I reinstalled nvidia_current (and enabled it through jockey-text) but nothing seems to help.

---

### Post by widggman on 2011-09-28
I tried to reinstall my nVidia driver and at some point, it says "The distribution-provided pre-install script failed!".

So here's the log file:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep 28 20:50:04 2011
installer version: 280.13

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 280.13.
-> There appears to already be a driver installed on your system (version: 280.
   13).  As part of installing this driver (version: 280.13), the existing driv
   er will be uninstalled.  Are you sure you want to continue? ('no' will abort
   installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: No)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by widggman on 2011-09-28
here's the content of /etc/X11/xorg.conf

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Wed Jul 27 17:15:58 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by D0natell0 on 2011-09-29
I think it would also help to see the contents of "/var/log/nvidia-installer.log"
Thanks.

---

### Post by varunendra on 2011-09-29
I'm out of ideas at the moment, so please do what *D0natell0* suggested. Also, have you tried booting in 'Safe graphics' mode (via grub 'recovery' menu)? Does it allow to boot into GUI or is same as normal booting?

---

### Post by widggman on 2011-09-29
> **D0natell0 said:**
> I think it would also help to see the contents of "/var/log/nvidia-installer.log"
Thanks.

It's the content of the log file that I put above!

Thanks!

---

### Post by varunendra on 2011-09-29
> **widggman said:**
> It's the content of the log file that I put above!

Thanks!
Totally missed it !!:(

However, I couldn't find any hint there either. So please confirm how does safe graphics mode behave. AFAIK, it uses 'Driver=Vesa' mode, so nvidia shouldn't interfere.

---

### Post by widggman on 2011-09-29
just to be sure... you suggest that I boot in safe mode and check what happen... will I have any log file or feedbacks from that ?

I never had to boot in safe mode before with Ubuntu (with Windows... too much)!

---

### Post by varunendra on 2011-09-30
You won't get any error-specific logs there. But if you can boot normally in that mode, it will be confirmed that the problem is nvidia driver-specific, and not gdm itself. A google recent search suggested that there may be many reasons for the error, and solutions may vary accordingly.

---

### Post by widggman on 2011-10-11
So, I download the new driver from nVidia, 285.05.09 and even with that one, I still have the same problem. The installation script failed and so on!

So, it's not a driver problem. Or it is, but something else makes the installation script fails. I don't know if it can be related to that package "nvidia-current" ?

---

