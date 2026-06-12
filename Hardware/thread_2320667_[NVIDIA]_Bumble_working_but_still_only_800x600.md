---
title: "[NVIDIA] Bumble working but still only 800x600"
date: 2016-04-16
forum: Hardware
---

### Post by Yoofz0ra on 2016-04-16
Hi,

I bought myself a new Asus ROG G552VW-DM266T with a Nvidia GeForce GTX 960M.
The graphic card has the optimus prime technology and after a lot of sweat I finally managed to get Bumblebee working but I'm still stuck at 800x600..

```
xrandr --verbose

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 (0x17f) normal (normal) 0mm x 0mm
    Identifier: 0x17e
    Timestamp:  3552
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  800x600 (0x17f)   36.0MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz
        v: height  600 start    0 end    0 total  600           clock   75.0Hz
```

```
lspci | egrep 'VGA|3D'

00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev ff)
```

I already searched for "Failed to get size of gamma for output default" but I don't find anything relevant to bumblebee..
Hope someone can help me :/
If there is anything else needed, I will add it.

Regards,
Morgan

---

### Post by Bashing-om on 2016-04-16
Yoofz0ra; Hello; Welcome to the forum.

BumbleBee is depreciated, I do not know how well it is maintained ; Would you consider using nvidia-prime to control the graphic's sets ?

This would entail purging BumbleBee, the Nvidia drivers, and most likely for the GeForce GTX 960M card, installing the appropriate driver from our trusted PPA and the control utility .

