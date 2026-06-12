---
title: "Replaced Mobo:  Now no video"
date: 2017-09-17
forum: Hardware
---

### Post by alabamatoy2 on 2017-09-17
Ubuntu 16.04 desktop.  Replaced the motherboard (substantial upgrade).  Machine is working fantastic except....no video.  I can get to it with webmin, and everything seems to be running and otherwise working correctly.

lshw produces:
```
**> lshw -class video**
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:125 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)
```

When I start the machine, the BIOS displays correctly, then I get the blank purple ubuntu boot screen, then video goes completely off (ie monitor says "no input") yet the PC is running correctly.

Suggestions?  I dont know where to start.  Its as though its using the previos MB video drivers and I dsont know how to tell it to revert to default.

---

### Post by Autodave on 2017-09-17
Are you using a seperate video cards or onboard video?  What video card?

---

### Post by ajgreeny on 2017-09-17
What graphics did the previous motherboard use? 
You might still have a now unnecessary and confusing driver installed if the old one was needing another driver.

---

### Post by alabamatoy2 on 2017-09-17
> **Autodave said:**
> Are you using a seperate video cards or onboard  video?  What video card?  No separate card, its whatever is on  the MB.

> **ajgreeny said:**
> What graphics did the previous motherboard use?   I had no separate card, and AFAICR, I never did anything related to the video, it worked from day one as a fresh install.  I mean I never installed any video drivers after I installed the OS.
> **ajgreeny said:**
>  You might still have a now unnecessary and confusing driver installed if the old one was needing another driver.  This is exactly what I was thinking, but I dont know where to begin to remove the old one(s) or force the OS to go through its initial recognition process like it would on a fresh install.

---

### Post by Yellow Pasque on 2017-09-18
> This is exactly what I was thinking, but I dont know where to begin to remove the old one(s) or force the OS to go through its initial recognition process like it would on a fresh install. 

If you didn't install any proprietary video driver(s), you don't need to remove anything. When the Xserver starts, it will automatically match the best video driver each time (unless you have a custom xorg.conf file that specifies the driver).

Can you boot with nomodeset boot paramter? If so, copy/paste your /var/log/Xorg.0.log.old file here. Use code tags as it's a lot of text.

My initial hunch is that you are using the graphics stack that came with Ubuntu 16.04.1 and you need to move up to a newer version because you have a recent CPU/GPU. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
But before you do anything, let's look at the Xorg log.

---

### Post by oldfred on 2017-09-18
In addition to all the good info above what was old motherboard & what is new motherboard?

And in addition to nomodeset as boot option can you boot recovery mode, second in grub menu under Advanced Options.
If one install, you may need to hold shift key to see grub menu or if UEFI press escape key before grub menu, just at end of UEFI/BIOS screen.

---

### Post by alabamatoy2 on 2017-09-18
> **Temüjin said:**
> Can you boot with nomodeset boot paramter? If so, copy/paste your /var/log/Xorg.0.log.old file here. Use code tags as it's a lot of text.

adding the nomodeset allowed me to have a GUI.  Its wretched, 640X480 and half off the screen, but its there, so you have definitely sent me in the right direction.  I'm learning something here!

