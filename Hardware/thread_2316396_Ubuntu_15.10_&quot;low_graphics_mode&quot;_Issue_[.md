---
title: "Ubuntu 15.10 &quot;low graphics mode&quot; Issue [GeForce 630m]"
date: 2016-03-07
forum: Hardware
---

### Post by daniii10 on 2016-03-07
I always had problems with Nvidia integrated graphic card, but after many trials I finally had it work. Until yesterday I got some issues.
I install Intel driver from [here]("https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0") (I know it was stupid), and it's probably ruined my Nvidia driver. After installing the Intel graphic driver I got the "low graphics mode" screen, so I purged Nvidia and got my laptop back to work, but I don't have Nvidia driver installed and not using my Nvidia card. So I installed Nvidia driver from 'Ubuntu-Drivers' and rebooted the machines and still the 'low graphics mode' screen again. Apparently for now my laptop can work only with the Intel card and with the command ```
sudo prime-select intel
``` 
But if I select Nvidia I get the low graphics mode window again.

Here is the long file:

```
[   185.594] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[   185.594] X Protocol Version 11, Revision 0
[   185.594] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[   185.594] Current Operating System: Linux daniel-Inspiron-5720 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64
[   185.594] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic.efi.signed root=UUID=74974142-c5de-406c-83aa-89b1d871a6f6 ro quiet splash vt.handoff=7
[   185.594] Build Date: 12 November 2015  05:33:29PM
[   185.594] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[   185.594] Current version of pixman: 0.32.6
[   185.594]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   185.594] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   185.594] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Mar  7 18:21:04 2016
[   185.594] (==) Using config file: "/etc/X11/xorg.conf"
[   185.594] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   185.595] Data incomplete in file /etc/X11/xorg.conf
    Undefined Screen "nvidia" referenced by ServerLayout "layout".
[   185.595] (EE) Problem parsing the config file
[   185.595] (EE) Error parsing the config file
[   185.595] (EE) 
Fatal server error:
[   185.595] (EE) no screens found(EE) 
[   185.595] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   185.595] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   185.595] (EE) 
[   185.595] (EE) Server terminated with error (1). Closing log file.
```

Please someone help me this is the only thing that bothers me in Ubuntu.
Thanks.

---

### Post by Yellow Pasque on 2016-03-08
There's an error in your /etc/X11/xorg.conf file. Try backing it up and deleting it.

---

### Post by daniii10 on 2016-03-08
Thank you for the respond.
Which one should I delete? or just all of them?

[[IMG]http://s22.postimg.org/e48zqgdyl/Xorg_file_edited.jpg[/IMG]]("http://postimg.org/image/e48zqgdyl/")

---

### Post by Bashing-om on 2016-03-08
daniii10; Hello;;

None of them are relevant; delete them all, is what i would do. Keeping only "xorg.conf.failsafe" all the others are of a backup nature and the system only looks for a file named  "/etc/X11/xorg.conf ". In this case the file does not exist.
As you profess that you also have Intel graphics that implies a hybrid graphic's situation. In this context the file " xorg.conf " is required .

one can generate a new xorg.conf file:
One way is terminal command:
```

sudo nvidia-xconfig

```
IF the proprietary driver is installed and the helper tool ' nvidia-prime' is installed :
```

dpkg -l | grep -i nvidia

```
should now workie great, last long time.

IF all appears in order, and the xorg file has been generated; reboot to see the effect.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
Thank you. Should I type the command when prime-select Nvidia before execute the comman "sudo nvidia-xconfig" ? because now it works on Intel. Or it doesn't matter?
I have the nvidia driver and nvidia-prime installed.

---

### Post by Bashing-om on 2016-03-08
daniii10; Well,

Should not matter, all we are doing is having the system generate the file. The kernel knows what is.

[INDENT][INDENT]faith
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
OK I execute the command "sudo nvidia-xconfig" It's still doesn't work. I also tried to execute the command on tty after I got the 'low graphics mode' screen and tried to restart lightdm and it doesn't work.

This is the terminal output:

[[IMG]http://s12.postimg.org/vui5w59eh/Terminal_output.jpg[/IMG]]("http://postimg.org/image/vui5w59eh/")

And this is the output for the command 'dpkg -l | grep -i nvidia'

[URL="http://postimg.org/image/oylw28wyt/"][IMG]http://s10.postimg.org/oylw28wyt/Terminal_output2.jpg[/IMG]

[/URL]Thank you for your help.

---

### Post by Bashing-om on 2016-03-08
daniii10; Yuk;

That does not look good. None of it .
Appears that you have attempted several driver installs.
HUH ?? xorg-server not found ??????

Let's now get a look at what X is doing. I do need to see this in a text file NOT from an image , Can not work reliably from an image file.
code tags is the answer for this:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

post back - between code tags - the output of terminal command:
```

cat /var/log/Xorg.0.log 

```
Also we want to make sure that the driver version matches the Nvidia card; 
post also:
```

lspci -k | grep -EA2 'VGA|3D'

```
so we know what it is that we are working with.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
Ok this is the respond for 'cat /var/log/Xorg.0.log'

```
[    35.818] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    35.818] X Protocol Version 11, Revision 0
[    35.818] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    35.818] Current Operating System: Linux daniel-Inspiron-5720 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64
[    35.818] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic.efi.signed root=UUID=74974142-c5de-406c-83aa-89b1d871a6f6 ro quiet splash vt.handoff=7
[    35.818] Build Date: 12 November 2015  05:33:29PM
[    35.818] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[    35.818] Current version of pixman: 0.32.6
[    35.818]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    35.818] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    35.818] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  8 15:52:43 2016
[    35.848] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.879] (==) No Layout section.  Using the first Screen section.
[    35.879] (==) No screen section available. Using defaults.
[    35.879] (**) |-->Screen "Default Screen Section" (0)
[    35.879] (**) |   |-->Monitor "<default monitor>"
[    35.879] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    35.879] (==) Automatically adding devices
[    35.879] (==) Automatically enabling devices
[    35.879] (==) Automatically adding GPU devices
[    35.879] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    35.879]     Entry deleted from font path.
[    35.879] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    35.879]     Entry deleted from font path.
[    35.879] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    35.879]     Entry deleted from font path.
[    35.879] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    35.879]     Entry deleted from font path.
[    35.879] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    35.879]     Entry deleted from font path.
[    35.879] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    35.879] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.879] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.879] (II) Loader magic: 0x55e96f3a4d40
[    35.879] (II) Module ABI versions:
[    35.879]     X.Org ANSI C Emulation: 0.4
[    35.879]     X.Org Video Driver: 19.0
[    35.879]     X.Org XInput driver : 21.0
[    35.879]     X.Org Server Extension : 9.0
[    35.880] (II) xfree86: Adding drm device (/dev/dri/card0)
[    35.881] (--) PCI:*(0:0:2:0) 8086:0166:1028:0565 rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    35.881] (--) PCI: (0:1:0:0) 10de:1140:1028:0565 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128
[    35.881] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    35.881] (II) "glx" will be loaded by default.
[    35.881] (II) LoadModule: "glx"
[    35.904] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    36.485] (II) Module glx: vendor="X.Org Foundation"
[    36.485]     compiled for 1.17.2, module version = 1.0.0
[    36.485]     ABI class: X.Org Server Extension, version 9.0
[    36.485] (==) AIGLX enabled
[    36.485] (==) Matched intel as autoconfigured driver 0
[    36.485] (==) Matched intel as autoconfigured driver 1
[    36.485] (==) Matched modesetting as autoconfigured driver 2
[    36.485] (==) Matched fbdev as autoconfigured driver 3
[    36.485] (==) Matched vesa as autoconfigured driver 4
[    36.485] (==) Assigned the driver to the xf86ConfigLayout
[    36.485] (II) LoadModule: "intel"
[    36.485] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    36.580] (II) Module intel: vendor="X.Org Foundation"
[    36.580]     compiled for 1.17.2, module version = 2.99.917
[    36.580]     Module class: X.Org Video Driver
[    36.580]     ABI class: X.Org Video Driver, version 19.0
[    36.580] (II) LoadModule: "modesetting"
[    36.580] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    36.599] (II) Module modesetting: vendor="X.Org Foundation"
[    36.599]     compiled for 1.17.2, module version = 1.17.2
[    36.599]     Module class: X.Org Video Driver
[    36.599]     ABI class: X.Org Video Driver, version 19.0
[    36.599] (II) LoadModule: "fbdev"
[    36.600] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    36.600] (II) Module fbdev: vendor="X.Org Foundation"
[    36.600]     compiled for 1.17.1, module version = 0.4.4
[    36.600]     Module class: X.Org Video Driver
[    36.600]     ABI class: X.Org Video Driver, version 19.0
[    36.600] (II) LoadModule: "vesa"
[    36.600] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    36.617] (II) Module vesa: vendor="X.Org Foundation"
[    36.617]     compiled for 1.17.1, module version = 2.3.4
[    36.617]     Module class: X.Org Video Driver
[    36.617]     ABI class: X.Org Video Driver, version 19.0
[    36.617] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    36.617] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    36.617] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    36.617] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    36.617] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    36.617] (II) FBDEV: driver for framebuffer: fbdev
[    36.617] (II) VESA: driver for VESA chipsets: vesa
[    36.617] (++) using VT number 7

[    36.618] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150731
[    36.618] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4 (Robert Ancell <robert.ancell@canonical.com>)
[    36.618] (II) intel(0): SNA compiled for use with valgrind
[    36.619] (WW) Falling back to old probe method for modesetting
[    36.620] (WW) Falling back to old probe method for fbdev
[    36.620] (II) Loading sub module "fbdevhw"
[    36.620] (II) LoadModule: "fbdevhw"
[    36.620] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    36.620] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.620]     compiled for 1.17.2, module version = 0.0.2
[    36.620]     ABI class: X.Org Video Driver, version 19.0
[    36.620] (WW) Falling back to old probe method for vesa
[    36.621] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    36.621] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx; using a maximum of 4 threads
[    36.621] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    36.621] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    36.621] (==) intel(0): RGB weight 888
[    36.621] (==) intel(0): Default visual is TrueColor
[    36.621] (II) intel(0): Output LVDS1 has no monitor section
[    36.632] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    36.632] (II) intel(0): Enabled output LVDS1
[    36.632] (II) intel(0): Output VGA1 has no monitor section
[    36.632] (II) intel(0): Enabled output VGA1
[    36.632] (II) intel(0): Output HDMI1 has no monitor section
[    36.632] (II) intel(0): Enabled output HDMI1
[    36.632] (II) intel(0): Output DP1 has no monitor section
[    36.632] (II) intel(0): Enabled output DP1
[    36.632] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    36.632] (II) intel(0): Output VIRTUAL1 has no monitor section
[    36.632] (II) intel(0): Enabled output VIRTUAL1
[    36.632] (--) intel(0): Output LVDS1 using initial mode 1600x900 on pipe 0
[    36.632] (==) intel(0): TearFree disabled
[    36.632] (==) intel(0): DPI set to (96, 96)
[    36.632] (II) Loading sub module "dri2"
[    36.632] (II) LoadModule: "dri2"
[    36.632] (II) Module "dri2" already built-in
[    36.632] (II) Loading sub module "present"
[    36.632] (II) LoadModule: "present"
[    36.632] (II) Module "present" already built-in
[    36.736] (II) UnloadModule: "modesetting"
[    36.736] (II) Unloading modesetting
[    36.736] (II) UnloadModule: "fbdev"
[    36.736] (II) Unloading fbdev
[    36.736] (II) UnloadSubModule: "fbdevhw"
[    36.736] (II) Unloading fbdevhw
[    36.736] (II) UnloadModule: "vesa"
[    36.736] (II) Unloading vesa
[    36.736] (==) Depth 24 pixmap format is 32 bpp
[    36.739] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    36.739] (==) intel(0): Backing store enabled
[    36.739] (==) intel(0): Silken mouse enabled
[    36.739] (II) intel(0): HW Cursor enabled
[    36.739] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.739] (==) intel(0): DPMS enabled
[    36.739] (==) intel(0): Display hotplug detection enabled
[    36.739] (II) intel(0): [DRI2] Setup complete
[    36.739] (II) intel(0): [DRI2]   DRI driver: i965
[    36.739] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    36.739] (II) intel(0): direct rendering: DRI2 enabled
[    36.739] (II) intel(0): hardware support for Present enabled
[    36.739] (--) RandR disabled
[    36.743] (II) SELinux: Disabled on system
[    37.215] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    37.215] (II) AIGLX: enabled GLX_ARB_create_context
[    37.215] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    37.215] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    37.215] (II) AIGLX: enabled GLX_INTEL_swap_event
[    37.215] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    37.215] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    37.215] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    37.215] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    37.215] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    37.215] (II) AIGLX: Loaded and initialized i965
[    37.215] (II) GLX: Initialized DRI2 GL provider for screen 0
[    37.233] (II) intel(0): switch to mode 1600x900@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    37.233] (II) intel(0): Setting screen physical size to 423 x 238
[    37.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.343] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    37.343] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.343] (II) LoadModule: "evdev"
[    37.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.569] (II) Module evdev: vendor="X.Org Foundation"
[    37.569]     compiled for 1.17.1, module version = 2.9.2
[    37.569]     Module class: X.Org XInput Driver
[    37.569]     ABI class: X.Org XInput driver, version 21.0
[    37.569] (II) Using input driver 'evdev' for 'Power Button'
[    37.569] (**) Power Button: always reports core events
[    37.569] (**) evdev: Power Button: Device: "/dev/input/event3"
[    37.569] (--) evdev: Power Button: Vendor 0 Product 0x1
[    37.569] (--) evdev: Power Button: Found keys
[    37.569] (II) evdev: Power Button: Configuring as keyboard
[    37.569] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    37.569] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    37.569] (**) Option "xkb_rules" "evdev"
[    37.569] (**) Option "xkb_model" "pc105"
[    37.569] (**) Option "xkb_layout" "us"
[    37.570] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    37.570] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    37.570] (II) Using input driver 'evdev' for 'Video Bus'
[    37.570] (**) Video Bus: always reports core events
[    37.570] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    37.570] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    37.570] (--) evdev: Video Bus: Found keys
[    37.570] (II) evdev: Video Bus: Configuring as keyboard
[    37.570] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    37.570] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    37.570] (**) Option "xkb_rules" "evdev"
[    37.570] (**) Option "xkb_model" "pc105"
[    37.570] (**) Option "xkb_layout" "us"
[    37.571] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    37.571] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    37.571] (II) Using input driver 'evdev' for 'Video Bus'
[    37.571] (**) Video Bus: always reports core events
[    37.571] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    37.571] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    37.571] (--) evdev: Video Bus: Found keys
[    37.571] (II) evdev: Video Bus: Configuring as keyboard
[    37.571] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30/LNXVIDEO:00/input/input7/event5"
[    37.571] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    37.571] (**) Option "xkb_rules" "evdev"
[    37.571] (**) Option "xkb_model" "pc105"
[    37.571] (**) Option "xkb_layout" "us"
[    37.571] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.571] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.571] (II) Using input driver 'evdev' for 'Power Button'
[    37.571] (**) Power Button: always reports core events
[    37.571] (**) evdev: Power Button: Device: "/dev/input/event0"
[    37.571] (--) evdev: Power Button: Vendor 0 Product 0x1
[    37.571] (--) evdev: Power Button: Found keys
[    37.571] (II) evdev: Power Button: Configuring as keyboard
[    37.571] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    37.571] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    37.571] (**) Option "xkb_rules" "evdev"
[    37.571] (**) Option "xkb_model" "pc105"
[    37.571] (**) Option "xkb_layout" "us"
[    37.572] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    37.572] (II) No input driver specified, ignoring this device.
[    37.572] (II) This device may have been added with another device file.
[    37.572] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    37.572] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    37.572] (II) Using input driver 'evdev' for 'Sleep Button'
[    37.572] (**) Sleep Button: always reports core events
[    37.572] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    37.572] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    37.572] (--) evdev: Sleep Button: Found keys
[    37.572] (II) evdev: Sleep Button: Configuring as keyboard
[    37.572] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    37.572] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    37.572] (**) Option "xkb_rules" "evdev"
[    37.572] (**) Option "xkb_model" "pc105"
[    37.572] (**) Option "xkb_layout" "us"
[    37.573] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event7)
[    37.573] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    37.573] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[    37.573] (**)  USB OPTICAL MOUSE: always reports core events
[    37.573] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event7"
[    37.628] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x425 Product 0x1
[    37.628] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[    37.628] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[    37.628] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[    37.628] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[    37.628] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[    37.628] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[    37.628] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    37.628] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.628] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:0425:0001.0001/input/input9/event7"
[    37.628] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 11)
[    37.628] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[    37.628] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    37.628] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[    37.628] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    37.628] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    37.628] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    37.629] (II) No input driver specified, ignoring this device.
[    37.629] (II) This device may have been added with another device file.
[    37.629] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event13)
[    37.629] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    37.629] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    37.629] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    37.629] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event13"
[    37.629] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xbda Product 0x58bf
[    37.629] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    37.629] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    37.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/input/input14/event13"
[    37.629] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    37.629] (**) Option "xkb_rules" "evdev"
[    37.629] (**) Option "xkb_model" "pc105"
[    37.629] (**) Option "xkb_layout" "us"
[    37.630] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    37.630] (II) No input driver specified, ignoring this device.
[    37.630] (II) This device may have been added with another device file.
[    37.630] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    37.630] (II) No input driver specified, ignoring this device.
[    37.630] (II) This device may have been added with another device file.
[    37.630] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    37.630] (II) No input driver specified, ignoring this device.
[    37.630] (II) This device may have been added with another device file.
[    37.630] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    37.630] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    37.630] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    37.630] (**) AT Translated Set 2 keyboard: always reports core events
[    37.630] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    37.630] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    37.630] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    37.630] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    37.630] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    37.630] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    37.630] (**) Option "xkb_rules" "evdev"
[    37.630] (**) Option "xkb_model" "pc105"
[    37.630] (**) Option "xkb_layout" "us"
[    37.631] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    37.631] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    37.631] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    37.631] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    37.631] (II) LoadModule: "synaptics"
[    37.631] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    37.631] (II) Module synaptics: vendor="X.Org Foundation"
[    37.631]     compiled for 1.17.1, module version = 1.8.2
[    37.631]     Module class: X.Org XInput Driver
[    37.631]     ABI class: X.Org XInput driver, version 21.0
[    37.631] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    37.631] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    37.631] (**) Option "Device" "/dev/input/event8"
[    37.664] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1408 (res 0)
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 704 (res 0)
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    37.664] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    37.664] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    37.664] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    37.676] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    37.676] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 14)
[    37.676] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    37.676] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    37.676] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.127
[    37.676] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    37.676] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    37.676] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    37.676] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    37.676] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    37.676] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    37.677] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    37.678] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    37.678] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    37.678] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    37.678] (**) Dell WMI hotkeys: always reports core events
[    37.678] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    37.678] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    37.678] (--) evdev: Dell WMI hotkeys: Found keys
[    37.678] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    37.678] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    37.678] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 15)
[    37.678] (**) Option "xkb_rules" "evdev"
[    37.678] (**) Option "xkb_model" "pc105"
[    37.678] (**) Option "xkb_layout" "us"
[    38.634] (II) intel(0): EDID vendor "AUO", prod id 5534
[    38.634] (II) intel(0): Printing DDC gathered Modelines:
[    38.634] (II) intel(0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    59.188] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    63.392] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    63.398] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    83.690] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[   118.792] (II) config/udev: Adding input device 15:08:29:18:17:DD (/dev/input/event14)
[   118.793] (**) 15:08:29:18:17:DD: Applying InputClass "evdev keyboard catchall"
[   118.793] (II) Using input driver 'evdev' for '15:08:29:18:17:DD'
[   118.793] (**) 15:08:29:18:17:DD: always reports core events
[   118.793] (**) evdev: 15:08:29:18:17:DD: Device: "/dev/input/event14"
[   118.793] (--) evdev: 15:08:29:18:17:DD: Vendor 0 Product 0
[   118.793] (--) evdev: 15:08:29:18:17:DD: Found keys
[   118.793] (II) evdev: 15:08:29:18:17:DD: Configuring as keyboard
[   118.793] (**) Option "config_info" "udev:/sys/devices/virtual/input/input15/event14"
[   118.793] (II) XINPUT: Adding extended input device "15:08:29:18:17:DD" (type: KEYBOARD, id 16)
[   118.793] (**) Option "xkb_rules" "evdev"
[   118.793] (**) Option "xkb_model" "pc105"
[   118.793] (**) Option "xkb_layout" "us"
[   118.793] (WW) Option "xkb_variant" requires a string value
[   118.793] (WW) Option "xkb_options" requires a string value
[   118.802] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   350.196] (II) AIGLX: Suspending AIGLX clients for VT switch
[   354.689] (II) AIGLX: Resuming AIGLX clients after VT switch
[   354.689] (II) intel(0): switch to mode 1600x900@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   354.765] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[   354.775] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.783] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.803] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.821] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   354.839] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   967.734] (II) config/udev: removing device  USB OPTICAL MOUSE
[   967.749] (II) evdev:  USB OPTICAL MOUSE: Close
[   967.749] (II) UnloadModule: "evdev"
[   969.129] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[   969.129] (II) No input driver specified, ignoring this device.
[   969.129] (II) This device may have been added with another device file.
[   969.211] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event7)
[   969.211] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[   969.211] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[   969.211] (**)  USB OPTICAL MOUSE: always reports core events
[   969.211] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event7"
[   969.264] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x425 Product 0x1
[   969.264] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[   969.264] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[   969.264] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[   969.264] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[   969.264] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[   969.264] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[   969.264] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[   969.264] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   969.264] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:0425:0001.0002/input/input16/event7"
[   969.264] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 11)
[   969.264] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[   969.265] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[   969.265] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[   969.265] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[   969.265] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
```

And for this "lspci -k | grep -EA2 'VGA|3D'"
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 0565
    Kernel driver in use: i915
--
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
    Subsystem: Dell GeForce GT 630M
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
```

I did try to install Nvidia driver several times, but I pruged it everytime before trying to install again.

---

### Post by Bashing-om on 2016-03-08
daniii10; Hey;

1 step in the right direction:
the card GeForce GT 630M takes the 304 version driver; per:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

What is of concern is that in the Xorg.0.log file, there is no hint of Nvidia .

Let's clean things up and take another look.
```

sudo find / -name "NVIDIA-Linux-*"

```
to make sure we are not having to cope with an OEM driver install .

IF OEM is not a factor we next make sure the system is clean .
```

sudo apt-get purge nvidia*

```

let’s remove all the packages marked as rc (-R-emoved but -C-onfig files remain).
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

On a clean environment let's install the driver:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers list
sudo ubuntu-drivers autoinstall

```

with that old of a driver, I am not certain that 'nvidia-prime' also autoinstalls along with the driver ( later version drivers I know it does) we need to check and see:
```

dpkg -l | grep -i nvidia

```
if 'nvidia-prime' is installed.

If now all looks good, reboot the system see what the effect is.

Able now to switch graphic's sets ?

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
I followed your instructions but I still have the same problem. When prime set to nvidia I get the low graphics mode screen after reboot (nvidia-prime was installed with the driver).

This command:
```
sudo find / -name "NVIDIA-Linux-*"
``` Doesn't return anything.

After I did all the commands Ubuntu-driver still installs 340 driver (that's what I installed before).

Maybe I should purge everything again and try to install 304 driver?

---

### Post by Bashing-om on 2016-03-08
daniii10; Humm ...

> 
After I did all the commands Ubuntu-driver still installs 340 driver (that's what I installed before).

Maybe I should purge everything again and try to install 304 driver?

I generally trust the system to know .

Let's take a look at the log file, see if there are hints there, and maybe look at a couple other logs.
The Xorg.0.log file is generated anew each boot ,
```

cat /var/log/Xorg.0.log
dpkg -l | grep -i nvidia

```
to see if Nvidia is now detected.

[INDENT][INDENT]got to be a reason why (not)
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
Ok this is the logs:

'cat /var/log/Xorg.0.log'
```
[    38.818] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    38.818] X Protocol Version 11, Revision 0
[    38.818] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    38.818] Current Operating System: Linux daniel-Inspiron-5720 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64
[    38.818] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic.efi.signed root=UUID=74974142-c5de-406c-83aa-89b1d871a6f6 ro quiet splash vt.handoff=7
[    38.818] Build Date: 12 November 2015  05:33:29PM
[    38.818] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[    38.818] Current version of pixman: 0.32.6
[    38.818]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.818] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.818] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  8 19:46:48 2016
[    38.934] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.957] (==) No Layout section.  Using the first Screen section.
[    38.957] (==) No screen section available. Using defaults.
[    38.957] (**) |-->Screen "Default Screen Section" (0)
[    38.957] (**) |   |-->Monitor "<default monitor>"
[    38.957] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    38.957] (==) Automatically adding devices
[    38.957] (==) Automatically enabling devices
[    38.957] (==) Automatically adding GPU devices
[    38.957] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.957]     Entry deleted from font path.
[    38.957] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.957]     Entry deleted from font path.
[    38.957] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.957]     Entry deleted from font path.
[    38.957] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.957]     Entry deleted from font path.
[    38.957] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.957]     Entry deleted from font path.
[    38.957] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.957] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.957] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    38.957] (II) Loader magic: 0x55d0e5147d40
[    38.957] (II) Module ABI versions:
[    38.957]     X.Org ANSI C Emulation: 0.4
[    38.957]     X.Org Video Driver: 19.0
[    38.957]     X.Org XInput driver : 21.0
[    38.957]     X.Org Server Extension : 9.0
[    38.958] (II) xfree86: Adding drm device (/dev/dri/card0)
[    38.959] (--) PCI:*(0:0:2:0) 8086:0166:1028:0565 rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    38.959] (--) PCI: (0:1:0:0) 10de:1140:1028:0565 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128
[    38.959] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    38.959] (II) "glx" will be loaded by default.
[    38.959] (II) LoadModule: "glx"
[    38.979] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.217] (II) Module glx: vendor="X.Org Foundation"
[    39.217]     compiled for 1.17.2, module version = 1.0.0
[    39.217]     ABI class: X.Org Server Extension, version 9.0
[    39.217] (==) AIGLX enabled
[    39.217] (==) Matched intel as autoconfigured driver 0
[    39.217] (==) Matched intel as autoconfigured driver 1
[    39.217] (==) Matched modesetting as autoconfigured driver 2
[    39.217] (==) Matched fbdev as autoconfigured driver 3
[    39.217] (==) Matched vesa as autoconfigured driver 4
[    39.217] (==) Assigned the driver to the xf86ConfigLayout
[    39.217] (II) LoadModule: "intel"
[    39.218] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    39.300] (II) Module intel: vendor="X.Org Foundation"
[    39.300]     compiled for 1.17.2, module version = 2.99.917
[    39.300]     Module class: X.Org Video Driver
[    39.300]     ABI class: X.Org Video Driver, version 19.0
[    39.300] (II) LoadModule: "modesetting"
[    39.300] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.319] (II) Module modesetting: vendor="X.Org Foundation"
[    39.319]     compiled for 1.17.2, module version = 1.17.2
[    39.320]     Module class: X.Org Video Driver
[    39.320]     ABI class: X.Org Video Driver, version 19.0
[    39.320] (II) LoadModule: "fbdev"
[    39.320] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    39.320] (II) Module fbdev: vendor="X.Org Foundation"
[    39.320]     compiled for 1.17.1, module version = 0.4.4
[    39.320]     Module class: X.Org Video Driver
[    39.320]     ABI class: X.Org Video Driver, version 19.0
[    39.320] (II) LoadModule: "vesa"
[    39.320] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    39.337] (II) Module vesa: vendor="X.Org Foundation"
[    39.337]     compiled for 1.17.1, module version = 2.3.4
[    39.337]     Module class: X.Org Video Driver
[    39.337]     ABI class: X.Org Video Driver, version 19.0
[    39.337] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    39.337] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    39.337] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    39.337] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    39.337] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    39.337] (II) FBDEV: driver for framebuffer: fbdev
[    39.337] (II) VESA: driver for VESA chipsets: vesa
[    39.337] (++) using VT number 7

[    39.338] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150731
[    39.338] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4 (Robert Ancell <robert.ancell@canonical.com>)
[    39.338] (II) intel(0): SNA compiled for use with valgrind
[    39.339] (WW) Falling back to old probe method for modesetting
[    39.340] (WW) Falling back to old probe method for fbdev
[    39.340] (II) Loading sub module "fbdevhw"
[    39.340] (II) LoadModule: "fbdevhw"
[    39.340] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    39.340] (II) Module fbdevhw: vendor="X.Org Foundation"
[    39.340]     compiled for 1.17.2, module version = 0.0.2
[    39.340]     ABI class: X.Org Video Driver, version 19.0
[    39.340] (WW) Falling back to old probe method for vesa
[    39.341] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    39.341] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx; using a maximum of 4 threads
[    39.341] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    39.341] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    39.341] (==) intel(0): RGB weight 888
[    39.341] (==) intel(0): Default visual is TrueColor
[    39.341] (II) intel(0): Output LVDS1 has no monitor section
[    39.352] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    39.352] (II) intel(0): Enabled output LVDS1
[    39.352] (II) intel(0): Output VGA1 has no monitor section
[    39.352] (II) intel(0): Enabled output VGA1
[    39.352] (II) intel(0): Output HDMI1 has no monitor section
[    39.352] (II) intel(0): Enabled output HDMI1
[    39.352] (II) intel(0): Output DP1 has no monitor section
[    39.352] (II) intel(0): Enabled output DP1
[    39.352] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    39.352] (II) intel(0): Output VIRTUAL1 has no monitor section
[    39.352] (II) intel(0): Enabled output VIRTUAL1
[    39.352] (--) intel(0): Output LVDS1 using initial mode 1600x900 on pipe 0
[    39.352] (==) intel(0): TearFree disabled
[    39.352] (==) intel(0): DPI set to (96, 96)
[    39.352] (II) Loading sub module "dri2"
[    39.352] (II) LoadModule: "dri2"
[    39.352] (II) Module "dri2" already built-in
[    39.352] (II) Loading sub module "present"
[    39.352] (II) LoadModule: "present"
[    39.352] (II) Module "present" already built-in
[    39.456] (II) UnloadModule: "modesetting"
[    39.456] (II) Unloading modesetting
[    39.456] (II) UnloadModule: "fbdev"
[    39.456] (II) Unloading fbdev
[    39.456] (II) UnloadSubModule: "fbdevhw"
[    39.456] (II) Unloading fbdevhw
[    39.456] (II) UnloadModule: "vesa"
[    39.456] (II) Unloading vesa
[    39.456] (==) Depth 24 pixmap format is 32 bpp
[    39.458] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    39.458] (==) intel(0): Backing store enabled
[    39.458] (==) intel(0): Silken mouse enabled
[    39.458] (II) intel(0): HW Cursor enabled
[    39.458] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    39.458] (==) intel(0): DPMS enabled
[    39.459] (==) intel(0): Display hotplug detection enabled
[    39.459] (II) intel(0): [DRI2] Setup complete
[    39.459] (II) intel(0): [DRI2]   DRI driver: i965
[    39.459] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    39.459] (II) intel(0): direct rendering: DRI2 enabled
[    39.459] (II) intel(0): hardware support for Present enabled
[    39.459] (--) RandR disabled
[    39.462] (II) SELinux: Disabled on system
[    39.813] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    39.813] (II) AIGLX: enabled GLX_ARB_create_context
[    39.813] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    39.813] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    39.813] (II) AIGLX: enabled GLX_INTEL_swap_event
[    39.813] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    39.813] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    39.813] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    39.813] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    39.813] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    39.813] (II) AIGLX: Loaded and initialized i965
[    39.813] (II) GLX: Initialized DRI2 GL provider for screen 0
[    39.816] (II) intel(0): switch to mode 1600x900@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    39.816] (II) intel(0): Setting screen physical size to 423 x 238
[    39.878] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.885] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    39.886] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.886] (II) LoadModule: "evdev"
[    39.886] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.917] (II) Module evdev: vendor="X.Org Foundation"
[    39.917]     compiled for 1.17.1, module version = 2.9.2
[    39.917]     Module class: X.Org XInput Driver
[    39.917]     ABI class: X.Org XInput driver, version 21.0
[    39.917] (II) Using input driver 'evdev' for 'Power Button'
[    39.917] (**) Power Button: always reports core events
[    39.917] (**) evdev: Power Button: Device: "/dev/input/event3"
[    39.917] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.917] (--) evdev: Power Button: Found keys
[    39.917] (II) evdev: Power Button: Configuring as keyboard
[    39.917] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    39.917] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    39.917] (**) Option "xkb_rules" "evdev"
[    39.917] (**) Option "xkb_model" "pc105"
[    39.917] (**) Option "xkb_layout" "us"
[    39.917] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    39.917] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    39.917] (II) Using input driver 'evdev' for 'Video Bus'
[    39.917] (**) Video Bus: always reports core events
[    39.917] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    39.918] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    39.918] (--) evdev: Video Bus: Found keys
[    39.918] (II) evdev: Video Bus: Configuring as keyboard
[    39.918] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    39.918] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    39.918] (**) Option "xkb_rules" "evdev"
[    39.918] (**) Option "xkb_model" "pc105"
[    39.918] (**) Option "xkb_layout" "us"
[    39.918] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    39.918] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    39.918] (II) Using input driver 'evdev' for 'Video Bus'
[    39.918] (**) Video Bus: always reports core events
[    39.918] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    39.918] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    39.918] (--) evdev: Video Bus: Found keys
[    39.918] (II) evdev: Video Bus: Configuring as keyboard
[    39.918] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30/LNXVIDEO:00/input/input7/event5"
[    39.918] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    39.918] (**) Option "xkb_rules" "evdev"
[    39.918] (**) Option "xkb_model" "pc105"
[    39.918] (**) Option "xkb_layout" "us"
[    39.918] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    39.918] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.918] (II) Using input driver 'evdev' for 'Power Button'
[    39.918] (**) Power Button: always reports core events
[    39.918] (**) evdev: Power Button: Device: "/dev/input/event0"
[    39.918] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.918] (--) evdev: Power Button: Found keys
[    39.918] (II) evdev: Power Button: Configuring as keyboard
[    39.919] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    39.919] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    39.919] (**) Option "xkb_rules" "evdev"
[    39.919] (**) Option "xkb_model" "pc105"
[    39.919] (**) Option "xkb_layout" "us"
[    39.919] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    39.919] (II) No input driver specified, ignoring this device.
[    39.919] (II) This device may have been added with another device file.
[    39.919] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    39.919] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    39.919] (II) Using input driver 'evdev' for 'Sleep Button'
[    39.919] (**) Sleep Button: always reports core events
[    39.919] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    39.919] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    39.919] (--) evdev: Sleep Button: Found keys
[    39.919] (II) evdev: Sleep Button: Configuring as keyboard
[    39.919] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    39.919] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    39.919] (**) Option "xkb_rules" "evdev"
[    39.919] (**) Option "xkb_model" "pc105"
[    39.919] (**) Option "xkb_layout" "us"
[    39.920] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event7)
[    39.920] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    39.920] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[    39.920] (**)  USB OPTICAL MOUSE: always reports core events
[    39.920] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event7"
[    39.976] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x425 Product 0x1
[    39.976] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[    39.976] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[    39.976] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[    39.976] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[    39.976] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[    39.976] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[    39.976] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    39.976] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    39.976] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:0425:0001.0001/input/input9/event7"
[    39.976] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 11)
[    39.976] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[    39.976] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    39.976] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[    39.976] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    39.976] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    39.977] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    39.977] (II) No input driver specified, ignoring this device.
[    39.977] (II) This device may have been added with another device file.
[    39.977] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event13)
[    39.977] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    39.977] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    39.977] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    39.977] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event13"
[    39.977] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xbda Product 0x58bf
[    39.977] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    39.977] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    39.977] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/input/input14/event13"
[    39.977] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    39.977] (**) Option "xkb_rules" "evdev"
[    39.977] (**) Option "xkb_model" "pc105"
[    39.977] (**) Option "xkb_layout" "us"
[    39.978] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    39.978] (II) No input driver specified, ignoring this device.
[    39.978] (II) This device may have been added with another device file.
[    39.978] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    39.978] (II) No input driver specified, ignoring this device.
[    39.978] (II) This device may have been added with another device file.
[    39.978] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    39.978] (II) No input driver specified, ignoring this device.
[    39.978] (II) This device may have been added with another device file.
[    39.978] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    39.978] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    39.978] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    39.978] (**) AT Translated Set 2 keyboard: always reports core events
[    39.978] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    39.978] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    39.978] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    39.978] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    39.978] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    39.978] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    39.978] (**) Option "xkb_rules" "evdev"
[    39.978] (**) Option "xkb_model" "pc105"
[    39.978] (**) Option "xkb_layout" "us"
[    39.979] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    39.979] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    39.979] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    39.979] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    39.979] (II) LoadModule: "synaptics"
[    39.979] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    39.979] (II) Module synaptics: vendor="X.Org Foundation"
[    39.979]     compiled for 1.17.1, module version = 1.8.2
[    39.979]     Module class: X.Org XInput Driver
[    39.979]     ABI class: X.Org XInput driver, version 21.0
[    39.979] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    39.979] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    39.979] (**) Option "Device" "/dev/input/event8"
[    39.996] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1408 (res 0)
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 704 (res 0)
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    39.996] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    39.996] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    39.996] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    40.008] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    40.008] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 14)
[    40.008] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    40.008] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    40.008] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.127
[    40.008] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    40.008] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    40.008] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    40.008] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    40.008] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    40.008] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    40.008] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    40.010] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    40.010] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    40.010] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    40.010] (**) Dell WMI hotkeys: always reports core events
[    40.010] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    40.010] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    40.010] (--) evdev: Dell WMI hotkeys: Found keys
[    40.010] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    40.010] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    40.010] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 15)
[    40.010] (**) Option "xkb_rules" "evdev"
[    40.010] (**) Option "xkb_model" "pc105"
[    40.010] (**) Option "xkb_layout" "us"
[    41.352] (II) intel(0): EDID vendor "AUO", prod id 5534
[    41.352] (II) intel(0): Printing DDC gathered Modelines:
[    41.352] (II) intel(0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    63.470] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    66.431] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    66.438] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    87.887] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
```

'dpkg -l | grep -i nvidia'
```
ii  bbswitch-dkms                                 0.8-2~wilyppa1                             all          Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-340                                  340.96-0ubuntu0.15.10.1                    amd64        NVIDIA CUDA runtime library
ii  libnvtt2:amd64                                2.0.8-1+dfsg-5build1                       amd64        NVIDIA Texture Tools
ii  nvidia-340                                    340.96-0ubuntu0.15.10.1                    amd64        NVIDIA binary driver - version 340.96
ii  nvidia-opencl-icd-340                         340.96-0ubuntu0.15.10.1                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                  0.8.1                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                               361.28-0ubuntu0~gpu15.10.1                 amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by Bashing-om on 2016-03-08
daniii10; Sssheeshhh;

Still no hint of Nvidia in the log file ... 
I have run into that stone wall of ignorance - on my part.
Not at all sure of what to do to get that driver recognized as the system is aware of the hardware.

Maybe, is nvidia "blacklisted " by some chance ?
what returns:
```

ls -al /etc/modprobe.d
lsmod | grep nvidia
sudo lshw -C display

```

look'n to find the where and why.

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
Terminal outputs:

ls -al /etc/modprobe.d
```
total 76
drwxr-xr-x   2 root root  4096 Mar  8 18:41 .
drwxr-xr-x 159 root root 12288 Mar  8 19:45 ..
-rw-r--r--   1 root root  2507 Jul 30  2015 alsa-base.conf
-rw-r--r--   1 root root   325 Aug 20  2015 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Aug 20  2015 blacklist.conf
-rw-r--r--   1 root root   210 Aug 20  2015 blacklist-firewire.conf
-rw-r--r--   1 root root   697 Aug 20  2015 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Nov  1 11:35 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Aug 20  2015 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Aug 20  2015 blacklist-watchdog.conf
-rw-r--r--   1 root root   127 Mar 11  2015 dkms.conf
-rw-r--r--   1 root root   390 Oct 15 07:34 fbdev-blacklist.conf
-rw-r--r--   1 root root   154 Jan 30  2015 intel-microcode-blacklist.conf
-rw-r--r--   1 root root   347 Aug 20  2015 iwlwifi.conf
-rw-r--r--   1 root root   104 Aug 20  2015 mlx4.conf
-rw-r--r--   1 root root   153 Nov 16 12:32 nvidia-340_hybrid.conf
lrwxrwxrwx   1 root root    49 Mar  8 18:41 nvidia-graphics-drivers.conf -> /etc/alternatives/x86_64-linux-gnu_nvidia_modconf
-rw-r--r--   1 root root    30 Jun  5  2015 vmwgfx-fbdev.conf
```

'lsmod | grep nvidia' doesn't return anything

sudo lshw -C display
```
*-display UNCLAIMED     
       description: 3D controller
       product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)
```

Thank you for your help.

---

### Post by Bashing-om on 2016-03-08
daniii10; Heym hey ...

Looks to be promising that Nvidia is blacklisted, as such NO nvidia modules will be available.

It is late my time, and my eyes are crossing and mind is mushy ..

we will pick this line of thought back up in my AM .

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-08
Ok thanks man it's late in my place also. We'll check it out tomorrow.

---

### Post by Bashing-om on 2016-03-09
daniii10; OK;

Back on this ...
Let's find out why and what all this blacklisting is all about.

Post back:
```

cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/dkms.conf
cat /etc/modprobe.d/nvidia-340_hybrid.conf
cat /etc/modprobe.d/nvidia-graphics-drivers.conf
cat /etc/modprobe.d/intel-microcode-blacklist.conf

```

A standard default AMD processor and ATI graphics install looks like this:
```

sysop@1404mini:~$ ls -al /etc/modprobe.d
total 56
drwxr-xr-x  2 root root  4096 Feb 10 11:13 .
drwxr-xr-x 98 root root 12288 Mar  9 14:02 ..
-rw-r--r--  1 root root   325 Apr 18  2013 blacklist-ath_pci.conf
-rw-r--r--  1 root root  1603 Apr 18  2013 blacklist.conf
-rw-r--r--  1 root root   210 Apr 18  2013 blacklist-firewire.conf
-rw-r--r--  1 root root   677 Apr 18  2013 blacklist-framebuffer.conf
-rw-r--r--  1 root root   583 Apr 18  2013 blacklist-rare-network.conf
-rw-r--r--  1 root root  1077 Apr 18  2013 blacklist-watchdog.conf
-rw-r--r--  1 root root   456 Jun 20  2014 fbdev-blacklist.conf
-rw-r--r--  1 root root   347 Apr 18  2013 iwlwifi.conf
-rw-r--r--  1 root root   104 Apr 18  2013 mlx4.conf
-rw-r--r--  1 root root    30 Aug  2  2012 vmwgfx-fbdev.conf
sysop@1404mini:~$

```

we work to enable the system to load the Nvidia modules .

Who knows where we go from here.

[INDENT][INDENT]there is that way that seems right
[INDENT][INDENT][INDENT][INDENT]that leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-09
OK this is the terminal outputs:

/etc/modprobe.d/blacklist.conf
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

/etc/modprobe.d/dkms.conf
```
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
```

/etc/modprobe.d/nvidia-340_hybrid.conf
```
# This file was installed by nvidia-340
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
```

/etc/modprobe.d/nvidia-graphics-drivers.conf
```
# This file was installed by nvidia-340
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-current
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
blacklist nvidia-340-updates
alias nvidia nvidia_340
alias nvidia-uvm nvidia_340-uvm
alias nouveau off
```

/etc/modprobe.d/intel-microcode-blacklist.conf
```
# The microcode module attempts to apply a microcode update when
# it autoloads.  This is not always safe, so we block it by default.
blacklist microcode
```

---

### Post by Bashing-om on 2016-03-09
daniii10; Welp;

I see nothing there I can point a finger at to cause the Nvidia driver (module) not to build or to be loaded. The driver is available, the hardware is seen, so why is it not loaded ? The system chooses to install the 340 version over the 304 version, and presently I have no heartburn over that circumstance ->
Presently stonewalled by my state of ignorance .

What results if we explicitly load nvidia ?
```

sudo modprobe nvidia

```

[INDENT]try'n to find out why
[INDENT][INDENT][INDENT]just do not know any better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-09
Terminal output for the command 'sudo modprobe nvidia':
```
modprobe: ERROR: could not insert 'nvidia_340': Invalid argument
```

Could it be by any chance that Intel graphics driver I installed from [here ]("https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0")causes the problem? Because that is when Nvidia stops working...

---

### Post by Bashing-om on 2016-03-09
daniii10; Ouch !

That failure of 'modprobe' does mean we have to dig deeper. Maybe way out of my level of experience.
Nvidia and ATI graphics I am familiar with; Intel not at all . An opportunity here to add to my smart bucket.

We do have this warning from Intel:
> 
KNOWN ISSUES

WARNING: Attempting to "force" package upgrades may break your OS installation, requiring a re-install or other time-intensive remedies (requiring a high level of expertise). Do not forcibly upgrade packages!


I do not know how the "testing" release of the Intel driver would react in a hybrid graphics situation, if it is even compatible .
Nor am I certain how to revert back from the OEM install of the driver .. I have some vague ideas that 'might' be correct.

Sit here for a spell and await others to chime in here with their thoughts ?

[INDENT][INDENT]when I do not know, wait
[INDENT][INDENT][INDENT]for the truth to sink in
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-09
OK thank you for your help.
Do you think it would be dangerous to try to remove Intel Graphics Driver following this guide? [http://askubuntu.com/questions/531540/how-to-safely-remove-proprietary-intel-driver](http://askubuntu.com/questions/531540/how-to-safely-remove-proprietary-intel-driver)

---

### Post by Bashing-om on 2016-03-09
daniii10; Nope, 

That procedure looks dirty to me, and not at all in line with what my thoughts are.

Let's sit on this a few hours and see what the more knowledgeable advise.

else, well we can blunder forward with my best intentions.

[INDENT][INDENT]blundering can be a good thing
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-09
Alright thanks for your help.

---

### Post by Bashing-om on 2016-03-09
daniii10 :)

I do have a procedure in mind , but I have no experience in the Intel realm and thus do not KNOW how effective it would be.
I would welcome others opinions here ,, if we even should be reverting the Intel graphic's driver ( makes good sense to me ) .

I rest assured good help will arrive .

[INDENT][INDENT]we are all on this together
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-09
OK thanks I'll wait for an answer.

---

### Post by Bashing-om on 2016-03-10
daniii10; Hey !

While we are waiting, let's consider what it will entail to revert the Intel driver to that of our repository.

Show the result:
```

apt-cache policy xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg

```

A lot of packages to consider, we find out which apply ; and I will find out what should be.

[INDENT][INDENT]and the hunt is on
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-10
OK terminal output:
```
i386 xserver-xorg
xserver-xorg-core:
  Installed: 2:1.17.2-1ubuntu9.1
  Candidate: 2:1.17.2-1ubuntu9.1
  Version table:
 *** 2:1.17.2-1ubuntu9.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.17.2-1ubuntu9 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
xserver-xorg-video-intel:
  Installed: 2:2.99.917+git20150808-0ubuntu4
  Candidate: 2:2.99.917+git20150808-0ubuntu4
  Version table:
 *** 2:2.99.917+git20150808-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
libgl1-mesa-glx:
  Installed: 11.0.4-1intel1
  Candidate: 11.0.4-1intel1
  Version table:
 *** 11.0.4-1intel1 0
        100 /var/lib/dpkg/status
     11.0.2-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
libgl1-mesa-dri:
  Installed: 11.0.4-1intel1
  Candidate: 11.0.4-1intel1
  Version table:
 *** 11.0.4-1intel1 0
        100 /var/lib/dpkg/status
     11.0.2-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
libgl1-mesa-glx:i386:
  Installed: 11.0.4-1intel1
  Candidate: 11.0.4-1intel1
  Version table:
 *** 11.0.4-1intel1 0
        100 /var/lib/dpkg/status
     11.0.2-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main i386 Packages
libgl1-mesa-dri:i386:
  Installed: 11.0.4-1intel1
  Candidate: 11.0.4-1intel1
  Version table:
 *** 11.0.4-1intel1 0
        100 /var/lib/dpkg/status
     11.0.2-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main i386 Packages
xserver-xorg:
  Installed: 1:7.7+7ubuntu4
  Candidate: 1:7.7+7ubuntu4
  Version table:
 *** 1:7.7+7ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Bashing-om on 2016-03-10
daniii10; Hello;


work'n on it .. bear with me while I verify what we have and consider what to do .


[INDENT][INDENT]I'll Be Baaackkk
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-10
Thank you I'll wait for a solution.

---

### Post by Bashing-om on 2016-03-10
daniii10; Welp;

I am still looking .
I do have a stumbling block.
Question:
> 
libgl1-mesa-glx:i386
libgl1-mesa-dri:i386:

as these are installed from Intel, is 'steam' a part in this ?

[INDENT][INDENT]unraveling a puzzle
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-10
I don't know. Do you suggest that these packages were installed by Intel graphics installer?

---

### Post by Bashing-om on 2016-03-10
daniii10; Hey ...

My looking about :
```

xserver-xorg-core:
  Installed: 2:1.17.2-1ubuntu9.1
  pack:      2:1.17.2-1ubuntu9.1:
xserver-xorg-video-intel:
  Installed: 2:2.99.917+git20150808-0ubuntu4
  pack:      2:1.17.2-1ubuntu9.1
libgl1-mesa-glx:
  Installed: 11.0.4-1intel1
  pack:      Sorry, your search gave no results
  search:    11.0.2-1ubuntu4
libgl1-mesa-dri:
  Installed: 11.0.4-1intel1
  pack:      Sorry, your search gave no results
  search:    11.0.2-1ubuntu4
  depends:   libdrm-intel1 (>= 2.4.48)
libgl1-mesa-glx:i386:
  Installed: 11.0.4-1intel1
  pack:      11.0.2-1ubuntu4: amd64 i386
  search:    Sorry, your search gave no results
  around:    (this works as a work around sudo apt-get install libc6:i386
              libgl1-mesa-dri-lts-<utopic>:i386 libgl1-mesa-glx-lts-
              <utopic>:i386)
  careful !   libgl1-mesa-dri-lts-utopic:i386 : Conflicts: libgl1-mesa-dri
  Launchpad:  libgl1-mesa-glx 10.5.8-1ubuntu1 (i386 binary) in ubuntu wily
               libgl1-mesa-dri:i386: -> This package does not include the
               modules themselves: these can be found in the libgl1-mesa-
               dri package.
libgl1-mesa-dri:i386:
  Installed: 11.0.4-1intel1
   pack:     11.0.2-1ubuntu4: amd64 i386

xserver-xorg:
  Installed: 1:7.7+7ubuntu4
  pack:      2:1.17.2-1ubuntu9.1:

```
and I said Ouch ! But, we can do this.

Then it dawned on me that this is ubuntu, and the driver was installed from a PPA .. and as such, hey ubuntu's package manager can get a handle on this. Let's let the package manager do all this heavy lifting for us !
IRT [https://download.01.org/gfx/](https://download.01.org/gfx/)

We can do:
```

sudo apt-get install ppa-purge
sudo ppa-purge -s download.01.org ppa:gfx/ubuntu

```
and if all runs right, the Intel driver and all it's packages will be reverted to what is in out repo .

Now this ppa-purge is worth the shot !

[INDENT][INDENT]package management
[INDENT][INDENT][INDENT]what a wonderful thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-10
This is the terminal outputs in case you need.

sudo apt-get install ppa-purge:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude aptitude-common libcwidget3v5
Suggested packages:
  aptitude-doc-en aptitude-doc debtags tasksel libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget3v5 ppa-purge
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,395 kB of archives.
After this operation, 10.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ wily-updates/main aptitude-common all 0.7.3-1ubuntu1.1 [747 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ wily/main libcwidget3v5 amd64 0.5.17-3.1ubuntu2 [293 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ wily-updates/main aptitude amd64 0.7.3-1ubuntu1.1 [1,348 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ wily/universe ppa-purge all 0.2.8+bzr57 [5,704 B]
Fetched 2,395 kB in 7s (334 kB/s)                                              
Selecting previously unselected package aptitude-common.
(Reading database ... 483647 files and directories currently installed.)
Preparing to unpack .../aptitude-common_0.7.3-1ubuntu1.1_all.deb ...
Unpacking aptitude-common (0.7.3-1ubuntu1.1) ...
Selecting previously unselected package libcwidget3v5:amd64.
Preparing to unpack .../libcwidget3v5_0.5.17-3.1ubuntu2_amd64.deb ...
Unpacking libcwidget3v5:amd64 (0.5.17-3.1ubuntu2) ...
Selecting previously unselected package aptitude.
Preparing to unpack .../aptitude_0.7.3-1ubuntu1.1_amd64.deb ...
Unpacking aptitude (0.7.3-1ubuntu1.1) ...
Selecting previously unselected package ppa-purge.
Preparing to unpack .../ppa-purge_0.2.8+bzr57_all.deb ...
Unpacking ppa-purge (0.2.8+bzr57) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up aptitude-common (0.7.3-1ubuntu1.1) ...
Setting up libcwidget3v5:amd64 (0.5.17-3.1ubuntu2) ...
Setting up aptitude (0.7.3-1ubuntu1.1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/cs/man8/aptitude.8.gz because associated file /usr/share/man/cs/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/de/man8/aptitude.8.gz because associated file /usr/share/man/de/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/es/man8/aptitude.8.gz because associated file /usr/share/man/es/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fi/man8/aptitude.8.gz because associated file /usr/share/man/fi/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fr/man8/aptitude.8.gz because associated file /usr/share/man/fr/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/gl/man8/aptitude.8.gz because associated file /usr/share/man/gl/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/it/man8/aptitude.8.gz because associated file /usr/share/man/it/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ja/man8/aptitude.8.gz because associated file /usr/share/man/ja/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/pl/man8/aptitude.8.gz because associated file /usr/share/man/pl/man8/aptitude-curses.8.gz (of link group aptitude) doesn't exist
Setting up ppa-purge (0.2.8+bzr57) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
```

sudo ppa-purge -s download.01.org ppa:gfx/ubuntu
```
Updating packages lists
PPA to be removed: gfx ubuntu
Warning:  Could not find package list for PPA: gfx ubuntu
```

Now, what should I do next? Should I purge Nvidia driver and reinstall?

---

### Post by Bashing-om on 2016-03-10
daniii10; Naw ...

> 
Now, what should I do next? Should I purge Nvidia driver and reinstall?


More likely my syntax is in error .. lemme go do some more look'n  and confirm the origin for the correct syntax.
If we do this manually, will be a real chore .. so many version mismatches and dependencies to resolve !

[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-10
What if I'll install the default driver, will it automatically reconfigure the repository driver to default? Or there is anyway to restore drivers to default?

---

### Post by Bashing-om on 2016-03-11
daniii10; Hey ....

Sorry for all the delays, I have hard drive issues - and am disconcerted to no end that I have lost my back-up files. Sorta gets in the way of focusing on your situation,

OK, I have been hard at work on your issue.

And, per Intel:
> 
What if I'll install the default driver, will it automatically reconfigure the repository driver to default? Or there is anyway to restore drivers to default?

NO, there is no easy way - without prior prudent planning - to revert. I see no error with the syntax for 'ppa-purge', so all I can surmise is the driver package does not support ( Intel hints so ) a reversion .

However, there is :
[http://theclonker.de/archive/89](http://theclonker.de/archive/89)
This procedure looks promising and stays within the package management system. I do trust the package management system much more than my own judgement, till we see a problem with what the package manager wants to do. When you look at my research results you will note that there are several version conflicts to be overcome. That is not even counting the dependency issues that I am presently unaware of.

In the Ckonker procedure, pay close attention to what you are doing , that you tell the system the environment is 'wily' .

Try it and see what happens.

[INDENT][INDENT]right, wrong, or otherwise
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
OK I got to the step when I need to remove intel graphics driver so far everything seems to work fine, but I think because I have a different version the command doesn't work:

sudo apt-get purge i915-3.6-3.5-dkms intel-linux-graphics-installer
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package i915-3.6-3.5-dkms
E: Couldn't find any package by regex 'i915-3.6-3.5-dkms'
```

How can I find the exact version number on my system in order to purge it correctly?

And this is a screen-shot from synaptic
[[IMG]http://s22.postimg.org/3p7qfz10t/Intel_driver.jpg[/IMG]]("http://postimg.org/image/3p7qfz10t/")

I think my version is i965.

---

### Post by Bashing-om on 2016-03-11
daniii10; Yeah ...

minding our Ps and Qs ...

Let do this:
```

sudo find / -name "i915-*"

```
To identify the correct file(s) and version.

As I like what the terminal tells me over how a GUI application relates.

[INDENT][INDENT]just the facts mam
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
When I execute the command:
```
sudo find / -name "i915-*"
```
Terminal doesn't return anything.
It suppose to tell me my driver version?

---

### Post by Bashing-om on 2016-03-11
daniii10; Well;

> 
  36.618] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150731


As advised, I have no experience with Intel .. but I had expected a return from the 'find' command similar to the what your xorg file related. Where that version may or may not still be valid . Old old file of yours.

Maybe try as:
```

sudo find / -name "*i915-*"

```
where we search for any file that contains the term " i915-" ?

[INDENT][INDENT]computers are so literal; and
[INDENT][INDENT][INDENT]can not read our minds, yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
Here is the terminal output for 'sudo find / -name "*i915-*"
```
/var/lib/dpkg/info/i915-4.3.3-4.2.0-dkms.list
/var/lib/dpkg/info/i915-4.3.3-4.2.0-dkms.postinst
/var/lib/dpkg/info/i915-4.3.3-4.2.0-dkms.prerm
/var/lib/dpkg/info/i915-4.3.3-4.2.0-dkms.md5sums
/var/lib/dkms/i915-4.3.3-4.2.0
/usr/src/i915-4.3.3-4.2.0-2
/usr/share/doc/i915-4.3.3-4.2.0-dkms
```

So now how can I purge the driver?

---

### Post by Bashing-om on 2016-03-11
daniii10; Uh Huh;


Looks to me like:
```

sudo apt-get purge i915-4.3.3-4.2.0-dkms intel-linux-graphics-installer

```
is what we want, and should workie fine.

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
That's what I thought just wanted to make sure.
So now after removing Intel driver should I try to 'prime-select' nvidia? to check if it works? or I need to purge Nvidia driver and reinstall first?

Update:
I think it's working!! I set prime to Nvidia and now it's working! How can I check if Nvidia is really work?

---

### Post by Bashing-om on 2016-03-11
daniii10; Hey !

Sweat condition 10 terminated ?

What now returns:
```

sudo lshw -C display
lsmod | grep nvidia

```
does the log file " /var/log/Xorg.0.log" now reflect that the Nvidia driver builds ?

If all things look hunky dory .. are we ready to update the system and see about some clean up ?

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]good things can happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
Terminal outputs:

 sudo lshw -C display
```
*-display               
       description: 3D controller
       product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:32 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)
```

lsmod | grep nvidia
```
nvidia              10567680  35
drm                   356352  9 i915,drm_kms_helper,nvidia
```

And this is the "/var/log/Xorg.0.log" file.
```
[    38.432] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    38.432] X Protocol Version 11, Revision 0
[    38.432] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    38.432] Current Operating System: Linux daniel-Inspiron-5720 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64
[    38.432] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic.efi.signed root=UUID=74974142-c5de-406c-83aa-89b1d871a6f6 ro quiet splash vt.handoff=7
[    38.432] Build Date: 12 November 2015  05:33:29PM
[    38.432] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[    38.432] Current version of pixman: 0.32.6
[    38.432]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.432] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.432] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 11 16:28:23 2016
[    38.453] (==) Using config file: "/etc/X11/xorg.conf"
[    38.453] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.460] (==) ServerLayout "layout"
[    38.460] (**) |-->Screen "nvidia" (0)
[    38.460] (**) |   |-->Monitor "<default monitor>"
[    38.460] (**) |   |-->Device "nvidia"
[    38.460] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    38.460] (**) |-->Inactive Device "intel"
[    38.460] (==) Automatically adding devices
[    38.460] (==) Automatically enabling devices
[    38.460] (==) Automatically adding GPU devices
[    38.460] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.460]     Entry deleted from font path.
[    38.460] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.460]     Entry deleted from font path.
[    38.460] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.460]     Entry deleted from font path.
[    38.460] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.460]     Entry deleted from font path.
[    38.460] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.460]     Entry deleted from font path.
[    38.460] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.460] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.460] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    38.460] (II) Loader magic: 0x562bef5f1d40
[    38.460] (II) Module ABI versions:
[    38.460]     X.Org ANSI C Emulation: 0.4
[    38.460]     X.Org Video Driver: 19.0
[    38.460]     X.Org XInput driver : 21.0
[    38.460]     X.Org Server Extension : 9.0
[    38.461] (II) xfree86: Adding drm device (/dev/dri/card1)
[    38.461] (II) xfree86: Adding drm device (/dev/dri/card0)
[    38.462] (--) PCI:*(0:0:2:0) 8086:0166:1028:0565 rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    38.462] (--) PCI: (0:1:0:0) 10de:1140:1028:0565 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128
[    38.462] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    38.462] (II) "glx" will be loaded by default.
[    38.462] (II) LoadModule: "glx"
[    38.469] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    38.831] (II) Module glx: vendor="NVIDIA Corporation"
[    38.831]     compiled for 4.0.2, module version = 1.0.0
[    38.831]     Module class: X.Org Server Extension
[    38.838] (II) NVIDIA GLX Module  340.96  Sun Nov  8 22:06:18 PST 2015
[    38.838] (II) LoadModule: "nvidia"
[    38.838] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    38.931] (II) Module nvidia: vendor="NVIDIA Corporation"
[    38.932]     compiled for 4.0.2, module version = 1.0.0
[    38.932]     Module class: X.Org Video Driver
[    38.944] (II) LoadModule: "modesetting"
[    38.972] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    38.989] (II) Module modesetting: vendor="X.Org Foundation"
[    38.989]     compiled for 1.17.2, module version = 1.17.2
[    38.989]     Module class: X.Org Video Driver
[    38.989]     ABI class: X.Org Video Driver, version 19.0
[    38.989] (II) NVIDIA dlloader X Driver  340.96  Sun Nov  8 21:46:28 PST 2015
[    38.989] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    39.000] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    39.000] (++) using VT number 7

[    39.006] (II) Loading sub module "fb"
[    39.006] (II) LoadModule: "fb"
[    39.006] (II) Loading /usr/lib/xorg/modules/libfb.so
[    39.007] (II) Module fb: vendor="X.Org Foundation"
[    39.007]     compiled for 1.17.2, module version = 1.0.0
[    39.007]     ABI class: X.Org ANSI C Emulation, version 0.4
[    39.007] (WW) Unresolved symbol: fbGetGCPrivateKey
[    39.007] (II) Loading sub module "wfb"
[    39.007] (II) LoadModule: "wfb"
[    39.007] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    39.022] (II) Module wfb: vendor="X.Org Foundation"
[    39.022]     compiled for 1.17.2, module version = 1.0.0
[    39.022]     ABI class: X.Org ANSI C Emulation, version 0.4
[    39.022] (II) Loading sub module "ramdac"
[    39.022] (II) LoadModule: "ramdac"
[    39.022] (II) Module "ramdac" already built-in
[    39.072] (II) modeset(G0): using drv /dev/dri/card0
[    39.072] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    39.072] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    39.072] (==) NVIDIA(0): RGB weight 888
[    39.072] (==) NVIDIA(0): Default visual is TrueColor
[    39.072] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.072] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    39.072] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    39.072] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    39.085] (**) NVIDIA(0): Enabling 2D acceleration
[    39.321] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    39.322] (II) NVIDIA(0): NVIDIA GPU GeForce GT 630M (GF117) at PCI:1:0:0 (GPU-0)
[    39.322] (--) NVIDIA(0): Memory: 1048576 kBytes
[    39.322] (--) NVIDIA(0): VideoBIOS: 75.17.33.00.01
[    39.322] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    39.322] (--) NVIDIA(0): Valid display device(s) on GeForce GT 630M at PCI:1:0:0
[    39.322] (--) NVIDIA(0):     none
[    39.322] (II) NVIDIA(0): Validated MetaModes:
[    39.322] (II) NVIDIA(0):     "NULL"
[    39.322] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    39.322] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    39.322] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    39.323] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    39.323] (**) modeset(G0): Option "AccelMethod" "None"
[    39.323] (==) modeset(G0): RGB weight 888
[    39.323] (==) modeset(G0): Default visual is TrueColor
[    39.323] (**) modeset(G0): glamor disabled
[    39.323] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    39.323] (II) modeset(G0): Output LVDS-1-0 has no monitor section
[    39.323] (II) modeset(G0): Output VGA-1-0 has no monitor section
[    39.324] (II) modeset(G0): Output HDMI-1-0 has no monitor section
[    39.324] (II) modeset(G0): Output DisplayPort-1-0 has no monitor section
[    39.324] (II) modeset(G0): EDID for output LVDS-1-0
[    39.324] (II) modeset(G0): Manufacturer: AUO  Model: 159e  Serial#: 0
[    39.324] (II) modeset(G0): Year: 2011  Week: 0
[    39.324] (II) modeset(G0): EDID Version: 1.4
[    39.324] (II) modeset(G0): Digital Display Input
[    39.324] (II) modeset(G0): 6 bits per channel
[    39.324] (II) modeset(G0): Digital interface is undefined
[    39.324] (II) modeset(G0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    39.324] (II) modeset(G0): Gamma: 2.20
[    39.324] (II) modeset(G0): No DPMS capabilities specified
[    39.324] (II) modeset(G0): Supported color encodings: RGB 4:4:4 
[    39.324] (II) modeset(G0): First detailed timing is preferred mode
[    39.324] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[    39.324] (II) modeset(G0): redX: 0.620 redY: 0.340   greenX: 0.325 greenY: 0.570
[    39.324] (II) modeset(G0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    39.324] (II) modeset(G0): Manufacturer's mask: 0
[    39.324] (II) modeset(G0): Supported detailed timing:
[    39.324] (II) modeset(G0): clock: 100.0 MHz   Image Size:  382 x 214 mm
[    39.324] (II) modeset(G0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1798 h_border: 0
[    39.324] (II) modeset(G0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    39.324] (II) modeset(G0): Supported detailed timing:
[    39.324] (II) modeset(G0): clock: 100.0 MHz   Image Size:  382 x 214 mm
[    39.324] (II) modeset(G0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1798 h_border: 0
[    39.324] (II) modeset(G0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    39.324] (II) modeset(G0):  DYMX0\80B173RW1
[    39.324] (II) modeset(G0): Unknown vendor-specific block 0
[    39.324] (II) modeset(G0): EDID (in hex):
[    39.324] (II) modeset(G0):     00ffffffffffff0006af9e1500000000
[    39.324] (II) modeset(G0):     001501049026157802c4959e57539226
[    39.324] (II) modeset(G0):     0f505400000001010101010101010101
[    39.324] (II) modeset(G0):     010101010101102740c660841a303020
[    39.324] (II) modeset(G0):     36007ed61000001a102740c660841a30
[    39.324] (II) modeset(G0):     302036007ed61000001a000000fe0044
[    39.324] (II) modeset(G0):     594d5830804231373352573100000000
[    39.324] (II) modeset(G0):     00004101960101000002010a20200077
[    39.324] (II) modeset(G0): Printing probed modes for output LVDS-1-0
[    39.324] (II) modeset(G0): Modeline "1600x900"x60.1  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    39.324] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    39.324] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    39.324] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    39.324] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    39.324] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    39.324] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    39.324] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    39.324] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    39.324] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    39.324] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    39.324] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    39.324] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    39.324] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    39.324] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    39.324] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    39.324] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    39.324] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    39.324] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    39.324] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    39.325] (II) modeset(G0): EDID for output VGA-1-0
[    39.326] (II) modeset(G0): EDID for output HDMI-1-0
[    39.326] (II) modeset(G0): EDID for output DisplayPort-1-0
[    39.326] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    39.326] (==) modeset(G0): DPI set to (96, 96)
[    39.326] (II) Loading sub module "fb"
[    39.326] (II) LoadModule: "fb"
[    39.326] (II) Loading /usr/lib/xorg/modules/libfb.so
[    39.326] (II) Module fb: vendor="X.Org Foundation"
[    39.326]     compiled for 1.17.2, module version = 1.0.0
[    39.326]     ABI class: X.Org ANSI C Emulation, version 0.4
[    39.326] (II) Loading sub module "shadow"
[    39.326] (II) LoadModule: "shadow"
[    39.326] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    39.326] (II) Module shadow: vendor="X.Org Foundation"
[    39.326]     compiled for 1.17.2, module version = 1.1.0
[    39.326]     ABI class: X.Org ANSI C Emulation, version 0.4
[    39.326] (--) Depth 24 pixmap format is 32 bpp
[    39.326] (==) modeset(G0): Backing store enabled
[    39.326] (==) modeset(G0): Silken mouse enabled
[    39.326] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    39.326] (==) modeset(G0): DPMS enabled
[    39.326] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    39.326] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    39.683] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    39.683] (II) NVIDIA:     access.
[    39.788] (II) NVIDIA(0): Setting mode "NULL"
[    39.788] (EE) NVIDIA(0): Failed to initiate mode change.
[    39.788] (EE) NVIDIA(0): Failed to complete mode change
[    39.864] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    39.874] (==) NVIDIA(0): Disabling shared memory pixmaps
[    39.874] (==) NVIDIA(0): Backing store enabled
[    39.874] (==) NVIDIA(0): Silken mouse enabled
[    39.874] (==) NVIDIA(0): DPMS enabled
[    39.874] (II) Loading sub module "dri2"
[    39.874] (II) LoadModule: "dri2"
[    39.874] (II) Module "dri2" already built-in
[    39.874] (II) NVIDIA(0): [DRI2] Setup complete
[    39.874] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    39.874] (--) RandR disabled
[    39.877] (II) SELinux: Disabled on system
[    39.878] (II) Initializing extension GLX
[    39.878] (II) Indirect GLX disabled.(II) modeset(G0): Damage tracking initialized
[    41.056] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.064] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    41.064] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.064] (II) LoadModule: "evdev"
[    41.064] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.498] (II) Module evdev: vendor="X.Org Foundation"
[    41.498]     compiled for 1.17.1, module version = 2.9.2
[    41.498]     Module class: X.Org XInput Driver
[    41.498]     ABI class: X.Org XInput driver, version 21.0
[    41.498] (II) Using input driver 'evdev' for 'Power Button'
[    41.498] (**) Power Button: always reports core events
[    41.498] (**) evdev: Power Button: Device: "/dev/input/event3"
[    41.498] (--) evdev: Power Button: Vendor 0 Product 0x1
[    41.498] (--) evdev: Power Button: Found keys
[    41.498] (II) evdev: Power Button: Configuring as keyboard
[    41.498] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    41.498] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    41.498] (**) Option "xkb_rules" "evdev"
[    41.498] (**) Option "xkb_model" "pc105"
[    41.498] (**) Option "xkb_layout" "us"
[    41.498] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    41.498] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    41.499] (II) Using input driver 'evdev' for 'Video Bus'
[    41.499] (**) Video Bus: always reports core events
[    41.499] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    41.499] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    41.499] (--) evdev: Video Bus: Found keys
[    41.499] (II) evdev: Video Bus: Configuring as keyboard
[    41.499] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    41.499] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    41.499] (**) Option "xkb_rules" "evdev"
[    41.499] (**) Option "xkb_model" "pc105"
[    41.499] (**) Option "xkb_layout" "us"
[    41.499] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    41.499] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    41.499] (II) Using input driver 'evdev' for 'Video Bus'
[    41.499] (**) Video Bus: always reports core events
[    41.499] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    41.499] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    41.499] (--) evdev: Video Bus: Found keys
[    41.499] (II) evdev: Video Bus: Configuring as keyboard
[    41.499] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30/LNXVIDEO:00/input/input7/event5"
[    41.499] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    41.499] (**) Option "xkb_rules" "evdev"
[    41.499] (**) Option "xkb_model" "pc105"
[    41.499] (**) Option "xkb_layout" "us"
[    41.500] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    41.500] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.500] (II) Using input driver 'evdev' for 'Power Button'
[    41.500] (**) Power Button: always reports core events
[    41.500] (**) evdev: Power Button: Device: "/dev/input/event0"
[    41.500] (--) evdev: Power Button: Vendor 0 Product 0x1
[    41.500] (--) evdev: Power Button: Found keys
[    41.500] (II) evdev: Power Button: Configuring as keyboard
[    41.500] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    41.500] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    41.500] (**) Option "xkb_rules" "evdev"
[    41.500] (**) Option "xkb_model" "pc105"
[    41.500] (**) Option "xkb_layout" "us"
[    41.500] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    41.500] (II) No input driver specified, ignoring this device.
[    41.500] (II) This device may have been added with another device file.
[    41.500] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    41.500] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    41.500] (II) Using input driver 'evdev' for 'Sleep Button'
[    41.500] (**) Sleep Button: always reports core events
[    41.500] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    41.500] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    41.500] (--) evdev: Sleep Button: Found keys
[    41.500] (II) evdev: Sleep Button: Configuring as keyboard
[    41.500] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    41.500] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    41.500] (**) Option "xkb_rules" "evdev"
[    41.500] (**) Option "xkb_model" "pc105"
[    41.500] (**) Option "xkb_layout" "us"
[    41.501] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event7)
[    41.501] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    41.501] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[    41.501] (**)  USB OPTICAL MOUSE: always reports core events
[    41.501] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event7"
[    41.556] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x425 Product 0x1
[    41.556] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[    41.556] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[    41.556] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[    41.556] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[    41.556] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[    41.556] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[    41.556] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    41.556] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.556] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:0425:0001.0001/input/input9/event7"
[    41.556] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 11)
[    41.556] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[    41.556] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    41.556] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[    41.556] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    41.556] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    41.556] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    41.556] (II) No input driver specified, ignoring this device.
[    41.556] (II) This device may have been added with another device file.
[    41.557] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event13)
[    41.557] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    41.557] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    41.557] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    41.557] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event13"
[    41.557] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xbda Product 0x58bf
[    41.557] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    41.557] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    41.557] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/input/input14/event13"
[    41.557] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    41.557] (**) Option "xkb_rules" "evdev"
[    41.557] (**) Option "xkb_model" "pc105"
[    41.557] (**) Option "xkb_layout" "us"
[    41.557] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    41.557] (II) No input driver specified, ignoring this device.
[    41.557] (II) This device may have been added with another device file.
[    41.557] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    41.557] (II) No input driver specified, ignoring this device.
[    41.557] (II) This device may have been added with another device file.
[    41.558] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    41.558] (II) No input driver specified, ignoring this device.
[    41.558] (II) This device may have been added with another device file.
[    41.558] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    41.558] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    41.558] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    41.558] (**) AT Translated Set 2 keyboard: always reports core events
[    41.558] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    41.558] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    41.558] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    41.558] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    41.558] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    41.558] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    41.558] (**) Option "xkb_rules" "evdev"
[    41.558] (**) Option "xkb_model" "pc105"
[    41.558] (**) Option "xkb_layout" "us"
[    41.558] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    41.558] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    41.558] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    41.558] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    41.558] (II) LoadModule: "synaptics"
[    41.559] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    41.559] (II) Module synaptics: vendor="X.Org Foundation"
[    41.559]     compiled for 1.17.1, module version = 1.8.2
[    41.559]     Module class: X.Org XInput Driver
[    41.559]     ABI class: X.Org XInput driver, version 21.0
[    41.559] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    41.559] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    41.559] (**) Option "Device" "/dev/input/event8"
[    41.616] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1408 (res 0)
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 704 (res 0)
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    41.616] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    41.616] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    41.616] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    41.632] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    41.632] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 14)
[    41.632] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    41.632] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    41.632] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.127
[    41.632] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    41.632] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    41.632] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    41.632] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    41.632] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    41.632] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    41.632] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    41.634] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    41.634] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    41.634] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    41.634] (**) Dell WMI hotkeys: always reports core events
[    41.634] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    41.634] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    41.634] (--) evdev: Dell WMI hotkeys: Found keys
[    41.634] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    41.634] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    41.634] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 15)
[    41.634] (**) Option "xkb_rules" "evdev"
[    41.634] (**) Option "xkb_model" "pc105"
[    41.634] (**) Option "xkb_layout" "us"
[    42.258] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    42.258] (II) modeset(G0): Printing DDC gathered Modelines:
[    42.258] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    42.281] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    42.281] (II) modeset(G0): Printing DDC gathered Modelines:
[    42.281] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    42.284] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    42.284] (II) modeset(G0): Printing DDC gathered Modelines:
[    42.284] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    42.327] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    42.327] (II) modeset(G0): Printing DDC gathered Modelines:
[    42.327] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    55.565] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    55.565] (II) modeset(G0): Printing DDC gathered Modelines:
[    55.565] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    56.456] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    56.456] (II) modeset(G0): Printing DDC gathered Modelines:
[    56.456] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    62.616] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    62.616] (II) modeset(G0): Printing DDC gathered Modelines:
[    62.616] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    69.420] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    70.738] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    70.739] (II) modeset(G0): Printing DDC gathered Modelines:
[    70.739] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    72.147] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    72.155] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    84.583] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[    84.583] (II) modeset(G0): Printing DDC gathered Modelines:
[    84.583] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[    94.081] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[   692.417] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   692.417] (II) modeset(G0): Printing DDC gathered Modelines:
[   692.417] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[   810.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-9415F00B5F6FE128994422C448549EF8FB5837C1.xkm
[   823.705] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   889.158] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   889.158] (II) modeset(G0): Printing DDC gathered Modelines:
[   889.158] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[   889.362] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   889.362] (II) modeset(G0): Printing DDC gathered Modelines:
[   889.362] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[   889.444] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   889.444] (II) modeset(G0): Printing DDC gathered Modelines:
[   889.444] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[   889.499] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   889.499] (II) modeset(G0): Printing DDC gathered Modelines:
[   889.499] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[   889.566] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[   889.566] (II) modeset(G0): Printing DDC gathered Modelines:
[   889.566] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
[  1235.466] (II) config/udev: Adding input device 15:08:29:18:17:DD (/dev/input/event14)
[  1235.466] (**) 15:08:29:18:17:DD: Applying InputClass "evdev keyboard catchall"
[  1235.466] (II) Using input driver 'evdev' for '15:08:29:18:17:DD'
[  1235.466] (**) 15:08:29:18:17:DD: always reports core events
[  1235.466] (**) evdev: 15:08:29:18:17:DD: Device: "/dev/input/event14"
[  1235.466] (--) evdev: 15:08:29:18:17:DD: Vendor 0 Product 0
[  1235.466] (--) evdev: 15:08:29:18:17:DD: Found keys
[  1235.466] (II) evdev: 15:08:29:18:17:DD: Configuring as keyboard
[  1235.466] (**) Option "config_info" "udev:/sys/devices/virtual/input/input15/event14"
[  1235.466] (II) XINPUT: Adding extended input device "15:08:29:18:17:DD" (type: KEYBOARD, id 16)
[  1235.466] (**) Option "xkb_rules" "evdev"
[  1235.466] (**) Option "xkb_model" "pc105"
[  1235.466] (**) Option "xkb_layout" "us"
[  1235.466] (WW) Option "xkb_variant" requires a string value
[  1235.466] (WW) Option "xkb_options" requires a string value
[  1235.477] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1278.562] (II) modeset(G0): EDID vendor "AUO", prod id 5534
[  1278.562] (II) modeset(G0): Printing DDC gathered Modelines:
[  1278.562] (II) modeset(G0): Modeline "1600x900"x0.0  100.00  1600 1648 1680 1798  900 903 909 926 +hsync -vsync (55.6 kHz eP)
```

Looks like it's working. I also run the Unigine Benchmark and it shows that it runs on Nvidia.
Thank you so much for your help!

---

### Post by Bashing-om on 2016-03-11
daniii10; Yepper !

All look'n good ! I think you dood it.

OK, cleanup .
Run:
```

sudo apt update

```
and then; 
```

sudo apt upgrade

```
and post that output back here.
Pay close attention to what the system is going to install and more importantly the recommends for "autoremove" . If you need to, copy this list down somewhere.

We pull the hammer back on the gun, and look before we pull the "autoremove" trigger.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
sudo apt update
```
Hit http://repo.steampowered.com precise InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://security.ubuntu.com wily-security InRelease [65.9 kB]             
Hit http://us.archive.ubuntu.com wily InRelease                                
Ign http://dl.google.com stable InRelease                                      
Get:2 http://us.archive.ubuntu.com wily-updates InRelease [65.9 kB]            
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://archive.canonical.com wily InRelease                                
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable Release                                        
Get:3 http://security.ubuntu.com wily-security/main Sources [39.9 kB]          
Hit http://archive.canonical.com wily/partner Sources                          
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit http://dl.google.com stable/main i386 Packages                             
Get:5 http://security.ubuntu.com wily-security/universe Sources [10.8 kB]      
Hit http://us.archive.ubuntu.com wily/main Sources                             
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit http://us.archive.ubuntu.com wily/restricted Sources                       
Get:6 http://security.ubuntu.com wily-security/multiverse Sources [2,788 B]    
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://us.archive.ubuntu.com wily/universe Sources                         
Get:7 http://security.ubuntu.com wily-security/main amd64 Packages [128 kB]    
Hit http://us.archive.ubuntu.com wily/multiverse Sources                       
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://archive.canonical.com wily/partner i386 Packages                    
Hit http://us.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://archive.canonical.com wily/partner Translation-en                   
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages                
Get:8 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages                  
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Get:9 http://security.ubuntu.com wily-security/universe amd64 Packages [49.3 kB]
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages                
Get:10 http://security.ubuntu.com wily-security/multiverse amd64 Packages [6,247 B]
Hit http://us.archive.ubuntu.com wily/main i386 Packages                       
Get:11 http://security.ubuntu.com wily-security/main i386 Packages [126 kB]    
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages                 
Get:12 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Hit http://us.archive.ubuntu.com wily/universe i386 Packages                   
Get:13 http://security.ubuntu.com wily-security/universe i386 Packages [49.3 kB]
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages                 
Get:14 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,443 B]
Hit http://us.archive.ubuntu.com wily/main Translation-en                      
Hit http://security.ubuntu.com wily-security/main Translation-en               
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en                
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://security.ubuntu.com wily-security/multiverse Translation-en         
Hit http://us.archive.ubuntu.com wily/restricted Translation-en                
Hit http://us.archive.ubuntu.com wily/universe Translation-en                  
Hit http://security.ubuntu.com wily-security/restricted Translation-en         
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://security.ubuntu.com wily-security/universe Translation-en           
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Get:15 http://us.archive.ubuntu.com wily-updates/main Sources [66.4 kB]        
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:16 http://us.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]  
Hit http://ppa.launchpad.net wily/main Translation-en                          
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:17 http://us.archive.ubuntu.com wily-updates/universe Sources [20.7 kB]    
Get:18 http://us.archive.ubuntu.com wily-updates/multiverse Sources [3,199 B]  
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://ppa.launchpad.net wily/main Translation-en                          
Get:19 http://us.archive.ubuntu.com wily-updates/main amd64 Packages [189 kB]  
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:20 http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 http://us.archive.ubuntu.com wily-updates/universe amd64 Packages [86.6 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Get:22 http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages [6,247 B]
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Get:23 http://us.archive.ubuntu.com wily-updates/main i386 Packages [186 kB]
Hit http://ppa.launchpad.net wily/main i386 Packages                         
Hit http://ppa.launchpad.net wily/main Translation-en                        
Get:24 http://us.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Hit http://ppa.launchpad.net wily/main amd64 Packages          
Get:25 http://us.archive.ubuntu.com wily-updates/universe i386 Packages [83.9 kB]
Hit http://ppa.launchpad.net wily/main i386 Packages                      
Get:26 http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,678 B]
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://us.archive.ubuntu.com wily-updates/main Translation-en
Hit http://us.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://ppa.launchpad.net wily/main amd64 Packages
Hit http://us.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://ppa.launchpad.net wily/main i386 Packages
Hit http://ppa.launchpad.net wily/main Translation-en
Hit http://ppa.launchpad.net wily/main amd64 Packages
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Hit http://ppa.launchpad.net wily/main Translation-en                          
Fetched 1,254 kB in 7s (157 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

sudo apt upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  libllvm3.7 libqt4-webkit:i386 linux-headers-4.2.0-21
  linux-headers-4.2.0-21-generic linux-headers-4.2.0-22
  linux-headers-4.2.0-22-generic linux-headers-4.2.0-23
  linux-headers-4.2.0-23-generic linux-headers-4.2.0-25
  linux-headers-4.2.0-25-generic ttf-ancient-fonts
Use 'apt-get autoremove' to remove them.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Should I do?
```
sudo apt-get autoremove
```

---

### Post by Bashing-om on 2016-03-11
daniii10; Well ..

I see nothing yet to preclude the "autoremove" . I do not expect to be presented with a problem.

do:
```

uname -r

```
IF the version returned is not in the autoremove list. then YES pull the trigger.
```

sudo apt-get autoremove

```
again, paying attention to what is removed . just in case .

[INDENT][INDENT]so close now
[INDENT][INDENT][INDENT]can feel it all over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
Is it good?
```
daniel@daniel-Inspiron-5720:~$ uname -r
4.2.0-30-generic
daniel@daniel-Inspiron-5720:~$ sudo apt-get autoremove
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libllvm3.7 libqt4-webkit:i386 linux-headers-4.2.0-21
  linux-headers-4.2.0-21-generic linux-headers-4.2.0-22
  linux-headers-4.2.0-22-generic linux-headers-4.2.0-23
  linux-headers-4.2.0-23-generic linux-headers-4.2.0-25
  linux-headers-4.2.0-25-generic ttf-ancient-fonts
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
After this operation, 343 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 483594 files and directories currently installed.)
Removing libllvm3.7:amd64 (1:3.7-2ubuntu4) ...
Removing libqt4-webkit:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing linux-headers-4.2.0-21-generic (4.2.0-21.25) ...
Removing linux-headers-4.2.0-21 (4.2.0-21.25) ...
Removing linux-headers-4.2.0-22-generic (4.2.0-22.27) ...
Removing linux-headers-4.2.0-22 (4.2.0-22.27) ...
Removing linux-headers-4.2.0-23-generic (4.2.0-23.28) ...
Removing linux-headers-4.2.0-23 (4.2.0-23.28) ...
Removing linux-headers-4.2.0-25-generic (4.2.0-25.30) ...
Removing linux-headers-4.2.0-25 (4.2.0-25.30) ...
Removing ttf-ancient-fonts (2.57-1ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
Processing triggers for fontconfig (2.11.1-0ubuntu6) ...
```

---

### Post by Bashing-om on 2016-03-11
daniii10; Uh Huh !

Looks good !

and last and least .. any stragglers around ?
```

sudo apt-get -f install
sudo dpkg -C

```

[INDENT][INDENT]betcha, finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And: 'sudo dpkg -C' return nothing.

---

### Post by Bashing-om on 2016-03-11
daniii10; Hey !

I think now you are in fine shape.

If you agree;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And as you have added to my knowledge of Intel
[INDENT][INDENT]and
[INDENT][INDENT]we have effected a resolution
[INDENT][INDENT][INDENT]how big of a feather do I put in my war bonnet 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniii10 on 2016-03-11
OK thanks a lot.

---

### Post by Bashing-om on 2016-03-11
> **daniii10 said:**
> OK thanks a lot.

:)

Glad to have helped .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by Kotseto on 2016-03-14
I have the exact same problem. Although I used Ubuntu on a flash drive with 4G memory for saving changes. I got THE SYSTEM IS RUNNING ON LOW GRAPHICS MODE?

I tried loading it again and it just flashes trying to load the correct resolution.

How do I enter Recovery mode on  a USB installed UBUNTU.

I can see the mouse pointer but not anything else.  Will CTRL + ALT + F2 get me anywhere with this guide?
[https://www.youtube.com/watch?v=o31QGpjR8KE](https://www.youtube.com/watch?v=o31QGpjR8KE)

---

### Post by Bashing-om on 2016-03-14
Kotseto; Ouch !

I do expect that you are expecting too much !
> 
 I used Ubuntu on a flash drive with 4G memory 

as I "think" the minimum disk space for (U)buntu is 6 gigs . And even that leaves no room for installing additional software.
I will be glad to be corrected in that minimum requirement.
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
(5 Gigs ??)

[INDENT][INDENT]can not place 10 pounds of sugar
[INDENT][INDENT][INDENT]in a 5 pound bag
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kotseto on 2016-03-16
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)  I will try this to use more Storage on my 15 G usb. For now i stick with 4G live persistent version. I use the mounted drive of Windows to store larger files and the programs i need for Ubuntu fit in 2G :)   As long as the Nvidia proprietary driver tested does not crash I will be fine.
Salvation lies within:
[http://ubuntuforums.org/showthread.php?t=2306441](http://ubuntuforums.org/showthread.php?t=2306441)

---

