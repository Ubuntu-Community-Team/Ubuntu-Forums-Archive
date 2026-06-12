---
title: "Ubuntu 15.04 with SiS 771/671 extremely slow graphics"
date: 2015-06-12
forum: Hardware
---

### Post by hetvm on 2015-06-12
I just installed Ubuntu 15.04 64-bit on a Dell Optiplex 160 SFF computer. Graphics display is incredibly slow such that the system is unusable. When I type, it takes about 1/2 second for each character to display. Windows take up to 5 seconds to fade in/out. Menus take 1 or 2 seconds to display after clicked.

lspci shows:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

I have found that there are quite a few discussions about this graphics card but they seem to be rather dated and some posts suggested there were improvements in 14.04 so I'm not sure how relevant those posts are. In any case most of the discussions did not seem to mention a massive performance issue but were rather concerned with resolution, and most did not seem to have any definite solutions, rather just massive listings of confg files and sketchy links to private web sites.

What can I do?

---

### Post by Pilot6 on 2015-06-12
The last Ubuntu that can work well with this card is Ubuntu 12.04 with a driver built from source. Anything newer does not give normal screen resolution.

---

### Post by hetvm on 2015-06-12
The resolution is fine at 1280x1024 @ 60 Hz actually. The problem I'm having is performance.

---

### Post by weatherman2 on 2015-06-12
You might want to try one of the less resource-hungry desktops like Lubuntu - or in Ubuntu, install Gnome Flashback and use Metacity.  I have found that gives reasonable performance on graphics chipsets where Unity is really slow.

---

### Post by hetvm on 2015-06-16
I installed Lubuntu 14.04.2 LTS. It is a little more usable but still annoyingly slow. When I drag a window it lags terribly behind the mouse, leading to a rather comical effect where windows go drifting around the screen long after I stopped moving the mouse as if they had a mind of their own. Scrolling in Firefox or PCManFM is also terribly slow. Even the full screen virtual consoles are too slow to use...getting a directory listing is like using a 2400 baud modem.

---

### Post by Yellow Pasque on 2015-06-17
It appears Debian/Ubuntu no longer build/distribute the sis driver, maybe because it doesn't build against newer Xservers.
Still, it should be available in 14.04 and it should give you some 2D acceleration, enough to make Lubuntu bearable.
Can you give the /var/log/Xorg.0.log ?

---

### Post by hetvm on 2015-06-17
Certainly.

