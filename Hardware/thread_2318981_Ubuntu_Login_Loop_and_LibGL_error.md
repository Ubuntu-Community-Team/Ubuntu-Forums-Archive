---
title: "Ubuntu Login Loop and LibGL error"
date: 2016-03-31
forum: Hardware
---

### Post by MatthiasE on 2016-03-31
[COLOR=#111111][FONT=Ubuntu]Hi,

after installing a Nvidia GeForce GTX 770 graphics card, I tried to install Nvidia's proprietary drivers via the "Additional drivers" dialogue.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After rebooting the computer the login screen appeared but I was not able to login. The screen turns black for a second then it falls back to the login screen.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So much about what happened - these are my specs and what I have tried so far:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]System: Ubuntu 15.10 Added the Graphics Drivers PPA to the software sources, tried all available drivers listed in the additional drivers dialogue leading to the same result. The only driver that works well is the Nouveau one. Then I checked whether there is a .Xauthority problem - but there is none.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However in ~/.xsessions-error these error messages appear:

[/FONT][/COLOR]> 
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

[COLOR=#111111][FONT=Ubuntu]Any suggestions?

Cheers,
Matthias[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-03-31
Install the proprietary driver and try to log in. Ctrl+Alt+F1 to the terminal when it fails and save the Xorg log.
```
cp /var/log/Xorg.0.log ~/xfail.log
```

Then you can switch back to nouveau and share the log with us (use code tags as it's a lot of text).

---

### Post by MatthiasE on 2016-04-05
Sorry, I've been ill for the last couple of days &#8230; I'm gonna post the logfile soon!

---

### Post by MatthiasE on 2016-04-05
This is the output of the logfile:

```

[    23.829] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    23.829] X Protocol Version 11, Revision 0
[    23.829] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    23.829] Current Operating System: Linux cameran-System-Product-Name 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64
[    23.829] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-35-generic.efi.signed root=UUID=ab120781-9a9e-4007-a11c-12ecfb25d800 ro noprompt persistent quiet splash vt.handoff=7
[    23.829] Build Date: 12 November 2015  05:33:29PM
[    23.829] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    23.829] Current version of pixman: 0.32.6
[    23.829]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    23.829] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.829] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  5 17:16:56 2016
[    23.829] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.829] (==) No Layout section.  Using the first Screen section.
[    23.829] (==) No screen section available. Using defaults.
[    23.829] (**) |-->Screen "Default Screen Section" (0)
[    23.829] (**) |   |-->Monitor "<default monitor>"
[    23.829] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.829] (==) Automatically adding devices
[    23.829] (==) Automatically enabling devices
[    23.829] (==) Automatically adding GPU devices
[    23.829] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.829]     Entry deleted from font path.
[    23.829] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.829]     Entry deleted from font path.
[    23.829] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.829]     Entry deleted from font path.
[    23.829] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.829]     Entry deleted from font path.
[    23.829] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.829]     Entry deleted from font path.
[    23.829] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.829] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.829] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.829] (II) Loader magic: 0x55af391d7d40
[    23.829] (II) Module ABI versions:
[    23.829]     X.Org ANSI C Emulation: 0.4
[    23.829]     X.Org Video Driver: 19.0
[    23.829]     X.Org XInput driver : 21.0
[    23.830]     X.Org Server Extension : 9.0
[    23.830] (II) xfree86: Adding drm device (/dev/dri/card0)
[    23.831] (--) PCI:*(0:1:0:0) 10de:1184:196e:1033 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    23.831] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    23.831] (II) "glx" will be loaded by default.
[    23.831] (II) LoadModule: "glx"
[    23.831] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    23.833] (II) Module glx: vendor="NVIDIA Corporation"
[    23.833]     compiled for 4.0.2, module version = 1.0.0
[    23.833]     Module class: X.Org Server Extension
[    23.833] (II) NVIDIA GLX Module  358.16  Mon Nov 16 18:54:01 PST 2015
[    23.833] (==) Matched nvidia as autoconfigured driver 0
[    23.833] (==) Matched nouveau as autoconfigured driver 1
[    23.833] (==) Matched nvidia as autoconfigured driver 2
[    23.833] (==) Matched nouveau as autoconfigured driver 3
[    23.833] (==) Matched modesetting as autoconfigured driver 4
[    23.833] (==) Matched fbdev as autoconfigured driver 5
[    23.833] (==) Matched vesa as autoconfigured driver 6
[    23.833] (==) Assigned the driver to the xf86ConfigLayout
[    23.833] (II) LoadModule: "nvidia"
[    23.833] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.833] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.833]     compiled for 4.0.2, module version = 1.0.0
[    23.833]     Module class: X.Org Video Driver
[    23.833] (II) LoadModule: "nouveau"
[    23.833] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.833] (II) Module nouveau: vendor="X.Org Foundation"
[    23.833]     compiled for 1.17.1, module version = 1.0.11
[    23.833]     Module class: X.Org Video Driver
[    23.833]     ABI class: X.Org Video Driver, version 19.0
[    23.833] (II) LoadModule: "modesetting"
[    23.834] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.834] (II) Module modesetting: vendor="X.Org Foundation"
[    23.834]     compiled for 1.17.2, module version = 1.17.2
[    23.834]     Module class: X.Org Video Driver
[    23.834]     ABI class: X.Org Video Driver, version 19.0
[    23.834] (II) LoadModule: "fbdev"
[    23.834] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.834] (II) Module fbdev: vendor="X.Org Foundation"
[    23.834]     compiled for 1.17.1, module version = 0.4.4
[    23.834]     Module class: X.Org Video Driver
[    23.834]     ABI class: X.Org Video Driver, version 19.0
[    23.834] (II) LoadModule: "vesa"
[    23.834] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.834] (II) Module vesa: vendor="X.Org Foundation"
[    23.834]     compiled for 1.17.1, module version = 2.3.4
[    23.834]     Module class: X.Org Video Driver
[    23.834]     ABI class: X.Org Video Driver, version 19.0
[    23.834] (II) NVIDIA dlloader X Driver  358.16  Mon Nov 16 18:32:40 PST 2015
[    23.834] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.834] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    23.834] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.834]     RIVA TNT        (NV04)
[    23.834]     RIVA TNT2       (NV05)
[    23.834]     GeForce 256     (NV10)
[    23.834]     GeForce 2       (NV11, NV15)
[    23.834]     GeForce 4MX     (NV17, NV18)
[    23.834]     GeForce 3       (NV20)
[    23.834]     GeForce 4Ti     (NV25, NV28)
[    23.834]     GeForce FX      (NV3x)
[    23.834]     GeForce 6       (NV4x)
[    23.834]     GeForce 7       (G7x)
[    23.834]     GeForce 8       (G8x)
[    23.834]     GeForce GTX 200 (NVA0)
[    23.834]     GeForce GTX 400 (NVC0)
[    23.834] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.834] (II) FBDEV: driver for framebuffer: fbdev
[    23.834] (II) VESA: driver for VESA chipsets: vesa
[    23.834] (++) using VT number 7


[    23.834] (II) Loading sub module "fb"
[    23.834] (II) LoadModule: "fb"
[    23.834] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.834] (II) Module fb: vendor="X.Org Foundation"
[    23.834]     compiled for 1.17.2, module version = 1.0.0
[    23.834]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.834] (II) Loading sub module "wfb"
[    23.834] (II) LoadModule: "wfb"
[    23.834] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.834] (II) Module wfb: vendor="X.Org Foundation"
[    23.834]     compiled for 1.17.2, module version = 1.0.0
[    23.834]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.834] (II) Loading sub module "ramdac"
[    23.834] (II) LoadModule: "ramdac"
[    23.834] (II) Module "ramdac" already built-in
[    23.835] (WW) Falling back to old probe method for modesetting
[    23.835] (WW) Falling back to old probe method for fbdev
[    23.835] (II) Loading sub module "fbdevhw"
[    23.835] (II) LoadModule: "fbdevhw"
[    23.835] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.835] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.835]     compiled for 1.17.2, module version = 0.0.2
[    23.835]     ABI class: X.Org Video Driver, version 19.0
[    23.835] (WW) Falling back to old probe method for vesa
[    23.835] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.835] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    23.835] (==) NVIDIA(0): RGB weight 888
[    23.835] (==) NVIDIA(0): Default visual is TrueColor
[    23.835] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.835] (**) NVIDIA(0): Enabling 2D acceleration
[    24.151] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    24.151] (--) NVIDIA(0):     CRT-0
[    24.151] (--) NVIDIA(0):     DFP-0
[    24.151] (--) NVIDIA(0):     DFP-1 (boot)
[    24.151] (--) NVIDIA(0):     DFP-2
[    24.151] (--) NVIDIA(0):     DFP-3
[    24.151] (--) NVIDIA(0):     DFP-4
[    24.153] (--) NVIDIA(0): CRT-0: disconnected
[    24.153] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    24.153] (--) NVIDIA(0): 
[    24.156] (--) NVIDIA(0): DFP-0: disconnected
[    24.156] (--) NVIDIA(0): DFP-0: Internal TMDS
[    24.156] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    24.156] (--) NVIDIA(0): 
[    24.166] (--) NVIDIA(0): BenQ V2400Eco (DFP-1): connected
[    24.166] (--) NVIDIA(0): BenQ V2400Eco (DFP-1): Internal TMDS
[    24.166] (--) NVIDIA(0): BenQ V2400Eco (DFP-1): 340.0 MHz maximum pixel clock
[    24.166] (--) NVIDIA(0): 
[    24.166] (--) NVIDIA(0): DFP-2: disconnected
[    24.166] (--) NVIDIA(0): DFP-2: Internal TMDS
[    24.166] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    24.166] (--) NVIDIA(0): 
[    24.166] (--) NVIDIA(0): DFP-3: disconnected
[    24.166] (--) NVIDIA(0): DFP-3: Internal TMDS
[    24.166] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[    24.166] (--) NVIDIA(0): 
[    24.166] (--) NVIDIA(0): DFP-4: disconnected
[    24.166] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    24.166] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[    24.166] (--) NVIDIA(0): 
[    24.166] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    24.167] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 770 (GK104) at PCI:1:0:0 (GPU-0)
[    24.167] (--) NVIDIA(0): Memory: 2097152 kBytes
[    24.167] (--) NVIDIA(0): VideoBIOS: 80.04.c3.00.2a
[    24.167] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.167] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.167] (**) NVIDIA(0):     device BenQ V2400Eco (DFP-1) (Using EDID frequencies has
[    24.167] (**) NVIDIA(0):     been enabled on all display devices.)
[    24.169] (==) NVIDIA(0): 
[    24.169] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    24.169] (==) NVIDIA(0):     will be used as the requested mode.
[    24.169] (==) NVIDIA(0): 
[    24.169] (II) NVIDIA(0): Validated MetaModes:
[    24.169] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    24.169] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    24.174] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    24.174] (--) NVIDIA(0):     option
[    24.174] (II) UnloadModule: "nouveau"
[    24.174] (II) Unloading nouveau
[    24.174] (II) UnloadModule: "modesetting"
[    24.174] (II) Unloading modesetting
[    24.174] (II) UnloadModule: "fbdev"
[    24.174] (II) Unloading fbdev
[    24.174] (II) UnloadSubModule: "fbdevhw"
[    24.174] (II) Unloading fbdevhw
[    24.174] (II) UnloadModule: "vesa"
[    24.174] (II) Unloading vesa
[    24.174] (--) Depth 24 pixmap format is 32 bpp
[    24.180] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    24.180] (II) NVIDIA:     access.
[    24.202] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[    24.251] (==) NVIDIA(0): Disabling shared memory pixmaps
[    24.251] (==) NVIDIA(0): Backing store enabled
[    24.252] (==) NVIDIA(0): Silken mouse enabled
[    24.252] (==) NVIDIA(0): DPMS enabled
[    24.252] (II) Loading sub module "dri2"
[    24.252] (II) LoadModule: "dri2"
[    24.252] (II) Module "dri2" already built-in
[    24.252] (II) NVIDIA(0): [DRI2] Setup complete
[    24.252] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    24.252] (--) RandR disabled
[    24.254] (II) SELinux: Disabled on system
[    24.255] (II) Initializing extension GLX
[    24.255] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.270] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.270] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.270] (II) LoadModule: "evdev"
[    24.270] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.270] (II) Module evdev: vendor="X.Org Foundation"
[    24.270]     compiled for 1.17.1, module version = 2.9.2
[    24.270]     Module class: X.Org XInput Driver
[    24.270]     ABI class: X.Org XInput driver, version 21.0
[    24.270] (II) Using input driver 'evdev' for 'Power Button'
[    24.270] (**) Power Button: always reports core events
[    24.270] (**) evdev: Power Button: Device: "/dev/input/event1"
[    24.270] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.270] (--) evdev: Power Button: Found keys
[    24.270] (II) evdev: Power Button: Configuring as keyboard
[    24.270] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.270] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    24.270] (**) Option "xkb_rules" "evdev"
[    24.270] (**) Option "xkb_model" "pc105"
[    24.270] (**) Option "xkb_layout" "de"
[    24.271] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    24.271] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.271] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.271] (II) Using input driver 'evdev' for 'Power Button'
[    24.271] (**) Power Button: always reports core events
[    24.271] (**) evdev: Power Button: Device: "/dev/input/event0"
[    24.271] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.271] (--) evdev: Power Button: Found keys
[    24.271] (II) evdev: Power Button: Configuring as keyboard
[    24.271] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    24.272] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    24.272] (**) Option "xkb_rules" "evdev"
[    24.272] (**) Option "xkb_model" "pc105"
[    24.272] (**) Option "xkb_layout" "de"
[    24.272] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event16)
[    24.272] (II) No input driver specified, ignoring this device.
[    24.272] (II) This device may have been added with another device file.
[    24.272] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    24.272] (II) No input driver specified, ignoring this device.
[    24.272] (II) This device may have been added with another device file.
[    24.272] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event18)
[    24.272] (II) No input driver specified, ignoring this device.
[    24.272] (II) This device may have been added with another device file.
[    24.272] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event19)
[    24.272] (II) No input driver specified, ignoring this device.
[    24.272] (II) This device may have been added with another device file.
[    24.273] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event5)
[    24.273] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[    24.273] (II) Using input driver 'evdev' for 'HID 046a:0023'
[    24.273] (**) HID 046a:0023: always reports core events
[    24.273] (**) evdev: HID 046a:0023: Device: "/dev/input/event5"
[    24.273] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[    24.273] (--) evdev: HID 046a:0023: Found keys
[    24.273] (II) evdev: HID 046a:0023: Configuring as keyboard
[    24.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb7/7-1/7-1.5/7-1.5:1.0/0003:046A:0023.0003/input/input8/event5"
[    24.273] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 8)
[    24.273] (**) Option "xkb_rules" "evdev"
[    24.273] (**) Option "xkb_model" "pc105"
[    24.273] (**) Option "xkb_layout" "de"
[    24.273] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event14)
[    24.273] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[    24.273] (II) Using input driver 'evdev' for 'HID 046a:0023'
[    24.273] (**) HID 046a:0023: always reports core events
[    24.273] (**) evdev: HID 046a:0023: Device: "/dev/input/event14"
[    24.273] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[    24.273] (--) evdev: HID 046a:0023: Found 1 mouse buttons
[    24.273] (--) evdev: HID 046a:0023: Found scroll wheel(s)
[    24.273] (--) evdev: HID 046a:0023: Found relative axes
[    24.273] (II) evdev: HID 046a:0023: Forcing relative x/y axes to exist.
[    24.273] (--) evdev: HID 046a:0023: Found absolute axes
[    24.273] (II) evdev: HID 046a:0023: Forcing absolute x/y axes to exist.
[    24.273] (--) evdev: HID 046a:0023: Found keys
[    24.273] (II) evdev: HID 046a:0023: Configuring as mouse
[    24.273] (II) evdev: HID 046a:0023: Configuring as keyboard
[    24.273] (II) evdev: HID 046a:0023: Adding scrollwheel support
[    24.273] (**) evdev: HID 046a:0023: YAxisMapping: buttons 4 and 5
[    24.273] (**) evdev: HID 046a:0023: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb7/7-1/7-1.5/7-1.5:1.1/0003:046A:0023.0004/input/input17/event14"
[    24.273] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 9)
[    24.273] (**) Option "xkb_rules" "evdev"
[    24.273] (**) Option "xkb_model" "pc105"
[    24.273] (**) Option "xkb_layout" "de"
[    24.273] (II) evdev: HID 046a:0023: initialized for relative axes.
[    24.273] (WW) evdev: HID 046a:0023: ignoring absolute axes.
[    24.274] (**) HID 046a:0023: (accel) keeping acceleration scheme 1
[    24.274] (**) HID 046a:0023: (accel) acceleration profile 0
[    24.274] (**) HID 046a:0023: (accel) acceleration factor: 2.000
[    24.274] (**) HID 046a:0023: (accel) acceleration threshold: 4
[    24.274] (II) config/udev: Adding input device Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 (/dev/input/event4)
[    24.274] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Applying InputClass "evdev pointer catchall"
[    24.274] (II) Using input driver 'evdev' for 'Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0'
[    24.274] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: always reports core events
[    24.274] (**) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Device: "/dev/input/event4"
[    24.328] (--) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Vendor 0x45e Product 0x7d
[    24.328] (--) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Found 3 mouse buttons
[    24.328] (--) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Found scroll wheel(s)
[    24.328] (--) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Found relative axes
[    24.328] (--) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Found x and y relative axes
[    24.328] (II) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Configuring as mouse
[    24.328] (II) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: Adding scrollwheel support
[    24.328] (**) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: YAxisMapping: buttons 4 and 5
[    24.328] (**) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.328] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb7/7-1/7-1.6/7-1.6:1.0/0003:045E:007D.0005/input/input7/event4"
[    24.328] (II) XINPUT: Adding extended input device "Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0" (type: MOUSE, id 10)
[    24.328] (II) evdev: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: initialized for relative axes.
[    24.328] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: (accel) keeping acceleration scheme 1
[    24.328] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: (accel) acceleration profile 0
[    24.328] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: (accel) acceleration factor: 2.000
[    24.328] (**) Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0: (accel) acceleration threshold: 4
[    24.328] (II) config/udev: Adding input device Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 (/dev/input/mouse1)
[    24.328] (II) No input driver specified, ignoring this device.
[    24.328] (II) This device may have been added with another device file.
[    24.328] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    24.328] (II) No input driver specified, ignoring this device.
[    24.328] (II) This device may have been added with another device file.
[    24.328] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    24.328] (II) No input driver specified, ignoring this device.
[    24.328] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event9)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event10)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event12)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event13)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.329] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    24.329] (II) No input driver specified, ignoring this device.
[    24.329] (II) This device may have been added with another device file.
[    24.330] (II) config/udev: Adding input device MOSART Semi. Rapoo 2.4G Wireless Touch Desktop  (/dev/input/event2)
[    24.330] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Applying InputClass "evdev keyboard catchall"
[    24.330] (II) Using input driver 'evdev' for 'MOSART Semi. Rapoo 2.4G Wireless Touch Desktop '
[    24.330] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : always reports core events
[    24.330] (**) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Device: "/dev/input/event2"
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Vendor 0x24ae Product 0x1001
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found keys
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Configuring as keyboard
[    24.330] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/usb5/5-2/5-2:1.0/0003:24AE:1001.0001/input/input5/event2"
[    24.330] (II) XINPUT: Adding extended input device "MOSART Semi. Rapoo 2.4G Wireless Touch Desktop " (type: KEYBOARD, id 11)
[    24.330] (**) Option "xkb_rules" "evdev"
[    24.330] (**) Option "xkb_model" "pc105"
[    24.330] (**) Option "xkb_layout" "de"
[    24.330] (II) config/udev: Adding input device MOSART Semi. Rapoo 2.4G Wireless Touch Desktop  (/dev/input/event3)
[    24.330] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Applying InputClass "evdev pointer catchall"
[    24.330] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Applying InputClass "evdev keyboard catchall"
[    24.330] (II) Using input driver 'evdev' for 'MOSART Semi. Rapoo 2.4G Wireless Touch Desktop '
[    24.330] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : always reports core events
[    24.330] (**) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Device: "/dev/input/event3"
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Vendor 0x24ae Product 0x1001
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found 9 mouse buttons
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found scroll wheel(s)
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found relative axes
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found x and y relative axes
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found absolute axes
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Forcing absolute x/y axes to exist.
[    24.330] (--) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Found keys
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Configuring as mouse
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Configuring as keyboard
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : Adding scrollwheel support
[    24.330] (**) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : YAxisMapping: buttons 4 and 5
[    24.330] (**) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.330] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/usb5/5-2/5-2:1.1/0003:24AE:1001.0002/input/input6/event3"
[    24.330] (II) XINPUT: Adding extended input device "MOSART Semi. Rapoo 2.4G Wireless Touch Desktop " (type: KEYBOARD, id 12)
[    24.330] (**) Option "xkb_rules" "evdev"
[    24.330] (**) Option "xkb_model" "pc105"
[    24.330] (**) Option "xkb_layout" "de"
[    24.330] (II) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : initialized for relative axes.
[    24.330] (WW) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : ignoring absolute axes.
[    24.331] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : (accel) keeping acceleration scheme 1
[    24.331] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : (accel) acceleration profile 0
[    24.331] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : (accel) acceleration factor: 2.000
[    24.331] (**) MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : (accel) acceleration threshold: 4
[    24.331] (II) config/udev: Adding input device MOSART Semi. Rapoo 2.4G Wireless Touch Desktop  (/dev/input/mouse0)
[    24.331] (II) No input driver specified, ignoring this device.
[    24.331] (II) This device may have been added with another device file.
[    24.331] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event15)
[    24.331] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    24.331] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    24.331] (**) Eee PC WMI hotkeys: always reports core events
[    24.331] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event15"
[    24.331] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    24.331] (--) evdev: Eee PC WMI hotkeys: Found keys
[    24.331] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    24.331] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input18/event15"
[    24.331] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 13)
[    24.331] (**) Option "xkb_rules" "evdev"
[    24.331] (**) Option "xkb_model" "pc105"
[    24.331] (**) Option "xkb_layout" "de"
[    24.515] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    24.515] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    24.515] (--) NVIDIA(GPU-0): 
[    24.519] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    24.519] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    24.519] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    24.519] (--) NVIDIA(GPU-0): 
[    24.531] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): connected
[    24.531] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): Internal TMDS
[    24.531] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): 340.0 MHz maximum pixel clock
[    24.531] (--) NVIDIA(GPU-0): 
[    24.531] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    24.531] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    24.531] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    24.531] (--) NVIDIA(GPU-0): 
[    24.531] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    24.531] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    24.531] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    24.531] (--) NVIDIA(GPU-0): 
[    24.532] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    24.532] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    24.532] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    24.532] (--) NVIDIA(GPU-0): 
[    24.645] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    24.645] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    24.645] (--) NVIDIA(GPU-0): 
[    24.647] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    24.647] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    24.647] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    24.647] (--) NVIDIA(GPU-0): 
[    24.658] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): connected
[    24.658] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): Internal TMDS
[    24.658] (--) NVIDIA(GPU-0): BenQ V2400Eco (DFP-1): 340.0 MHz maximum pixel clock
[    24.658] (--) NVIDIA(GPU-0): 
[    24.658] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    24.658] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    24.658] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    24.658] (--) NVIDIA(GPU-0): 
[    24.658] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    24.658] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    24.658] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    24.658] (--) NVIDIA(GPU-0): 
[    24.658] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    24.658] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    24.658] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    24.658] (--) NVIDIA(GPU-0): 

```

---

### Post by Yellow Pasque on 2016-04-06
Hmm. Your log looks good. Perhaps this link will help (though the exact commands may be a bit different since you have a different version of nvidia driver installed): [http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update](http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update)

---

### Post by MatthiasE on 2016-04-13
Thanks - but unfortunately it didn't help. 

These are the symbolic links that are connected to the nvidia-driver (version 340 is mentioned because I tried out this one when I created the links as it is explained in the link you posted):

```

lrwxrwxrwx 1 root root 15 Nov 16 18:32 /usr/lib32/nvidia-340/libGL.so.1 -> libGL.so.340.96
lrwxrwxrwx 1 root root 10 Nov 16 18:32 /usr/lib32/nvidia-340/libGL.so -> libGL.so.1
-rw-r--r-- 1 root root 1075136 Nov  9 07:11 /usr/lib32/nvidia-340/libGL.so.340.96
lrwxrwxrwx 1 root root 30 Apr 13 10:06 /usr/local/lib/libGL.so.1.2.0 -> /usr/lib/nvidia-340/libGL.so.1
lrwxrwxrwx 1 root root 14 Feb 23 21:13 /usr/lib/x86_64-linux-gnu/libGL.so.1 -> libGL.so.1.2.0
-rw-r--r-- 1 root root 619000 Feb 23 21:13 /usr/lib/x86_64-linux-gnu/libGL.so.1.2.0
lrwxrwxrwx 1 root root 14 Feb 23 20:46 /usr/lib/i386-linux-gnu/libGL.so.1 -> libGL.so.1.2.0
-rw-r--r-- 1 root root 689788 Feb 23 20:46 /usr/lib/i386-linux-gnu/libGL.so.1.2.0
lrwxrwxrwx 1 root root 15 Nov 16 18:32 /usr/lib/nvidia-340/libGL.so.1 -> libGL.so.340.96
lrwxrwxrwx 1 root root 10 Nov 16 18:32 /usr/lib/nvidia-340/libGL.so -> libGL.so.1
-rw-r--r-- 1 root root 1267768 Nov  9 07:05 /usr/lib/nvidia-340/libGL.so.340.96

```

Maybe you can identify if there's a link missing or wrong …

Thanks for your help!

---