```
[    23.402] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    23.402] X Protocol Version 11, Revision 0
[    23.402] Build Operating System: Linux 4.4.0-83-generic x86_64 Ubuntu
[    23.402] Current Operating System: Linux [fqdn].com 4.4.0-93-generic #116-Ubuntu SMP Fri Aug 11 21:17:51 UTC 2017 x86_64
[    23.402] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-93-generic root=UUID=201dca4c-8a58-4a38-9cd9-8771e8691ad8 ro quiet splash nomodeset vt.handoff=7
[    23.402] Build Date: 17 July 2017  05:05:12PM
[    23.402] xorg-server 2:1.18.4-0ubuntu0.3 (For technical support please see http://www.ubuntu.com/support) 
[    23.402] Current version of pixman: 0.33.6
[    23.402]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.402] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.402] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 18 18:47:46 2017
[    23.592] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.593] (==) No Layout section.  Using the first Screen section.
[    23.593] (==) No screen section available. Using defaults.
[    23.593] (**) |-->Screen "Default Screen Section" (0)
[    23.593] (**) |   |-->Monitor "<default monitor>"
[    24.157] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.157] (==) Automatically adding devices
[    24.157] (==) Automatically enabling devices
[    24.157] (==) Automatically adding GPU devices
[    24.157] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    24.157] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.157]     Entry deleted from font path.
[    24.157] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.157]     Entry deleted from font path.
[    24.157] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.157]     Entry deleted from font path.
[    24.157] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.157]     Entry deleted from font path.
[    24.157] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.157]     Entry deleted from font path.
[    24.157] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.157] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.157] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.161] (II) Loader magic: 0x5cbc861dc0
[    24.161] (II) Module ABI versions:
[    24.161]     X.Org ANSI C Emulation: 0.4
[    24.161]     X.Org Video Driver: 20.0
[    24.161]     X.Org XInput driver : 22.1
[    24.161]     X.Org Server Extension : 9.0
[    24.162] (++) using VT number 7

[    24.162] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    24.162] (--) PCI:*(0:0:2:0) 8086:5912:1458:d000 rev 4, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    24.162] (II) LoadModule: "glx"
[    24.193] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.064] (II) Module glx: vendor="X.Org Foundation"
[    25.064]     compiled for 1.18.4, module version = 1.0.0
[    25.064]     ABI class: X.Org Server Extension, version 9.0
[    25.064] (==) AIGLX enabled
[    25.064] (==) Matched intel as autoconfigured driver 0
[    25.064] (==) Matched modesetting as autoconfigured driver 1
[    25.064] (==) Matched fbdev as autoconfigured driver 2
[    25.064] (==) Matched vesa as autoconfigured driver 3
[    25.064] (==) Assigned the driver to the xf86ConfigLayout
[    25.064] (II) LoadModule: "intel"
[    25.064] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.112] (II) Module intel: vendor="X.Org Foundation"
[    25.112]     compiled for 1.18.4, module version = 2.99.917
[    25.112]     Module class: X.Org Video Driver
[    25.112]     ABI class: X.Org Video Driver, version 20.0
[    25.112] (II) LoadModule: "modesetting"
[    25.112] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.112] (II) Module modesetting: vendor="X.Org Foundation"
[    25.112]     compiled for 1.18.4, module version = 1.18.4
[    25.112]     Module class: X.Org Video Driver
[    25.112]     ABI class: X.Org Video Driver, version 20.0
[    25.112] (II) LoadModule: "fbdev"
[    25.112] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.112] (II) Module fbdev: vendor="X.Org Foundation"
[    25.112]     compiled for 1.18.1, module version = 0.4.4
[    25.112]     Module class: X.Org Video Driver
[    25.112]     ABI class: X.Org Video Driver, version 20.0
[    25.112] (II) LoadModule: "vesa"
[    25.112] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.112] (II) Module vesa: vendor="X.Org Foundation"
[    25.112]     compiled for 1.18.1, module version = 2.3.4
[    25.112]     Module class: X.Org Video Driver
[    25.112]     ABI class: X.Org Video Driver, version 20.0
[    25.112] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    25.112] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    25.112] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    25.112] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    25.112] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.112] (II) FBDEV: driver for framebuffer: fbdev
[    25.112] (II) VESA: driver for VESA chipsets: vesa
[    25.184] (EE) open /dev/dri/card0: No such file or directory
[    25.184] (WW) Falling back to old probe method for modesetting
[    25.184] (EE) open /dev/dri/card0: No such file or directory
[    25.184] (II) Loading sub module "fbdevhw"
[    25.184] (II) LoadModule: "fbdevhw"
[    25.184] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.184] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.184]     compiled for 1.18.4, module version = 0.0.2
[    25.184]     ABI class: X.Org Video Driver, version 20.0
[    25.184] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    25.184] (II) FBDEV(1): using default device
[    25.184] (WW) Falling back to old probe method for vesa
[    25.184] (EE) Screen 0 deleted because of no matching config section.
[    25.184] (II) UnloadModule: "modesetting"
[    25.184] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.184] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    25.184] (==) FBDEV(0): RGB weight 888
[    25.184] (==) FBDEV(0): Default visual is TrueColor
[    25.184] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.184] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[    25.184] (II) FBDEV(0): checking modes against framebuffer device...
[    25.184] (II) FBDEV(0): checking modes against monitor...
[    25.184] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    25.184] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    25.184] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    25.184] (==) FBDEV(0): DPI set to (96, 96)
[    25.184] (II) Loading sub module "fb"
[    25.184] (II) LoadModule: "fb"
[    25.184] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.209] (II) Module fb: vendor="X.Org Foundation"
[    25.209]     compiled for 1.18.4, module version = 1.0.0
[    25.209]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.209] (**) FBDEV(0): using shadow framebuffer
[    25.209] (II) Loading sub module "shadow"
[    25.209] (II) LoadModule: "shadow"
[    25.209] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    25.239] (II) Module shadow: vendor="X.Org Foundation"
[    25.239]     compiled for 1.18.4, module version = 1.1.0
[    25.239]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.239] (II) UnloadModule: "vesa"
[    25.239] (II) Unloading vesa
[    25.240] (==) Depth 24 pixmap format is 32 bpp
[    25.240] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    25.294] (==) FBDEV(0): Backing store enabled
[    25.294] (==) FBDEV(0): DPMS enabled
[    25.295] (==) RandR enabled
[    25.298] (II) SELinux: Disabled on system
[    25.298] (II) AIGLX: Screen 0 is not DRI2 capable
[    25.298] (EE) AIGLX: reverting to software rendering
[    26.645] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.645] (II) AIGLX: Loaded and initialized swrast
[    26.645] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    26.826] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    26.826] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.826] (II) LoadModule: "evdev"
[    26.826] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.852] (II) Module evdev: vendor="X.Org Foundation"
[    26.852]     compiled for 1.18.1, module version = 2.10.1
[    26.852]     Module class: X.Org XInput Driver
[    26.852]     ABI class: X.Org XInput driver, version 22.1
[    26.852] (II) Using input driver 'evdev' for 'Power Button'
[    26.852] (**) Power Button: always reports core events
[    26.852] (**) evdev: Power Button: Device: "/dev/input/event2"
[    26.852] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.852] (--) evdev: Power Button: Found keys
[    26.852] (II) evdev: Power Button: Configuring as keyboard
[    26.852] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    26.852] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.852] (**) Option "xkb_rules" "evdev"
[    26.852] (**) Option "xkb_model" "pc105"
[    26.852] (**) Option "xkb_layout" "us"
[    26.853] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.853] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.853] (II) Using input driver 'evdev' for 'Power Button'
[    26.853] (**) Power Button: always reports core events
[    26.853] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.853] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.853] (--) evdev: Power Button: Found keys
[    26.853] (II) evdev: Power Button: Configuring as keyboard
[    26.853] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    26.853] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.853] (**) Option "xkb_rules" "evdev"
[    26.853] (**) Option "xkb_model" "pc105"
[    26.853] (**) Option "xkb_layout" "us"
[    26.853] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    26.853] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.853] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.853] (**) Sleep Button: always reports core events
[    26.853] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    26.853] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    26.853] (--) evdev: Sleep Button: Found keys
[    26.853] (II) evdev: Sleep Button: Configuring as keyboard
[    26.853] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    26.853] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    26.853] (**) Option "xkb_rules" "evdev"
[    26.853] (**) Option "xkb_model" "pc105"
[    26.853] (**) Option "xkb_layout" "us"
[    26.854] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event3)
[    26.854] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    26.854] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    26.854] (**) Dell Dell USB Keyboard: always reports core events
[    26.854] (**) evdev: Dell Dell USB Keyboard: Device: "/dev/input/event3"
[    26.854] (--) evdev: Dell Dell USB Keyboard: Vendor 0x413c Product 0x2105
[    26.854] (--) evdev: Dell Dell USB Keyboard: Found keys
[    26.854] (II) evdev: Dell Dell USB Keyboard: Configuring as keyboard
[    26.854] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8.1/1-8.1:1.0/0003:413C:2105.0002/input/input6/event3"
[    26.854] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD, id 9)
[    26.854] (**) Option "xkb_rules" "evdev"
[    26.854] (**) Option "xkb_model" "pc105"
[    26.854] (**) Option "xkb_layout" "us"
[    26.854] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    26.854] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    26.854] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    26.854] (**) USB Optical Mouse: always reports core events
[    26.854] (**) evdev: USB Optical Mouse: Device: "/dev/input/event4"
[    26.854] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d22
[    26.854] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    26.854] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    26.854] (--) evdev: USB Optical Mouse: Found relative axes
[    26.854] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    26.854] (II) evdev: USB Optical Mouse: Configuring as mouse
[    26.854] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    26.854] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    26.854] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.854] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8.2/1-8.2:1.0/0003:0461:4D22.0003/input/input7/event4"
[    26.854] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 10)
[    26.854] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    26.854] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    26.854] (**) USB Optical Mouse: (accel) acceleration profile 0
[    26.854] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    26.854] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    26.854] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    26.854] (II) No input driver specified, ignoring this device.
[    26.854] (II) This device may have been added with another device file.
[    26.855] (II) config/udev: Adding input device No brand 2Port KVMSwicther (/dev/input/event5)
[    26.855] (**) No brand 2Port KVMSwicther: Applying InputClass "evdev keyboard catchall"
[    26.855] (II) Using input driver 'evdev' for 'No brand 2Port KVMSwicther'
[    26.855] (**) No brand 2Port KVMSwicther: always reports core events
[    26.855] (**) evdev: No brand 2Port KVMSwicther: Device: "/dev/input/event5"
[    26.855] (--) evdev: No brand 2Port KVMSwicther: Vendor 0x10d5 Product 0x55a2
[    26.855] (--) evdev: No brand 2Port KVMSwicther: Found keys
[    26.855] (II) evdev: No brand 2Port KVMSwicther: Configuring as keyboard
[    26.855] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8.3/1-8.3:1.0/0003:10D5:55A2.0004/input/input8/event5"
[    26.855] (II) XINPUT: Adding extended input device "No brand 2Port KVMSwicther" (type: KEYBOARD, id 11)
[    26.855] (**) Option "xkb_rules" "evdev"
[    26.855] (**) Option "xkb_model" "pc105"
[    26.855] (**) Option "xkb_layout" "us"
[    26.855] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    26.855] (II) No input driver specified, ignoring this device.
[    26.855] (II) This device may have been added with another device file.
[    26.855] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    26.855] (II) No input driver specified, ignoring this device.
[    26.855] (II) This device may have been added with another device file.
[    26.855] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event9)
[    26.855] (II) No input driver specified, ignoring this device.
[    26.855] (II) This device may have been added with another device file.
[    26.855] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event10)
[    26.855] (II) No input driver specified, ignoring this device.
[    26.855] (II) This device may have been added with another device file.
[    26.855] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[    26.855] (II) No input driver specified, ignoring this device.
[    26.855] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event12)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event13)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event14)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event15)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event16)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[    26.856] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    26.856] (II) No input driver specified, ignoring this device.
[    26.856] (II) This device may have been added with another device file.
[   767.024] (II) evdev: No brand 2Port KVMSwicther: Close
[   767.024] (II) UnloadModule: "evdev"
[   767.024] (II) evdev: USB Optical Mouse: Close
[   767.024] (II) UnloadModule: "evdev"
[   767.024] (II) evdev: Dell Dell USB Keyboard: Close
[   767.025] (II) UnloadModule: "evdev"
[   767.025] (II) evdev: Sleep Button: Close
[   767.025] (II) UnloadModule: "evdev"
[   767.025] (II) evdev: Power Button: Close
[   767.025] (II) UnloadModule: "evdev"
[   767.025] (II) evdev: Power Button: Close
[   767.025] (II) UnloadModule: "evdev"
[   767.029] (II) Server terminated successfully (0). Closing log file.


```