```

[    20.029] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    20.029] X Protocol Version 11, Revision 0
[    20.029] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    20.029] Current Operating System: Linux opti160 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64
[    20.029] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic root=UUID=f60abef0-8832-4da5-8066-33d52939fbf5 ro quiet splash vt.handoff=7
[    20.029] Build Date: 12 February 2015  11:11:26PM
[    20.029] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    20.030] Current version of pixman: 0.30.2
[    20.030]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.030] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.030] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 17 17:34:43 2015
[    20.032] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.033] (==) No Layout section.  Using the first Screen section.
[    20.033] (==) No screen section available. Using defaults.
[    20.033] (**) |-->Screen "Default Screen Section" (0)
[    20.033] (**) |   |-->Monitor "<default monitor>"
[    20.035] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.036] (==) Automatically adding devices
[    20.036] (==) Automatically enabling devices
[    20.036] (==) Automatically adding GPU devices
[    20.036] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.036]     Entry deleted from font path.
[    20.036] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.036]     Entry deleted from font path.
[    20.036] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.036]     Entry deleted from font path.
[    20.036] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    20.036]     Entry deleted from font path.
[    20.036] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.036]     Entry deleted from font path.
[    20.037] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.037]     Entry deleted from font path.
[    20.037] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    20.037] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.037] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.037] (II) Loader magic: 0x7f6c15b01c80
[    20.037] (II) Module ABI versions:
[    20.037]     X.Org ANSI C Emulation: 0.4
[    20.037]     X.Org Video Driver: 18.0
[    20.037]     X.Org XInput driver : 21.0
[    20.037]     X.Org Server Extension : 8.0
[    20.040] (--) PCI:*(0:1:0:0) 1039:6351:1028:02c3 rev 16, Mem @ 0xd0000000/268435456, 0xfeae0000/131072, I/O @ 0x0000ec00/128
[    20.041] (II) LoadModule: "glx"
[    20.057] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.141] (II) Module glx: vendor="X.Org Foundation"
[    20.141]     compiled for 1.16.0, module version = 1.0.0
[    20.142]     ABI class: X.Org Server Extension, version 8.0
[    20.142] (==) AIGLX enabled
[    20.142] (==) Matched sis as autoconfigured driver 0
[    20.142] (==) Matched modesetting as autoconfigured driver 1
[    20.142] (==) Matched fbdev as autoconfigured driver 2
[    20.142] (==) Matched vesa as autoconfigured driver 3
[    20.142] (==) Assigned the driver to the xf86ConfigLayout
[    20.142] (II) LoadModule: "sis"
[    20.145] (WW) Warning, couldn't open module sis
[    20.145] (II) UnloadModule: "sis"
[    20.145] (II) Unloading sis
[    20.145] (EE) Failed to load module "sis" (module does not exist, 0)
[    20.145] (II) LoadModule: "modesetting"
[    20.146] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.147] (II) Module modesetting: vendor="X.Org Foundation"
[    20.147]     compiled for 1.16.0, module version = 0.9.0
[    20.147]     Module class: X.Org Video Driver
[    20.147]     ABI class: X.Org Video Driver, version 18.0
[    20.147] (II) LoadModule: "fbdev"
[    20.148] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.149] (II) Module fbdev: vendor="X.Org Foundation"
[    20.149]     compiled for 1.16.0, module version = 0.4.4
[    20.149]     Module class: X.Org Video Driver
[    20.149]     ABI class: X.Org Video Driver, version 18.0
[    20.149] (II) LoadModule: "vesa"
[    20.150] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.150] (II) Module vesa: vendor="X.Org Foundation"
[    20.150]     compiled for 1.16.0, module version = 2.3.3
[    20.150]     Module class: X.Org Video Driver
[    20.150]     ABI class: X.Org Video Driver, version 18.0
[    20.150] (==) Matched sis as autoconfigured driver 0
[    20.151] (==) Matched modesetting as autoconfigured driver 1
[    20.151] (==) Matched fbdev as autoconfigured driver 2
[    20.151] (==) Matched vesa as autoconfigured driver 3
[    20.151] (==) Assigned the driver to the xf86ConfigLayout
[    20.151] (II) LoadModule: "sis"
[    20.152] (WW) Warning, couldn't open module sis
[    20.152] (II) UnloadModule: "sis"
[    20.152] (II) Unloading sis
[    20.152] (EE) Failed to load module "sis" (module does not exist, 0)
[    20.153] (II) LoadModule: "modesetting"
[    20.153] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.153] (II) Module modesetting: vendor="X.Org Foundation"
[    20.154]     compiled for 1.16.0, module version = 0.9.0
[    20.154]     Module class: X.Org Video Driver
[    20.154]     ABI class: X.Org Video Driver, version 18.0
[    20.154] (II) UnloadModule: "modesetting"
[    20.154] (II) Unloading modesetting
[    20.154] (II) Failed to load module "modesetting" (already loaded, 0)
[    20.154] (II) LoadModule: "fbdev"
[    20.155] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.155] (II) Module fbdev: vendor="X.Org Foundation"
[    20.155]     compiled for 1.16.0, module version = 0.4.4
[    20.155]     Module class: X.Org Video Driver
[    20.155]     ABI class: X.Org Video Driver, version 18.0
[    20.155] (II) UnloadModule: "fbdev"
[    20.155] (II) Unloading fbdev
[    20.155] (II) Failed to load module "fbdev" (already loaded, 0)
[    20.155] (II) LoadModule: "vesa"
[    20.156] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.156] (II) Module vesa: vendor="X.Org Foundation"
[    20.156]     compiled for 1.16.0, module version = 2.3.3
[    20.156]     Module class: X.Org Video Driver
[    20.156]     ABI class: X.Org Video Driver, version 18.0
[    20.156] (II) UnloadModule: "vesa"
[    20.157] (II) Unloading vesa
[    20.157] (II) Failed to load module "vesa" (already loaded, 0)
[    20.157] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.157] (II) FBDEV: driver for framebuffer: fbdev
[    20.157] (II) VESA: driver for VESA chipsets: vesa
[    20.157] (++) using VT number 7

[    20.157] (EE) open /dev/dri/card0: No such file or directory
[    20.157] (EE) open /dev/dri/card0: No such file or directory
[    20.158] (WW) Falling back to old probe method for modesetting
[    20.158] (EE) open /dev/dri/card0: No such file or directory
[    20.158] (EE) open /dev/dri/card0: No such file or directory
[    20.158] (II) Loading sub module "fbdevhw"
[    20.158] (II) LoadModule: "fbdevhw"
[    20.159] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.159] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.159]     compiled for 1.16.0, module version = 0.0.2
[    20.159]     ABI class: X.Org Video Driver, version 18.0
[    20.159] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    20.159] (II) FBDEV(2): using default device
[    20.159] (WW) Falling back to old probe method for vesa
[    20.160] (EE) Screen 0 deleted because of no matching config section.
[    20.160] (II) UnloadModule: "modesetting"
[    20.160] (EE) Screen 0 deleted because of no matching config section.
[    20.160] (II) UnloadModule: "modesetting"
[    20.160] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.160] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    20.160] (==) FBDEV(0): RGB weight 888
[    20.160] (==) FBDEV(0): Default visual is TrueColor
[    20.160] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.160] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[    20.160] (II) FBDEV(0): checking modes against framebuffer device...
[    20.161] (II) FBDEV(0): checking modes against monitor...
[    20.161] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    20.161] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[    20.161] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[    20.161] (==) FBDEV(0): DPI set to (96, 96)
[    20.161] (II) Loading sub module "fb"
[    20.161] (II) LoadModule: "fb"
[    20.162] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.162] (II) Module fb: vendor="X.Org Foundation"
[    20.162]     compiled for 1.16.0, module version = 1.0.0
[    20.162]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.163] (**) FBDEV(0): using shadow framebuffer
[    20.163] (II) Loading sub module "shadow"
[    20.163] (II) LoadModule: "shadow"
[    20.163] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    20.164] (II) Module shadow: vendor="X.Org Foundation"
[    20.164]     compiled for 1.16.0, module version = 1.1.0
[    20.164]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.164] (II) UnloadModule: "vesa"
[    20.164] (II) Unloading vesa
[    20.164] (==) Depth 24 pixmap format is 32 bpp
[    20.165] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    20.188] (==) FBDEV(0): Backing store enabled
[    20.191] (==) FBDEV(0): DPMS enabled
[    20.192] (==) RandR enabled
[    20.215] (II) AIGLX: Screen 0 is not DRI2 capable
[    20.215] (EE) AIGLX: reverting to software rendering
[    20.348] (II) AIGLX: Loaded and initialized swrast
[    20.348] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    20.390] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.401] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.401] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.401] (II) LoadModule: "evdev"
[    20.402] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.440] (II) Module evdev: vendor="X.Org Foundation"
[    20.440]     compiled for 1.16.0, module version = 2.9.0
[    20.440]     Module class: X.Org XInput Driver
[    20.440]     ABI class: X.Org XInput driver, version 21.0
[    20.441] (II) Using input driver 'evdev' for 'Power Button'
[    20.441] (**) Power Button: always reports core events
[    20.441] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.441] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.441] (--) evdev: Power Button: Found keys
[    20.441] (II) evdev: Power Button: Configuring as keyboard
[    20.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.441] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.441] (**) Option "xkb_rules" "evdev"
[    20.441] (**) Option "xkb_model" "pc105"
[    20.442] (**) Option "xkb_layout" "us"
[    20.444] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.444] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.444] (II) Using input driver 'evdev' for 'Power Button'
[    20.444] (**) Power Button: always reports core events
[    20.444] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.444] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.444] (--) evdev: Power Button: Found keys
[    20.445] (II) evdev: Power Button: Configuring as keyboard
[    20.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    20.445] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    20.445] (**) Option "xkb_rules" "evdev"
[    20.445] (**) Option "xkb_model" "pc105"
[    20.445] (**) Option "xkb_layout" "us"
[    20.447] (II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/event3)
[    20.447] (**) HP HP USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[    20.448] (II) Using input driver 'evdev' for 'HP HP USB Laser Mouse'
[    20.448] (**) HP HP USB Laser Mouse: always reports core events
[    20.448] (**) evdev: HP HP USB Laser Mouse: Device: "/dev/input/event3"
[    20.448] (--) evdev: HP HP USB Laser Mouse: Vendor 0x3f0 Product 0x2c24
[    20.448] (--) evdev: HP HP USB Laser Mouse: Found 3 mouse buttons
[    20.448] (--) evdev: HP HP USB Laser Mouse: Found scroll wheel(s)
[    20.448] (--) evdev: HP HP USB Laser Mouse: Found relative axes
[    20.448] (--) evdev: HP HP USB Laser Mouse: Found x and y relative axes
[    20.448] (II) evdev: HP HP USB Laser Mouse: Configuring as mouse
[    20.448] (II) evdev: HP HP USB Laser Mouse: Adding scrollwheel support
[    20.448] (**) evdev: HP HP USB Laser Mouse: YAxisMapping: buttons 4 and 5
[    20.449] (**) evdev: HP HP USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.449] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/0003:03F0:2C24.0001/input/input3/event3"
[    20.449] (II) XINPUT: Adding extended input device "HP HP USB Laser Mouse" (type: MOUSE, id 8)
[    20.449] (II) evdev: HP HP USB Laser Mouse: initialized for relative axes.
[    20.450] (**) HP HP USB Laser Mouse: (accel) keeping acceleration scheme 1
[    20.450] (**) HP HP USB Laser Mouse: (accel) acceleration profile 0
[    20.450] (**) HP HP USB Laser Mouse: (accel) acceleration factor: 2.000
[    20.450] (**) HP HP USB Laser Mouse: (accel) acceleration threshold: 4
[    20.451] (II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/mouse0)
[    20.451] (II) No input driver specified, ignoring this device.
[    20.451] (II) This device may have been added with another device file.
[    20.453] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event4)
[    20.453] (II) No input driver specified, ignoring this device.
[    20.453] (II) This device may have been added with another device file.
[    20.454] (II) config/udev: Adding input device HDA SIS966 Front Headphone (/dev/input/event5)
[    20.454] (II) No input driver specified, ignoring this device.
[    20.454] (II) This device may have been added with another device file.
[    20.455] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    20.455] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.455] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.455] (**) AT Translated Set 2 keyboard: always reports core events
[    20.455] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    20.456] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.456] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.456] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.456] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    20.456] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    20.456] (**) Option "xkb_rules" "evdev"
[    20.456] (**) Option "xkb_model" "pc105"
[    20.456] (**) Option "xkb_layout" "us"
[    20.481] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    23.905] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm


```

---

### Post by Yellow Pasque on 2015-06-18
```
(EE) Failed to load module "sis" (module does not exist, 0)
```
Have you installed xserver-xorg-video-sis package?

---

### Post by hetvm on 2015-06-18
It appears I cannot:

```

~$ sudo apt-get install xserver-xorg-video-sis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-sis : Depends: xorg-video-abi-15
                          Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Yellow Pasque on 2015-06-18
```
xserver-xorg-video-sis : Depends: xorg-video-abi-15
```
That is what I suspected. Lubuntu 14.04.2 comes with a newer Xserver than what was in 14.04 and 14.04.1, and the sis package has not been updated to support it. I'm not sure how hard it would be to update (it may just be a formality of changing the dependency on xorg-video-abi-15 to accept newer versions of that metapackage).

So, in more practical terms, you'll probably get better results by installing Lubuntu 14.04.1 and installing the sis package.
Another possibility if you don't want to do a complete reinstall is forcing use of the generic vesa driver, since the fbdev driver is currently being auto-selected. You could make an /etc/X11/xorg.conf with following contents:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