[INDENT][INDENT]hey, it is a thought
[/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-16
Hi Bashing-om,

Yes I already tried nvidia-prime but I will try again.
I will keep you posted.
Thank you!

Regards,
Morgan

---

### Post by Bashing-om on 2016-04-16
Yoofz0ra; K,

It you are at all uncertain as to the procedure to purge and re-install .. we are here to guide and assist.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-17
Hi,

So I deleted bumblebee & nvidia like this:

sudo apt-get purge bumblebee* primus libvdpau-va-gl1
sudo apt-get purge nvidia*

I installed prime:
sudo apt-get install nvidia-352 nvidia-prime mesa-utils
(nvidia-352 was the only one working with bumblebee)

I rebooted and I now I can't log in anymore. :) (only tty1 & tty2)

My Xorg.0.log file:

```
[   515.006] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[   515.006] X Protocol Version 11, Revision 0
[   515.006] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[   515.006] Current Operating System: Linux mhautman 3.16.0-70-generic #90~14.04.1-Ubuntu SMP Wed Apr 6 22:56:34 UTC 2016 x86_64
[   515.006] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-70-generic.efi.signed root=UUID=af234c39-db20-421a-87c0-d0278b4203f3 ro quiet splash vt.handoff=7
[   515.006] Build Date: 12 February 2015  11:11:26PM
[   515.006] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[   515.006] Current version of pixman: 0.30.2
[   515.006]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   515.006] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   515.006] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 17 19:54:12 2016
[   515.006] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   515.006] (==) No Layout section.  Using the first Screen section.
[   515.006] (==) No screen section available. Using defaults.
[   515.006] (**) |-->Screen "Default Screen Section" (0)
[   515.006] (**) |   |-->Monitor "<default monitor>"
[   515.006] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   515.006] (==) Automatically adding devices
[   515.006] (==) Automatically enabling devices
[   515.006] (==) Automatically adding GPU devices
[   515.006] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   515.006]     Entry deleted from font path.
[   515.006] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   515.006]     Entry deleted from font path.
[   515.006] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   515.006]     Entry deleted from font path.
[   515.006] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   515.006]     Entry deleted from font path.
[   515.006] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   515.006]     Entry deleted from font path.
[   515.006] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   515.006] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   515.006] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   515.006] (II) Loader magic: 0x7f36a8b98c80
[   515.006] (II) Module ABI versions:
[   515.006]     X.Org ANSI C Emulation: 0.4
[   515.006]     X.Org Video Driver: 18.0
[   515.006]     X.Org XInput driver : 21.0
[   515.006]     X.Org Server Extension : 8.0
[   515.007] (II) xfree86: Adding drm device (/dev/dri/card0)
[   515.008] (--) PCI:*(0:0:2:0) 8086:191b:1043:1c5d rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[   515.008] (--) PCI: (0:1:0:0) 10de:139b:1043:1c5d rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   515.008] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   515.008] (II) "glx" will be loaded by default.
[   515.008] (II) LoadModule: "glx"
[   515.008] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   515.014] (II) Module glx: vendor="NVIDIA Corporation"
[   515.014]     compiled for 4.0.2, module version = 1.0.0
[   515.014]     Module class: X.Org Server Extension
[   515.014] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[   515.014] (==) Matched nvidia as autoconfigured driver 0
[   515.014] (==) Matched nouveau as autoconfigured driver 1
[   515.014] (==) Matched intel as autoconfigured driver 2
[   515.014] (==) Matched modesetting as autoconfigured driver 3
[   515.014] (==) Matched fbdev as autoconfigured driver 4
[   515.014] (==) Matched vesa as autoconfigured driver 5
[   515.014] (==) Assigned the driver to the xf86ConfigLayout
[   515.014] (II) LoadModule: "nvidia"
[   515.014] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   515.014] (II) Module nvidia: vendor="NVIDIA Corporation"
[   515.014]     compiled for 4.0.2, module version = 1.0.0
[   515.014]     Module class: X.Org Video Driver
[   515.014] (II) LoadModule: "nouveau"
[   515.014] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   515.014] (II) Module nouveau: vendor="X.Org Foundation"
[   515.014]     compiled for 1.16.0, module version = 1.0.11
[   515.014]     Module class: X.Org Video Driver
[   515.014]     ABI class: X.Org Video Driver, version 18.0
[   515.014] (II) LoadModule: "intel"
[   515.014] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   515.014] (II) Module intel: vendor="X.Org Foundation"
[   515.014]     compiled for 1.16.0, module version = 2.99.914
[   515.014]     Module class: X.Org Video Driver
[   515.014]     ABI class: X.Org Video Driver, version 18.0
[   515.014] (II) LoadModule: "modesetting"
[   515.015] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   515.015] (II) Module modesetting: vendor="X.Org Foundation"
[   515.015]     compiled for 1.16.0, module version = 0.9.0
[   515.015]     Module class: X.Org Video Driver
[   515.015]     ABI class: X.Org Video Driver, version 18.0
[   515.015] (II) LoadModule: "fbdev"
[   515.015] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   515.015] (II) Module fbdev: vendor="X.Org Foundation"
[   515.015]     compiled for 1.16.0, module version = 0.4.4
[   515.015]     Module class: X.Org Video Driver
[   515.015]     ABI class: X.Org Video Driver, version 18.0
[   515.015] (II) LoadModule: "vesa"
[   515.015] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   515.015] (II) Module vesa: vendor="X.Org Foundation"
[   515.015]     compiled for 1.16.0, module version = 2.3.3
[   515.015]     Module class: X.Org Video Driver
[   515.015]     ABI class: X.Org Video Driver, version 18.0
[   515.015] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[   515.015] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   515.015] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[   515.015] (II) NOUVEAU driver for NVIDIA chipset families :
[   515.015]     RIVA TNT        (NV04)
[   515.015]     RIVA TNT2       (NV05)
[   515.015]     GeForce 256     (NV10)
[   515.015]     GeForce 2       (NV11, NV15)
[   515.015]     GeForce 4MX     (NV17, NV18)
[   515.015]     GeForce 3       (NV20)
[   515.015]     GeForce 4Ti     (NV25, NV28)
[   515.015]     GeForce FX      (NV3x)
[   515.015]     GeForce 6       (NV4x)
[   515.015]     GeForce 7       (G7x)
[   515.015]     GeForce 8       (G8x)
[   515.015]     GeForce GTX 200 (NVA0)
[   515.015]     GeForce GTX 400 (NVC0)
[   515.015] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   515.015] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   515.015] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   515.015] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   515.015] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   515.015] (II) FBDEV: driver for framebuffer: fbdev
[   515.015] (II) VESA: driver for VESA chipsets: vesa
[   515.015] (++) using VT number 7

[   515.015] (EE) [drm] KMS not enabled
[   515.015] (EE) [drm] KMS not enabled
[   515.018] (WW) Falling back to old probe method for modesetting
[   515.018] (II) Loading sub module "fbdevhw"
[   515.018] (II) LoadModule: "fbdevhw"
[   515.018] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   515.018] (II) Module fbdevhw: vendor="X.Org Foundation"
[   515.018]     compiled for 1.16.0, module version = 0.0.2
[   515.018]     ABI class: X.Org Video Driver, version 18.0
[   515.018] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[   515.018] (II) FBDEV(1): using default device
[   515.018] (WW) Falling back to old probe method for vesa
[   515.018] (EE) Screen 0 deleted because of no matching config section.
[   515.018] (II) UnloadModule: "modesetting"
[   515.018] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   515.018] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   515.018] (==) FBDEV(0): RGB weight 888
[   515.018] (==) FBDEV(0): Default visual is TrueColor
[   515.018] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   515.018] (II) FBDEV(0): hardware: EFI VGA (video memory: 1876kB)
[   515.018] (II) FBDEV(0): checking modes against framebuffer device...
[   515.018] (II) FBDEV(0): checking modes against monitor...
[   515.018] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[   515.018] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[   515.018] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[   515.018] (==) FBDEV(0): DPI set to (96, 96)
[   515.018] (II) Loading sub module "fb"
[   515.018] (II) LoadModule: "fb"
[   515.018] (II) Loading /usr/lib/xorg/modules/libfb.so
[   515.018] (II) Module fb: vendor="X.Org Foundation"
[   515.018]     compiled for 1.16.0, module version = 1.0.0
[   515.018]     ABI class: X.Org ANSI C Emulation, version 0.4
[   515.018] (**) FBDEV(0): using shadow framebuffer
[   515.018] (II) Loading sub module "shadow"
[   515.018] (II) LoadModule: "shadow"
[   515.018] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   515.018] (II) Module shadow: vendor="X.Org Foundation"
[   515.018]     compiled for 1.16.0, module version = 1.1.0
[   515.018]     ABI class: X.Org ANSI C Emulation, version 0.4
[   515.018] (II) UnloadModule: "nvidia"
[   515.018] (II) Unloading nvidia
[   515.018] (II) UnloadModule: "vesa"
[   515.018] (II) Unloading vesa
[   515.018] (==) Depth 24 pixmap format is 32 bpp
[   515.018] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   515.018] (==) FBDEV(0): Backing store enabled
[   515.018] (==) FBDEV(0): DPMS enabled
[   515.018] (==) RandR enabled
[   515.021] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   515.025] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   515.026] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   515.026] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   515.026] (II) LoadModule: "evdev"
[   515.026] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   515.026] (II) Module evdev: vendor="X.Org Foundation"
[   515.026]     compiled for 1.16.0, module version = 2.9.0
[   515.026]     Module class: X.Org XInput Driver
[   515.026]     ABI class: X.Org XInput driver, version 21.0
[   515.026] (II) Using input driver 'evdev' for 'Power Button'
[   515.026] (**) Power Button: always reports core events
[   515.026] (**) evdev: Power Button: Device: "/dev/input/event2"
[   515.026] (--) evdev: Power Button: Vendor 0 Product 0x1
[   515.026] (--) evdev: Power Button: Found keys
[   515.026] (II) evdev: Power Button: Configuring as keyboard
[   515.026] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   515.026] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   515.026] (**) Option "xkb_rules" "evdev"
[   515.026] (**) Option "xkb_model" "pc105"
[   515.026] (**) Option "xkb_layout" "be"
[   515.027] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[   515.027] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   515.028] (II) No input driver specified, ignoring this device.
[   515.028] (II) This device may have been added with another device file.
[   515.028] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   515.028] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   515.028] (II) Using input driver 'evdev' for 'Sleep Button'
[   515.028] (**) Sleep Button: always reports core events
[   515.028] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   515.028] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   515.028] (--) evdev: Sleep Button: Found keys
[   515.028] (II) evdev: Sleep Button: Configuring as keyboard
[   515.028] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[   515.028] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[   515.028] (**) Option "xkb_rules" "evdev"
[   515.028] (**) Option "xkb_model" "pc105"
[   515.028] (**) Option "xkb_layout" "be"
[   515.028] (II) config/udev: Adding input device USB2.0 HD UVC WebCam (/dev/input/event4)
[   515.028] (**) USB2.0 HD UVC WebCam: Applying InputClass "evdev keyboard catchall"
[   515.028] (II) Using input driver 'evdev' for 'USB2.0 HD UVC WebCam'
[   515.028] (**) USB2.0 HD UVC WebCam: always reports core events
[   515.028] (**) evdev: USB2.0 HD UVC WebCam: Device: "/dev/input/event4"
[   515.028] (--) evdev: USB2.0 HD UVC WebCam: Vendor 0x4f2 Product 0xb424
[   515.028] (--) evdev: USB2.0 HD UVC WebCam: Found keys
[   515.028] (II) evdev: USB2.0 HD UVC WebCam: Configuring as keyboard
[   515.028] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input4/event4"
[   515.028] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam" (type: KEYBOARD, id 8)
[   515.028] (**) Option "xkb_rules" "evdev"
[   515.028] (**) Option "xkb_model" "pc105"
[   515.028] (**) Option "xkb_layout" "be"
[   515.028] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[   515.028] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   515.028] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[   515.028] (**) Logitech USB Receiver: always reports core events
[   515.028] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event7"
[   515.028] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[   515.028] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[   515.028] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[   515.028] (--) evdev: Logitech USB Receiver: Found relative axes
[   515.028] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[   515.028] (II) evdev: Logitech USB Receiver: Configuring as mouse
[   515.028] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[   515.028] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   515.028] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   515.028] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:046D:C52F.0001/input/input7/event7"
[   515.028] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[   515.028] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[   515.028] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[   515.028] (**) Logitech USB Receiver: (accel) acceleration profile 0
[   515.028] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[   515.028] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[   515.029] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[   515.029] (II) No input driver specified, ignoring this device.
[   515.029] (II) This device may have been added with another device file.
[   515.029] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[   515.029] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   515.029] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[   515.029] (**) Logitech USB Receiver: always reports core events
[   515.029] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event8"
[   515.029] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[   515.029] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[   515.029] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[   515.029] (--) evdev: Logitech USB Receiver: Found relative axes
[   515.029] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[   515.029] (--) evdev: Logitech USB Receiver: Found absolute axes
[   515.029] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[   515.029] (--) evdev: Logitech USB Receiver: Found keys
[   515.029] (II) evdev: Logitech USB Receiver: Configuring as mouse
[   515.029] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[   515.029] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[   515.029] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   515.029] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   515.029] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:046D:C52F.0002/input/input8/event8"
[   515.029] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[   515.029] (**) Option "xkb_rules" "evdev"
[   515.029] (**) Option "xkb_model" "pc105"
[   515.029] (**) Option "xkb_layout" "be"
[   515.029] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[   515.029] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[   515.029] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[   515.029] (**) Logitech USB Receiver: (accel) acceleration profile 0
[   515.029] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[   515.029] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[   515.029] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event5)
[   515.029] (II) No input driver specified, ignoring this device.
[   515.029] (II) This device may have been added with another device file.
[   515.029] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event6)
[   515.029] (II) No input driver specified, ignoring this device.
[   515.029] (II) This device may have been added with another device file.
[   515.029] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event9)
[   515.029] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   515.029] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[   515.029] (**) Asus WMI hotkeys: always reports core events
[   515.029] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event9"
[   515.029] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[   515.029] (--) evdev: Asus WMI hotkeys: Found keys
[   515.029] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[   515.029] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input9/event9"
[   515.029] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[   515.029] (**) Option "xkb_rules" "evdev"
[   515.029] (**) Option "xkb_model" "pc105"
[   515.029] (**) Option "xkb_layout" "be"
[   515.030] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   515.030] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   515.030] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   515.030] (**) AT Translated Set 2 keyboard: always reports core events
[   515.030] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   515.030] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   515.030] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   515.030] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   515.030] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   515.030] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   515.030] (**) Option "xkb_rules" "evdev"
[   515.030] (**) Option "xkb_model" "pc105"
[   515.030] (**) Option "xkb_layout" "be"
[   515.031] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

Help?

Regards,
Morgan

---

### Post by Bashing-om on 2016-04-17
Yoofz0ra; Well ... well ...

we have:
> 
515.008] (--) PCI:*(0:0:2:0) 8086:191b:1043:1c5d rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[   515.008] (--) PCI: (0:1:0:0) 10de:139b:1043:1c5d rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   515.008]

The graphic's hardware identified .

Drivers for both Nvidia (352) and Intel are found .... But:
> 
 515.018] (**) FBDEV(1): claimed PCI slot 0@0:2:0


Huh ??? Why now is the frame buffer driver grabbing the Nvidia slot 0:2:0 ??

And now:
> 
515.018] (II) UnloadModule: "nvidia"

 515.021] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

The Nvidia driver does not build .

Let's try this:
```

sudo rm /etc/X11/xorg.conf
sudo apt remove nvidia-*
sudo ubuntu-drivers autoinstall

```

See what the system chooses to install ... be advised .. in hybrid graphics systems with the GTX 9xxxx series .. the better success I have seen is with the 361 version driver as advised by Nvidia:
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)

If you want to go this route, and
If you are running an older (14.04) release, we will obtain this driver from our trusted PPA  if the 352 version driver still does not work out.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-18
Hi Bashing-om,

I tried what you said and still the same behavior.

He still installs nvidia-352..

I'm on version 14.04.4 LTS btw.

Xorg.log

```
[  1876.327] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[  1876.327] X Protocol Version 11, Revision 0
[  1876.327] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[  1876.327] Current Operating System: Linux mhautman 3.16.0-70-generic #90~14.04.1-Ubuntu SMP Wed Apr 6 22:56:34 UTC 2016 x86_64
[  1876.327] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-70-generic.efi.signed root=UUID=af234c39-db20-421a-87c0-d0278b4203f3 ro quiet splash vt.handoff=7
[  1876.327] Build Date: 12 February 2015  11:11:26PM
[  1876.327] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1876.327] Current version of pixman: 0.30.2
[  1876.327]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1876.327] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1876.327] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 18 16:48:12 2016
[  1876.327] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1876.327] (==) No Layout section.  Using the first Screen section.
[  1876.327] (==) No screen section available. Using defaults.
[  1876.327] (**) |-->Screen "Default Screen Section" (0)
[  1876.327] (**) |   |-->Monitor "<default monitor>"
[  1876.327] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1876.327] (==) Automatically adding devices
[  1876.327] (==) Automatically enabling devices
[  1876.327] (==) Automatically adding GPU devices
[  1876.327] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1876.327]     Entry deleted from font path.
[  1876.327] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1876.327]     Entry deleted from font path.
[  1876.327] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1876.327]     Entry deleted from font path.
[  1876.327] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1876.327]     Entry deleted from font path.
[  1876.327] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1876.327]     Entry deleted from font path.
[  1876.327] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1876.327] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1876.327] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1876.327] (II) Loader magic: 0x7f55cda44c80
[  1876.327] (II) Module ABI versions:
[  1876.327]     X.Org ANSI C Emulation: 0.4
[  1876.327]     X.Org Video Driver: 18.0
[  1876.327]     X.Org XInput driver : 21.0
[  1876.327]     X.Org Server Extension : 8.0
[  1876.328] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1876.329] (--) PCI:*(0:0:2:0) 8086:191b:1043:1c5d rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[  1876.329] (--) PCI: (0:1:0:0) 10de:139b:1043:1c5d rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  1876.329] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  1876.329] (II) "glx" will be loaded by default.
[  1876.329] (II) LoadModule: "glx"
[  1876.330] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  1876.336] (II) Module glx: vendor="NVIDIA Corporation"
[  1876.336]     compiled for 4.0.2, module version = 1.0.0
[  1876.336]     Module class: X.Org Server Extension
[  1876.336] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[  1876.336] (==) Matched nvidia as autoconfigured driver 0
[  1876.336] (==) Matched nouveau as autoconfigured driver 1
[  1876.336] (==) Matched intel as autoconfigured driver 2
[  1876.336] (==) Matched modesetting as autoconfigured driver 3
[  1876.336] (==) Matched fbdev as autoconfigured driver 4
[  1876.336] (==) Matched vesa as autoconfigured driver 5
[  1876.336] (==) Assigned the driver to the xf86ConfigLayout
[  1876.336] (II) LoadModule: "nvidia"
[  1876.336] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1876.336] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1876.336]     compiled for 4.0.2, module version = 1.0.0
[  1876.336]     Module class: X.Org Video Driver
[  1876.337] (II) LoadModule: "nouveau"
[  1876.337] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1876.337] (II) Module nouveau: vendor="X.Org Foundation"
[  1876.337]     compiled for 1.16.0, module version = 1.0.11
[  1876.337]     Module class: X.Org Video Driver
[  1876.337]     ABI class: X.Org Video Driver, version 18.0
[  1876.337] (II) LoadModule: "intel"
[  1876.337] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1876.337] (II) Module intel: vendor="X.Org Foundation"
[  1876.337]     compiled for 1.16.0, module version = 2.99.914
[  1876.337]     Module class: X.Org Video Driver
[  1876.337]     ABI class: X.Org Video Driver, version 18.0
[  1876.337] (II) LoadModule: "modesetting"
[  1876.337] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1876.337] (II) Module modesetting: vendor="X.Org Foundation"
[  1876.337]     compiled for 1.16.0, module version = 0.9.0
[  1876.337]     Module class: X.Org Video Driver
[  1876.337]     ABI class: X.Org Video Driver, version 18.0
[  1876.337] (II) LoadModule: "fbdev"
[  1876.337] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1876.337] (II) Module fbdev: vendor="X.Org Foundation"
[  1876.337]     compiled for 1.16.0, module version = 0.4.4
[  1876.337]     Module class: X.Org Video Driver
[  1876.337]     ABI class: X.Org Video Driver, version 18.0
[  1876.337] (II) LoadModule: "vesa"
[  1876.337] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1876.338] (II) Module vesa: vendor="X.Org Foundation"
[  1876.338]     compiled for 1.16.0, module version = 2.3.3
[  1876.338]     Module class: X.Org Video Driver
[  1876.338]     ABI class: X.Org Video Driver, version 18.0
[  1876.338] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[  1876.338] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1876.338] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[  1876.338] (II) NOUVEAU driver for NVIDIA chipset families :
[  1876.338]     RIVA TNT        (NV04)
[  1876.338]     RIVA TNT2       (NV05)
[  1876.338]     GeForce 256     (NV10)
[  1876.338]     GeForce 2       (NV11, NV15)
[  1876.338]     GeForce 4MX     (NV17, NV18)
[  1876.338]     GeForce 3       (NV20)
[  1876.338]     GeForce 4Ti     (NV25, NV28)
[  1876.338]     GeForce FX      (NV3x)
[  1876.338]     GeForce 6       (NV4x)
[  1876.338]     GeForce 7       (G7x)
[  1876.338]     GeForce 8       (G8x)
[  1876.338]     GeForce GTX 200 (NVA0)
[  1876.338]     GeForce GTX 400 (NVC0)
[  1876.338] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  1876.338] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[  1876.338] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[  1876.338] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[  1876.338] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1876.338] (II) FBDEV: driver for framebuffer: fbdev
[  1876.338] (II) VESA: driver for VESA chipsets: vesa
[  1876.338] (++) using VT number 7

