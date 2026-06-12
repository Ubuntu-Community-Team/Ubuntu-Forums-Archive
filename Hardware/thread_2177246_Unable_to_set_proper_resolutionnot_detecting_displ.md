---
title: "Unable to set proper resolution/not detecting display properly"
date: 2013-09-27
forum: Hardware
---

### Post by Michael_Bir on 2013-09-27
I have both a BeagleBone Black and a Raspberry Pi that I'm working with, and figured this would be the best place to ask, since the BBB has Ubuntu with Openbox only and Raspbian is Debian based...


I'm using a Motorola Bionic Lapdock to connect to either device as it's easier in my opinion then having to have a separate full blown monitor, keyboard and mouse hooked up.


First the RPi: with no crazy configuring of any kind, when I hook up the RPi to the dock, it recognizes the dock's 1366 x 768 resolution and both the CLI and the lxde GUI run on the correct resolution.


-However-


For the BBB: when hooked up, it doesn't recognize the monitor the same way and both the CLI and OpenBox GUI are stuck in a 700x568 (I might be slightly off with that number) resolution.


I've read up on editing the xorg.conf and different functions that the "xrandr" command is capable of. When I try 


    xrandr -q


I get a response about it not being able to detect something with the gamma output and then what the min, current, and max resolutions are.  I know the lapdock is capable of the 1366x768 but it says the max is 700x568...


My /etc/X11 folder does not have an xorg.conf file generated and I didn't want to just go start trying to make one and mess things up.


So, my question(s) would be:


What would be the best route for me to take to force the correct resolution?


For the CLI I'm not sure if resolution has anything to do with it, but I would like the text to be smaller as it would be in a higher resolution environment. And as for the Openbox GUI I'd like it to be set to the display's capable 1366x768.  


Update:  I've tried to run:  


    sudo Xorg -configure
 
and it fails telling me that no displays were detected.  I also thought maybe I'd check the xorg.conf file on my Raspberry Pi's Raspbian Distro (seeing as how the resolution and stuff is detected fine on there), but sadly that X11 folder doesn't have an xorg.conf file; however, it does seem to have other files relating to the X server that aren't on my Ubuntu distro.  Also, I tried issuing the command:


    xrandr -q


on my Raspberry Pi, but it reports that it "Can't open display".  So, my conclusion at this point is that I can force the resolution and/or font of the CLI and the GUI without the OS recognizing exactly what the display is, but I don't understand what I can maybe copy over or look for on the Raspbian distro that's causing it to work properly where the Ubuntu distro isn't.


Thanks for any help.


As an updated additional question, I'd wonder if there's a driver I may need that I don't have?  Are there any other generic drivers that might not come stock that I could download for this?  I don't know of any proprietary drivers the Motorola Bionic Lapdock would require, so if anyone might have any ideas on what to check or download in regards to drivers that could help too.


Again here's another addition:
I ran the following command that was recommended on another forum to check the edid information and output when an X session is initiated.


    X -verbose 6 > ~/xlog.txt 2>&1