---

### Post by Yellow Pasque on 2017-09-19
Hmm. I was looking for a log from your failed boot (one where you tried to boot without nomodeset). That log shows you booting with nomodeset. It does tell us that you're using Intel HD 630, which is a very recent GPU.
[http://pci-ids.ucw.cz/read/PC/8086/5912](http://pci-ids.ucw.cz/read/PC/8086/5912)

I would try a LiveUSB/CD of Ubuntu 16.04.3, and if that works, then I would try moving forward with LTS enablement stack in the link I posted previously.

> Its wretched, 640X480 and half off the screen
If you're still encountering issues and want a better resolution, try uninstalling the xserver-xorg-video-fbdev package. Generic VESA driver should at least give you 1024x768.

---

### Post by alabamatoy2 on 2017-09-21
> **Temüjin said:**
> If you're still encountering issues and want a better resolution, try uninstalling the xserver-xorg-video-fbdev package. Generic VESA driver should at least give you 1024x768.

This gave me quite a fright.  Removed this package, rebooted and it crashed somehow.  Im apparently not very good at diagnosing such things.  Rebooted again, and grub gave me a whole slew of options.  I simply picked the top one on the list, and it booted right up, and has beautiful 1024X768 as you predicted.  For the moment, I'm happy.  I will get around to installing the LTS enablement stack as you suggested.

Thank everyone very much for the assistance.  I have learned more about the system, and its working again!!

---