[  1876.338] (EE) [drm] KMS not enabled
[  1876.338] (EE) [drm] KMS not enabled
[  1876.341] (WW) Falling back to old probe method for modesetting
[  1876.341] (II) Loading sub module "fbdevhw"
[  1876.341] (II) LoadModule: "fbdevhw"
[  1876.341] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1876.341] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1876.341]     compiled for 1.16.0, module version = 0.0.2
[  1876.341]     ABI class: X.Org Video Driver, version 18.0
[  1876.341] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[  1876.341] (II) FBDEV(1): using default device
[  1876.341] (WW) Falling back to old probe method for vesa
[  1876.341] (EE) Screen 0 deleted because of no matching config section.
[  1876.341] (II) UnloadModule: "modesetting"
[  1876.341] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1876.341] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[  1876.341] (==) FBDEV(0): RGB weight 888
[  1876.341] (==) FBDEV(0): Default visual is TrueColor
[  1876.341] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[  1876.341] (II) FBDEV(0): hardware: EFI VGA (video memory: 1876kB)
[  1876.341] (II) FBDEV(0): checking modes against framebuffer device...
[  1876.341] (II) FBDEV(0): checking modes against monitor...
[  1876.341] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[  1876.341] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[  1876.341] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[  1876.341] (==) FBDEV(0): DPI set to (96, 96)
[  1876.341] (II) Loading sub module "fb"
[  1876.341] (II) LoadModule: "fb"
[  1876.342] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1876.342] (II) Module fb: vendor="X.Org Foundation"
[  1876.342]     compiled for 1.16.0, module version = 1.0.0
[  1876.342]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1876.342] (**) FBDEV(0): using shadow framebuffer
[  1876.342] (II) Loading sub module "shadow"
[  1876.342] (II) LoadModule: "shadow"
[  1876.342] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  1876.342] (II) Module shadow: vendor="X.Org Foundation"
[  1876.342]     compiled for 1.16.0, module version = 1.1.0
[  1876.342]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1876.342] (II) UnloadModule: "nvidia"
[  1876.342] (II) Unloading nvidia
[  1876.342] (II) UnloadModule: "vesa"
[  1876.342] (II) Unloading vesa
[  1876.342] (==) Depth 24 pixmap format is 32 bpp
[  1876.342] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[  1876.342] (==) FBDEV(0): Backing store enabled
[  1876.342] (==) FBDEV(0): DPMS enabled
[  1876.342] (==) RandR enabled
[  1876.346] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  1876.351] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1876.352] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1876.352] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1876.352] (II) LoadModule: "evdev"
[  1876.353] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1876.353] (II) Module evdev: vendor="X.Org Foundation"
[  1876.353]     compiled for 1.16.0, module version = 2.9.0
[  1876.353]     Module class: X.Org XInput Driver
[  1876.353]     ABI class: X.Org XInput driver, version 21.0
[  1876.353] (II) Using input driver 'evdev' for 'Power Button'
[  1876.353] (**) Power Button: always reports core events
[  1876.353] (**) evdev: Power Button: Device: "/dev/input/event2"
[  1876.353] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1876.353] (--) evdev: Power Button: Found keys
[  1876.353] (II) evdev: Power Button: Configuring as keyboard
[  1876.353] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1876.353] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1876.353] (**) Option "xkb_rules" "evdev"
[  1876.353] (**) Option "xkb_model" "pc105"
[  1876.353] (**) Option "xkb_layout" "be"
[  1876.354] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[  1876.354] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1876.354] (II) No input driver specified, ignoring this device.
[  1876.354] (II) This device may have been added with another device file.
[  1876.354] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  1876.354] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1876.354] (II) Using input driver 'evdev' for 'Sleep Button'
[  1876.354] (**) Sleep Button: always reports core events
[  1876.354] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  1876.354] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  1876.354] (--) evdev: Sleep Button: Found keys
[  1876.354] (II) evdev: Sleep Button: Configuring as keyboard
[  1876.354] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  1876.354] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[  1876.354] (**) Option "xkb_rules" "evdev"
[  1876.354] (**) Option "xkb_model" "pc105"
[  1876.354] (**) Option "xkb_layout" "be"
[  1876.355] (II) config/udev: Adding input device USB2.0 HD UVC WebCam (/dev/input/event4)
[  1876.355] (**) USB2.0 HD UVC WebCam: Applying InputClass "evdev keyboard catchall"
[  1876.355] (II) Using input driver 'evdev' for 'USB2.0 HD UVC WebCam'
[  1876.355] (**) USB2.0 HD UVC WebCam: always reports core events
[  1876.355] (**) evdev: USB2.0 HD UVC WebCam: Device: "/dev/input/event4"
[  1876.355] (--) evdev: USB2.0 HD UVC WebCam: Vendor 0x4f2 Product 0xb424
[  1876.355] (--) evdev: USB2.0 HD UVC WebCam: Found keys
[  1876.355] (II) evdev: USB2.0 HD UVC WebCam: Configuring as keyboard
[  1876.355] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input4/event4"
[  1876.355] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam" (type: KEYBOARD, id 8)
[  1876.355] (**) Option "xkb_rules" "evdev"
[  1876.355] (**) Option "xkb_model" "pc105"
[  1876.355] (**) Option "xkb_layout" "be"
[  1876.355] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  1876.355] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  1876.355] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  1876.355] (**) Logitech USB Receiver: always reports core events
[  1876.355] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event8"
[  1876.355] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[  1876.355] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[  1876.355] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[  1876.355] (--) evdev: Logitech USB Receiver: Found relative axes
[  1876.355] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[  1876.355] (II) evdev: Logitech USB Receiver: Configuring as mouse
[  1876.355] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[  1876.355] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  1876.355] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1876.355] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:046D:C52F.0001/input/input8/event8"
[  1876.355] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[  1876.355] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[  1876.355] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  1876.355] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  1876.355] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  1876.355] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  1876.355] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  1876.355] (II) No input driver specified, ignoring this device.
[  1876.355] (II) This device may have been added with another device file.
[  1876.355] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[  1876.355] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  1876.355] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  1876.355] (**) Logitech USB Receiver: always reports core events
[  1876.355] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event9"
[  1876.355] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[  1876.356] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[  1876.356] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[  1876.356] (--) evdev: Logitech USB Receiver: Found relative axes
[  1876.356] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[  1876.356] (--) evdev: Logitech USB Receiver: Found absolute axes
[  1876.356] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[  1876.356] (--) evdev: Logitech USB Receiver: Found keys
[  1876.356] (II) evdev: Logitech USB Receiver: Configuring as mouse
[  1876.356] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[  1876.356] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[  1876.356] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  1876.356] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1876.356] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:046D:C52F.0002/input/input9/event9"
[  1876.356] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[  1876.356] (**) Option "xkb_rules" "evdev"
[  1876.356] (**) Option "xkb_model" "pc105"
[  1876.356] (**) Option "xkb_layout" "be"
[  1876.356] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[  1876.356] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[  1876.356] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  1876.356] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  1876.356] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  1876.356] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  1876.356] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event5)
[  1876.356] (II) No input driver specified, ignoring this device.
[  1876.356] (II) This device may have been added with another device file.
[  1876.356] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event6)
[  1876.356] (II) No input driver specified, ignoring this device.
[  1876.356] (II) This device may have been added with another device file.
[  1876.356] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event7)
[  1876.356] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  1876.356] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[  1876.356] (**) Asus WMI hotkeys: always reports core events
[  1876.356] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event7"
[  1876.356] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[  1876.356] (--) evdev: Asus WMI hotkeys: Found keys
[  1876.356] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[  1876.356] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input7/event7"
[  1876.356] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[  1876.356] (**) Option "xkb_rules" "evdev"
[  1876.356] (**) Option "xkb_model" "pc105"
[  1876.356] (**) Option "xkb_layout" "be"
[  1876.356] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1876.356] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1876.356] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1876.356] (**) AT Translated Set 2 keyboard: always reports core events
[  1876.356] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  1876.356] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1876.356] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1876.356] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1876.356] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1876.356] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[  1876.356] (**) Option "xkb_rules" "evdev"
[  1876.356] (**) Option "xkb_model" "pc105"
[  1876.357] (**) Option "xkb_layout" "be"
[  1876.358] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