I was hoping maybe someone experienced in this could read the following output and see if they can figure out what I need to do.


    X.Org X Server 1.11.3
    Release Date: 2011-12-16
    X Protocol Version 11, Revision 0
    Build Operating System: Linux 2.6.42-1426-omap4 armv7l Ubuntu
    Current Operating System: Linux BBB 3.8.13-bone20 #1 SMP Wed May 29 10:49:26 UTC 2013       armv7l
    Kernel command line: console=ttyO0,115200n8 fixrtc root=/dev/mmcblk0p2 ro  rootfstype=ext4 rootwait fixrtc
    Build Date: 11 April 2013  01:10:51PM
    xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
    Current version of pixman: 0.24.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
    Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 27 18:37:40 2013
    (==) Using system config directory "/usr/share/X11/xorg.conf.d"
    (==) No Layout section.  Using the first Screen section.
    (==) No screen section available. Using defaults.
    (**) |-->Screen "Default Screen Section" (0)
    (**) |   |-->Monitor "<default monitor>"
    (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
    (==) Automatically adding devices
    (==) Automatically enabling devices
    (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
    (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
    Entry deleted from font path.
    (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
    Entry deleted from font path.
    (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
    Entry deleted from font path.
    (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
    Entry deleted from font path.
    (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
    (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
    (==) ModulePath set to "/usr/lib/arm-linux-gnueabihf/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
    (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
    (II) Loader magic: 0xb6fa8d00
    (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 11.0
    X.Org XInput driver : 16.0
    X.Org Server Extension : 6.0
    (II) LoadModule: "extmod"
    (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
    (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 6.0
    (II) Loading extension MIT-SCREEN-SAVER
    (II) Loading extension XFree86-VidModeExtension
    (II) Loading extension XFree86-DGA
    (II) Loading extension DPMS
    (II) Loading extension XVideo
    (II) Loading extension XVideo-MotionCompensation
    (II) Loading extension X-Resource
    (II) LoadModule: "dbe"
    (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
    (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 6.0
    (II) Loading extension DOUBLE-BUFFER
    (II) LoadModule: "glx"
    (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
    (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 6.0
    (==) AIGLX enabled
    (II) Loading extension GLX
    (II) LoadModule: "record"
    (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
    (II) Module record: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 6.0
    (II) Loading extension RECORD
    (II) LoadModule: "dri"
    (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
    (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 6.0
    (II) Loading extension XFree86-DRI
    (II) LoadModule: "dri2"
    (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
    (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.2.0
    ABI class: X.Org Server Extension, version 6.0
    (II) Loading extension DRI2
    (==) Matched pvr as autoconfigured driver 0
    (==) Matched fbdev as autoconfigured driver 1
    (==) Assigned the driver to the xf86ConfigLayout
    (II) LoadModule: "pvr"
    (WW) Warning, couldn't open module pvr
    (II) UnloadModule: "pvr"
    (II) Unloading pvr
    (EE) Failed to load module "pvr" (module does not exist, 0)
    (II) LoadModule: "fbdev"
    (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
    (II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 0.4.2
    ABI class: X.Org Video Driver, version 11.0
    (==) Matched pvr as autoconfigured driver 0
    (==) Matched fbdev as autoconfigured driver 1
    (==) Assigned the driver to the xf86ConfigLayout
    (II) LoadModule: "pvr"
    (WW) Warning, couldn't open module pvr
    (II) UnloadModule: "pvr"
    (II) Unloading pvr
    (EE) Failed to load module "pvr" (module does not exist, 0)
    (II) LoadModule: "fbdev"
    (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
    (II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 0.4.2
    ABI class: X.Org Video Driver, version 11.0
    (II) UnloadModule: "fbdev"
    (II) Unloading fbdev
    (II) Failed to load module "fbdev" (already loaded, 0)
    (II) FBDEV: driver for framebuffer: fbdev
    (--) using VT number 8


    (WW) Falling back to old probe method for fbdev
    (II) Loading sub module "fbdevhw"
    (II) LoadModule: "fbdevhw"
    (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
    (II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 0.0.2
    ABI class: X.Org Video Driver, version 11.0
    (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
    (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
    (II) FBDEV(0): using default device
    (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
    (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
    (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16
    (==) FBDEV(0): RGB weight 565
    (==) FBDEV(0): Default visual is TrueColor
    (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
    (II) FBDEV(0): hardware:  (video memory: 810kB)
    (II) FBDEV(0): checking modes against framebuffer device...
    (II) FBDEV(0): checking modes against monitor...
    (--) FBDEV(0): Virtual size is 720x576 (pitch 720)
    (**) FBDEV(0):  Built-in mode "current"
    (==) FBDEV(0): DPI set to (96, 96)
    (II) Loading sub module "fb"
    (II) LoadModule: "fb"
    (II) Loading /usr/lib/xorg/modules/libfb.so
    (II) Module fb: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
    (**) FBDEV(0): using shadow framebuffer
    (II) Loading sub module "shadow"
    (II) LoadModule: "shadow"
    (II) Loading /usr/lib/xorg/modules/libshadow.so
    (II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
    (==) FBDEV(0): Backing store disabled
    (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
    (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
    (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
    (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
    (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument    
    (==) FBDEV(0): DPMS enabled
    (==) RandR enabled
    (II) Initializing built-in extension Generic Event Extension
    (II) Initializing built-in extension SHAPE
    (II) Initializing built-in extension MIT-SHM
    (II) Initializing built-in extension XInputExtension
    (II) Initializing built-in extension XTEST
    (II) Initializing built-in extension BIG-REQUESTS
    (II) Initializing built-in extension SYNC
    (II) Initializing built-in extension XKEYBOARD
    (II) Initializing built-in extension XC-MISC
    (II) Initializing built-in extension SECURITY
    (II) Initializing built-in extension XINERAMA
    (II) Initializing built-in extension XFIXES
    (II) Initializing built-in extension RENDER
    (II) Initializing built-in extension RANDR
    (II) Initializing built-in extension COMPOSITE
    (II) Initializing built-in extension DAMAGE
    (II) AIGLX: Screen 0 is not DRI2 capable
    (II) AIGLX: Screen 0 is not DRI capable
    (II) AIGLX: Loaded and initialized swrast
    (II) GLX: Initialized DRISWRAST GL provider for screen 0
    (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
    (II) XKB: Reusing cached keymap
    (II) config/udev: Adding input device tps65217_pwr_but (/dev/input/event0)
    (**) tps65217_pwr_but: Applying InputClass "evdev keyboard catchall"
    (II) LoadModule: "evdev"
    (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    (II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.11.3, module version = 2.7.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 16.0
    (II) Using input driver 'evdev' for 'tps65217_pwr_but'
    (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    Option "XkbRules" "evdev"
    Option "xkb_model" "pc105"
    Option "xkb_layout" "us"
    Option "_source" "server/udev"
    Option "name" "tps65217_pwr_but"
    Option "path" "/dev/input/event0"
    Option "device" "/dev/input/event0"
    Option "config_info" "udev:/sys/devices/ocp.2/44e0b000.i2c/i2c-0/0-0024/input/input0/event0"
    Option "driver" "evdev"
    (**) tps65217_pwr_but: always reports core events
    (**) evdev: tps65217_pwr_but: Device: "/dev/input/event0"
    (--) evdev: tps65217_pwr_but: Vendor 0 Product 0
    (--) evdev: tps65217_pwr_but: Found keys
    (II) evdev: tps65217_pwr_but: Configuring as keyboard
    (**) Option "config_info" "udev:/sys/devices/ocp.2/44e0b000.i2c/i2c-0/0-0024/input/input0/event0"
    (II) XINPUT: Adding extended input device "tps65217_pwr_but" (type: KEYBOARD, id 6)
    (**) Option "xkb_rules" "evdev"
    (**) Option "xkb_model" "pc105"
    (**) Option "xkb_layout" "us"
    (II) XKB: Reusing cached keymap
    (II) config/udev: Adding input device Motorola Mobility Motorola HD Dock (/dev/input/event1)
    (**) Motorola Mobility Motorola HD Dock: Applying InputClass "evdev keyboard catchall"
    (II) Using input driver 'evdev' for 'Motorola Mobility Motorola HD Dock'
    (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    Option "XkbRules" "evdev"
    Option "xkb_model" "pc105"
    Option "xkb_layout" "us"
    Option "_source" "server/udev"
    Option "name" "Motorola Mobility Motorola HD Dock"
    Option "path" "/dev/input/event1"
    Option "device" "/dev/input/event1"
    Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.1/1-1.1:1.0/input/input1/event1"
    Option "driver" "evdev"
    (**) Motorola Mobility Motorola HD Dock: always reports core events
    (**) evdev: Motorola Mobility Motorola HD Dock: Device: "/dev/input/event1"
    (--) evdev: Motorola Mobility Motorola HD Dock: absolute axis 0x20 [548..0]
    (--) evdev: Motorola Mobility Motorola HD Dock: Vendor 0x22b8 Product 0x938
    (--) evdev: Motorola Mobility Motorola HD Dock: Found 1 mouse buttons
    (--) evdev: Motorola Mobility Motorola HD Dock: Found absolute axes
    (II) evdev: Motorola Mobility Motorola HD Dock: Forcing absolute x/y axes to exist.
    (--) evdev: Motorola Mobility Motorola HD Dock: Found keys
    (II) evdev: Motorola Mobility Motorola HD Dock: Configuring as mouse
    (II) evdev: Motorola Mobility Motorola HD Dock: Configuring as keyboard
    (**) evdev: Motorola Mobility Motorola HD Dock: YAxisMapping: buttons 4 and 5
    (**) evdev: Motorola Mobility Motorola HD Dock: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
    (**) Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.1/1-1.1:1.0/input/input1/event1"
    (II) XINPUT: Adding extended input device "Motorola Mobility Motorola HD Dock" (type: KEYBOARD, id 7)
    (**) Option "xkb_rules" "evdev"
    (**) Option "xkb_model" "pc105"
    (**) Option "xkb_layout" "us"
    (II) XKB: Reusing cached keymap
    (II) evdev: Motorola Mobility Motorola HD Dock: initialized for absolute axes.
    (**) Motorola Mobility Motorola HD Dock: (accel) keeping acceleration scheme 1
    (**) Motorola Mobility Motorola HD Dock: (accel) acceleration profile 0
    (**) Motorola Mobility Motorola HD Dock: (accel) acceleration factor: 2.000
    (**) Motorola Mobility Motorola HD Dock: (accel) acceleration threshold: 4
    (II) config/udev: Adding input device Motorola USB keyboard [us basic] (/dev/input/event2)
    (**) Motorola USB keyboard [us basic]: Applying InputClass "evdev keyboard catchall"
    (II) Using input driver 'evdev' for 'Motorola USB keyboard [us basic]'
    (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    Option "XkbRules" "evdev"
    Option "xkb_model" "pc105"
    Option "xkb_layout" "us"
    Option "_source" "server/udev"
    Option "name" "Motorola USB keyboard [us basic]"
    Option "path" "/dev/input/event2"
    Option "device" "/dev/input/event2"
    Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
    Option "driver" "evdev"
    (**) Motorola USB keyboard [us basic]: always reports core events
    (**) evdev: Motorola USB keyboard [us basic]: Device: "/dev/input/event2"
    (--) evdev: Motorola USB keyboard [us basic]: Vendor 0x22b8 Product 0x93a
    (--) evdev: Motorola USB keyboard [us basic]: Found keys
    (II) evdev: Motorola USB keyboard [us basic]: Configuring as keyboard
    (**) Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
    (II) XINPUT: Adding extended input device "Motorola USB keyboard [us basic]" (type: KEYBOARD, id 8)
    (**) Option "xkb_rules" "evdev"
    (**) Option "xkb_model" "pc105"
    (**) Option "xkb_layout" "us"
    (II) XKB: Reusing cached keymap
    (II) config/udev: Adding input device Motorola USB keyboard [us basic] (/dev/input/event3)
    (**) Motorola USB keyboard [us basic]: Applying InputClass "evdev pointer catchall"
    (**) Motorola USB keyboard [us basic]: Applying InputClass "evdev keyboard catchall"
    (II) Using input driver 'evdev' for 'Motorola USB keyboard [us basic]'
    (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    Option "XkbRules" "evdev"
    Option "xkb_model" "pc105"
    Option "xkb_layout" "us"
    Option "_source" "server/udev"
    Option "name" "Motorola USB keyboard [us basic]"
    Option "path" "/dev/input/event3"
    Option "device" "/dev/input/event3"
    Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.3/1-1.3:1.1/input/input3/event3"
    Option "driver" "evdev"
    (**) Motorola USB keyboard [us basic]: always reports core events
    (**) evdev: Motorola USB keyboard [us basic]: Device: "/dev/input/event3"
    (--) evdev: Motorola USB keyboard [us basic]: Vendor 0x22b8 Product 0x93a
    (--) evdev: Motorola USB keyboard [us basic]: Found 9 mouse buttons
    (--) evdev: Motorola USB keyboard [us basic]: Found scroll wheel(s)
    (--) evdev: Motorola USB keyboard [us basic]: Found relative axes
    (--) evdev: Motorola USB keyboard [us basic]: Found x and y relative axes
    (--) evdev: Motorola USB keyboard [us basic]: Found keys
    (II) evdev: Motorola USB keyboard [us basic]: Configuring as mouse
    (II) evdev: Motorola USB keyboard [us basic]: Configuring as keyboard
    (II) evdev: Motorola USB keyboard [us basic]: Adding scrollwheel support
    (**) evdev: Motorola USB keyboard [us basic]: YAxisMapping: buttons 4 and 5
    (**) evdev: Motorola USB keyboard [us basic]: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
    (**) Option "config_info" "udev:/sys/devices/ocp.2/47400000.usb/musb-hdrc.1.auto/usb1/1-1/1-1.3/1-1.3:1.1/input/input3/event3"
    (II) XINPUT: Adding extended input device "Motorola USB keyboard [us basic]" (type: KEYBOARD, id 9)
    (**) Option "xkb_rules" "evdev"
    (**) Option "xkb_model" "pc105"
    (**) Option "xkb_layout" "us"
    (II) XKB: Reusing cached keymap
    (II) evdev: Motorola USB keyboard [us basic]: initialized for relative axes.
    (**) Motorola USB keyboard [us basic]: (accel) keeping acceleration scheme 1
    (**) Motorola USB keyboard [us basic]: (accel) acceleration profile 0
    (**) Motorola USB keyboard [us basic]: (accel) acceleration factor: 2.000
    (**) Motorola USB keyboard [us basic]: (accel) acceleration threshold: 4
    (II) config/udev: Adding input device Motorola USB keyboard [us basic] (/dev/input/mouse0)
    (II) No input driver specified, ignoring this device.
    (II) This device may have been added with another device file.
    (II) evdev: Motorola USB keyboard [us basic]: Close
    (II) UnloadModule: "evdev"
    (II) Unloading evdev
    (II) evdev: Motorola USB keyboard [us basic]: Close
    (II) UnloadModule: "evdev"
    (II) Unloading evdev
    (II) evdev: Motorola Mobility Motorola HD Dock: Close
    (II) UnloadModule: "evdev"
    (II) Unloading evdev
    (II) evdev: tps65217_pwr_but: Close
    (II) UnloadModule: "evdev"
    (II) Unloading evdev
    ddxSigGiveUp: Closing log
    Server terminated successfully (0). Closing log file.

---