---

### Post by Bashing-om on 2016-04-18
Yoofz0ra: Yuk .. sorry;

We still have that situation:
> 
1876.342] (II) Unloading nvidia
 1876.346] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


It is above my skill level to "know" what is going on . Hopefully others here will chime in and give is some guidance.
I do not mind at all to poke at this and see what I can learn, and what we can do for a resolution.

As this is hybrid graphics the need to control the graphic's sets is imperative.

Do we have the controller installed ( should have by default !) ?
```

dpkg -l nvidia-settings
dpkg -l nvidia-prime

```
does the required config file exist ( should have been built when the driver installed)
```

cat /etc/X11/Xorg.conf

```

[INDENT][INDENT]inquiring minds do want to know
[/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-18
Hi Bashing-om,

np.

They are all installed. (nvidia-settings 331.20 & nvidia-prime 0.6.2)

But the config file (Xorg.conf) doesn't exist.

I also hope there are other people interested :/

Regards,
Morgan

---

### Post by Bashing-om on 2016-04-18
Yoofz0ra; Welp;

In this situation, the config file is required for hybrid graphics.

Let's have the system make one up.
```

sudo nvidia-xconfig

```

reboot to see the effect ..

[INDENT][INDENT]cross fingers
[INDENT][INDENT][INDENT]see where we can go from here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-18
Hi Bashing-om,

Still no luck..

Xorg.log

```
[    64.982] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    64.982] X Protocol Version 11, Revision 0
[    64.983] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    64.983] Current Operating System: Linux mhautman 3.16.0-70-generic #90~14.04.1-Ubuntu SMP Wed Apr 6 22:56:34 UTC 2016 x86_64
[    64.983] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-70-generic.efi.signed root=UUID=af234c39-db20-421a-87c0-d0278b4203f3 ro quiet splash vt.handoff=7
[    64.983] Build Date: 12 February 2015  11:11:26PM
[    64.983] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    64.983] Current version of pixman: 0.30.2
[    64.983]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    64.983] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    64.983] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 18 21:01:28 2016
[    64.983] (==) Using config file: "/etc/X11/xorg.conf"
[    64.983] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    64.983] (==) ServerLayout "Layout0"
[    64.983] (**) |-->Screen "Screen0" (0)
[    64.983] (**) |   |-->Monitor "Monitor0"
[    64.983] (**) |   |-->Device "Device0"
[    64.983] (**) |-->Input Device "Keyboard0"
[    64.983] (**) |-->Input Device "Mouse0"
[    64.983] (==) Automatically adding devices
[    64.983] (==) Automatically enabling devices
[    64.983] (==) Automatically adding GPU devices
[    64.983] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    64.983]     Entry deleted from font path.
[    64.983] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    64.983]     Entry deleted from font path.
[    64.983] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    64.983]     Entry deleted from font path.
[    64.983] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    64.983]     Entry deleted from font path.
[    64.983] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    64.983]     Entry deleted from font path.
[    64.983] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    64.983] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    64.983] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    64.983] (WW) Disabling Keyboard0
[    64.983] (WW) Disabling Mouse0
[    64.983] (II) Loader magic: 0x7f671ca66c80
[    64.983] (II) Module ABI versions:
[    64.983]     X.Org ANSI C Emulation: 0.4
[    64.983]     X.Org Video Driver: 18.0
[    64.983]     X.Org XInput driver : 21.0
[    64.983]     X.Org Server Extension : 8.0
[    64.983] (II) xfree86: Adding drm device (/dev/dri/card0)
[    64.985] (--) PCI:*(0:0:2:0) 8086:191b:1043:1c5d rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[    64.985] (--) PCI: (0:1:0:0) 10de:139b:1043:1c5d rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    64.985] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    64.985] (II) "glx" will be loaded by default.
[    64.985] (II) LoadModule: "glx"
[    64.985] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    64.992] (II) Module glx: vendor="NVIDIA Corporation"
[    64.992]     compiled for 4.0.2, module version = 1.0.0
[    64.992]     Module class: X.Org Server Extension
[    64.992] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    64.992] (II) LoadModule: "nvidia"
[    64.992] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    64.992] (II) Module nvidia: vendor="NVIDIA Corporation"
[    64.992]     compiled for 4.0.2, module version = 1.0.0
[    64.992]     Module class: X.Org Video Driver
[    64.992] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[    64.992] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    64.992] (++) using VT number 7

[    64.992] (EE) No devices detected.
[    64.992] (==) Matched nvidia as autoconfigured driver 0
[    64.992] (==) Matched nouveau as autoconfigured driver 1
[    64.992] (==) Matched intel as autoconfigured driver 2
[    64.992] (==) Matched modesetting as autoconfigured driver 3
[    64.992] (==) Matched fbdev as autoconfigured driver 4
[    64.992] (==) Matched vesa as autoconfigured driver 5
[    64.992] (==) Assigned the driver to the xf86ConfigLayout
[    64.992] (II) LoadModule: "nvidia"
[    64.992] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    64.992] (II) Module nvidia: vendor="NVIDIA Corporation"
[    64.992]     compiled for 4.0.2, module version = 1.0.0
[    64.992]     Module class: X.Org Video Driver
[    64.992] (II) UnloadModule: "nvidia"
[    64.992] (II) Unloading nvidia
[    64.992] (II) Failed to load module "nvidia" (already loaded, 32615)
[    64.992] (II) LoadModule: "nouveau"
[    64.993] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    64.993] (II) Module nouveau: vendor="X.Org Foundation"
[    64.993]     compiled for 1.16.0, module version = 1.0.11
[    64.993]     Module class: X.Org Video Driver
[    64.993]     ABI class: X.Org Video Driver, version 18.0
[    64.993] (II) LoadModule: "intel"
[    64.993] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    64.993] (II) Module intel: vendor="X.Org Foundation"
[    64.993]     compiled for 1.16.0, module version = 2.99.914
[    64.993]     Module class: X.Org Video Driver
[    64.993]     ABI class: X.Org Video Driver, version 18.0
[    64.993] (II) LoadModule: "modesetting"
[    64.993] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    64.993] (II) Module modesetting: vendor="X.Org Foundation"
[    64.993]     compiled for 1.16.0, module version = 0.9.0
[    64.993]     Module class: X.Org Video Driver
[    64.993]     ABI class: X.Org Video Driver, version 18.0
[    64.993] (II) LoadModule: "fbdev"
[    64.993] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    64.993] (II) Module fbdev: vendor="X.Org Foundation"
[    64.993]     compiled for 1.16.0, module version = 0.4.4
[    64.993]     Module class: X.Org Video Driver
[    64.993]     ABI class: X.Org Video Driver, version 18.0
[    64.993] (II) LoadModule: "vesa"
[    64.993] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    64.993] (II) Module vesa: vendor="X.Org Foundation"
[    64.993]     compiled for 1.16.0, module version = 2.3.3
[    64.993]     Module class: X.Org Video Driver
[    64.993]     ABI class: X.Org Video Driver, version 18.0
[    64.993] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[    64.993] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    64.993] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    64.993] (II) NOUVEAU driver for NVIDIA chipset families :
[    64.994]     RIVA TNT        (NV04)
[    64.994]     RIVA TNT2       (NV05)
[    64.994]     GeForce 256     (NV10)
[    64.994]     GeForce 2       (NV11, NV15)
[    64.994]     GeForce 4MX     (NV17, NV18)
[    64.994]     GeForce 3       (NV20)
[    64.994]     GeForce 4Ti     (NV25, NV28)
[    64.994]     GeForce FX      (NV3x)
[    64.994]     GeForce 6       (NV4x)
[    64.994]     GeForce 7       (G7x)
[    64.994]     GeForce 8       (G8x)
[    64.994]     GeForce GTX 200 (NVA0)
[    64.994]     GeForce GTX 400 (NVC0)
[    64.994] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    64.994] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    64.994] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    64.994] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    64.994] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    64.994] (II) FBDEV: driver for framebuffer: fbdev
[    64.994] (II) VESA: driver for VESA chipsets: vesa
[    64.994] (++) using VT number 7

[    64.994] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    64.994] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    64.994] (EE) [drm] KMS not enabled
[    64.994] (EE) [drm] KMS not enabled
[    64.997] (WW) Falling back to old probe method for modesetting
[    64.997] (II) Loading sub module "fbdevhw"
[    64.997] (II) LoadModule: "fbdevhw"
[    64.997] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    64.997] (II) Module fbdevhw: vendor="X.Org Foundation"
[    64.997]     compiled for 1.16.0, module version = 0.0.2
[    64.997]     ABI class: X.Org Video Driver, version 18.0
[    64.997] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    64.997] (II) FBDEV(1): using default device
[    64.997] (WW) Falling back to old probe method for vesa
[    64.997] (EE) Screen 0 deleted because of no matching config section.
[    64.997] (II) UnloadModule: "modesetting"
[    64.997] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[    64.997] (==) FBDEV(0): RGB weight 888
[    64.997] (==) FBDEV(0): Default visual is TrueColor
[    64.997] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    64.997] (II) FBDEV(0): hardware: EFI VGA (video memory: 1876kB)
[    64.997] (II) FBDEV(0): checking modes against framebuffer device...
[    64.997] (II) FBDEV(0): checking modes against monitor...
[    64.997] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[    64.997] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[    64.997] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[    64.997] (==) FBDEV(0): DPI set to (96, 96)
[    64.997] (II) Loading sub module "fb"
[    64.997] (II) LoadModule: "fb"
[    64.997] (II) Loading /usr/lib/xorg/modules/libfb.so
[    64.997] (II) Module fb: vendor="X.Org Foundation"
[    64.997]     compiled for 1.16.0, module version = 1.0.0
[    64.997]     ABI class: X.Org ANSI C Emulation, version 0.4
[    64.997] (**) FBDEV(0): using shadow framebuffer
[    64.997] (II) Loading sub module "shadow"
[    64.997] (II) LoadModule: "shadow"
[    64.997] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    64.997] (II) Module shadow: vendor="X.Org Foundation"
[    64.997]     compiled for 1.16.0, module version = 1.1.0
[    64.997]     ABI class: X.Org ANSI C Emulation, version 0.4
[    64.997] (II) UnloadModule: "nvidia"
[    64.997] (II) Unloading nvidia
[    64.998] (II) UnloadModule: "vesa"
[    64.998] (II) Unloading vesa
[    64.998] (==) Depth 24 pixmap format is 32 bpp
[    64.998] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    64.998] (==) FBDEV(0): Backing store enabled
[    64.998] (**) FBDEV(0): DPMS enabled
[    64.998] (==) RandR enabled
[    65.002] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    65.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    65.008] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    65.008] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    65.008] (II) LoadModule: "evdev"
[    65.008] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    65.009] (II) Module evdev: vendor="X.Org Foundation"
[    65.009]     compiled for 1.16.0, module version = 2.9.0
[    65.009]     Module class: X.Org XInput Driver
[    65.009]     ABI class: X.Org XInput driver, version 21.0
[    65.009] (II) Using input driver 'evdev' for 'Power Button'
[    65.009] (**) Power Button: always reports core events
[    65.009] (**) evdev: Power Button: Device: "/dev/input/event2"
[    65.009] (--) evdev: Power Button: Vendor 0 Product 0x1
[    65.009] (--) evdev: Power Button: Found keys
[    65.009] (II) evdev: Power Button: Configuring as keyboard
[    65.009] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    65.009] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    65.009] (**) Option "xkb_rules" "evdev"
[    65.009] (**) Option "xkb_model" "pc105"
[    65.009] (**) Option "xkb_layout" "be"
[    65.010] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[    65.010] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    65.010] (II) No input driver specified, ignoring this device.
[    65.010] (II) This device may have been added with another device file.
[    65.010] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    65.010] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    65.010] (II) Using input driver 'evdev' for 'Sleep Button'
[    65.010] (**) Sleep Button: always reports core events
[    65.010] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    65.010] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    65.010] (--) evdev: Sleep Button: Found keys
[    65.010] (II) evdev: Sleep Button: Configuring as keyboard
[    65.010] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    65.010] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    65.011] (**) Option "xkb_rules" "evdev"
[    65.011] (**) Option "xkb_model" "pc105"
[    65.011] (**) Option "xkb_layout" "be"
[    65.011] (II) config/udev: Adding input device USB2.0 HD UVC WebCam (/dev/input/event4)
[    65.011] (**) USB2.0 HD UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    65.011] (II) Using input driver 'evdev' for 'USB2.0 HD UVC WebCam'
[    65.011] (**) USB2.0 HD UVC WebCam: always reports core events
[    65.011] (**) evdev: USB2.0 HD UVC WebCam: Device: "/dev/input/event4"
[    65.011] (--) evdev: USB2.0 HD UVC WebCam: Vendor 0x4f2 Product 0xb424
[    65.011] (--) evdev: USB2.0 HD UVC WebCam: Found keys
[    65.011] (II) evdev: USB2.0 HD UVC WebCam: Configuring as keyboard
[    65.011] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input4/event4"
[    65.011] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam" (type: KEYBOARD, id 8)
[    65.011] (**) Option "xkb_rules" "evdev"
[    65.011] (**) Option "xkb_model" "pc105"
[    65.011] (**) Option "xkb_layout" "be"
[    65.011] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    65.011] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    65.011] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    65.011] (**) Logitech USB Receiver: always reports core events
[    65.011] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[    65.011] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    65.011] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    65.011] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    65.011] (--) evdev: Logitech USB Receiver: Found relative axes
[    65.011] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    65.011] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    65.011] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    65.011] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    65.011] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.011] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:046D:C52F.0001/input/input6/event6"
[    65.011] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[    65.011] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    65.011] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    65.011] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    65.012] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    65.012] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    65.012] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    65.012] (II) No input driver specified, ignoring this device.
[    65.012] (II) This device may have been added with another device file.
[    65.012] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    65.012] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    65.012] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    65.012] (**) Logitech USB Receiver: always reports core events
[    65.012] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event7"
[    65.012] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    65.012] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[    65.012] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    65.012] (--) evdev: Logitech USB Receiver: Found relative axes
[    65.012] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[    65.012] (--) evdev: Logitech USB Receiver: Found absolute axes
[    65.012] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    65.012] (--) evdev: Logitech USB Receiver: Found keys
[    65.012] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    65.012] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    65.012] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    65.012] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    65.012] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.012] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:046D:C52F.0002/input/input7/event7"
[    65.012] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    65.012] (**) Option "xkb_rules" "evdev"
[    65.012] (**) Option "xkb_model" "pc105"
[    65.012] (**) Option "xkb_layout" "be"
[    65.012] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    65.012] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    65.012] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    65.012] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    65.012] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    65.012] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    65.012] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    65.012] (II) No input driver specified, ignoring this device.
[    65.012] (II) This device may have been added with another device file.
[    65.012] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    65.013] (II) No input driver specified, ignoring this device.
[    65.013] (II) This device may have been added with another device file.
[    65.013] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    65.013] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    65.013] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    65.013] (**) Asus WMI hotkeys: always reports core events
[    65.013] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    65.013] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    65.013] (--) evdev: Asus WMI hotkeys: Found keys
[    65.013] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    65.013] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    65.013] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    65.013] (**) Option "xkb_rules" "evdev"
[    65.013] (**) Option "xkb_model" "pc105"
[    65.013] (**) Option "xkb_layout" "be"
[    65.013] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    65.013] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    65.013] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    65.013] (**) AT Translated Set 2 keyboard: always reports core events
[    65.013] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    65.013] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    65.013] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    65.013] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    65.013] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    65.013] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    65.013] (**) Option "xkb_rules" "evdev"
[    65.013] (**) Option "xkb_model" "pc105"
[    65.013] (**) Option "xkb_layout" "be"
[    65.015] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

/etc/X11/xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 352.63  (buildmeister@swio-display-x64-rhel04-11)  Sat Nov  7 22:00:19 PST 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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


```

---

### Post by Bashing-om on 2016-04-18
Yoofz0ra; Ouch !

Surprised that the generated config file is not at all what I expected.
I do have an old working config file for a reference, yours is not at all the same.
As I do not have complete faith in my knowledge of the Nvidia/Intel config file; let's sit on this a spell and await others to advise.

log file:
> 
64.992] (EE) No devices detected.
64.992] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
64.992] (II) UnloadModule: "nvidia"

64.992] (II) Failed to load module "nvidia" (already loaded, 32615)

64.997] (**) FBDEV(1): claimed PCI slot 0@0:2:0

 64.997] (II) Unloading nvidia

  65.002] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)



I surely do not know why the Nvidia driver does not fully build and install .

[INDENT][INDENT]when in doubt
[INDENT][INDENT][INDENT]wait
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yoofz0ra on 2016-04-19
Hi Bashing-om,

Thank you for trying.

I really hope you know other people who can help! :)

Regards,
Morgan

---

### Post by Yoofz0ra on 2016-04-20
No-one else knows something here?
Sorry but I'm really disappointed about this forum...

Regards,
Morgan

---

### Post by motar2 on 2016-04-20
> **Yoofz0ra said:**
> No-one else knows something here? Sorry but I'm really disappointed about this forum...  Regards, Morgan    

Hey is a forum, it doesn´t mean it will have the answer to everything.   

Only Douglas Adams knows that the answer is 42.    Back to your problem.  

 I had some problems with the NVDIA 840m card and Bumble, finally decide to reinstall and start afresh, casue could not remember all the changes I made.    

I am running Mint 17.3, but the repositories are all Ubuntu so check my description on the Mint threat and see if it is of some help.    

 [https://forums.linuxmint.com/viewtopic.php?f=49&t=219616](https://forums.linuxmint.com/viewtopic.php?f=49&t=219616)

---

### Post by Yoofz0ra on 2016-04-20
Hi motar2,

Sorry I'm a little frustrated because I re-installed Ubuntu 6 times already and followed lot's of forum post or blogs.
I didn't find any solution to my problem.. this was the last step and if no-one's answering I have no other ******* choice then installing Windows :)

I feel like I'm the only one in the world where it doesn't work.

Bumblebee or prime, none works.

Sorry again.

Regards,
Morgan

---

### Post by Yoofz0ra on 2016-04-23
Hi,

With the new Ubuntu 16 LTS update it works perfectly.

Thank you a lot Bashing-om. It's because of you I didn't installed Windows because I started to become crazy! ;)

Regards,
Morgan

---

### Post by rahulyup on 2016-04-23
Same goes for me . nvidia-xconfig results in creating new xconf file .Rebooting results in black screen and I couldn't log in . All i have to do is  purge my drivers . I hope one day I will be able to use nvidia on Ubuntu Huh ! :(

---

### Post by Yoofz0ra on 2016-04-23
Hi Rahulyup,

I forced the upgrade to Ubuntu 16.04 LTS through the terminael , you can find explanations here. [http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts)
I'm on 1980x1920 full hd now. 
The nouveau drivers work, the proprietary still don't work but I'm fine with nouveau since I got a nice resolution + HD.

Hope it helps you.

Regards,
Morgan

---

### Post by Bashing-om on 2016-04-23
Yoofz0ra; Great !

Glad you are still with us . Release 16.04 promised to resolve a lot of the new hardware graphic's issues; In your case seems it did !

[INDENT][INDENT]just keep n keep'n on
[/INDENT][/INDENT]

---

### Post by motar2 on 2016-04-23
Hey I understand, suffered the same problems with my setup, I was just trying to cheer you up.

I am glad that the new version is working OK for you, this issue with NVIDIA and drivers is a real pain, I believe that Linus Torval was right about NVIDIA as a company, here is a riminder of what he thought about it.

[http://de.engadget.com/2012/06/18/linux-erfinder-torvalds-mag-nvidia-nicht-so-gerne-mit-video](http://de.engadget.com/2012/06/18/linux-erfinder-torvalds-mag-nvidia-nicht-so-gerne-mit-video)

ATB

---

