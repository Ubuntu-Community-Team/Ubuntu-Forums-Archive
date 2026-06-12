---
title: "ACER timeline 1830TZ boot issue"
date: 2010-10-02
forum: Hardware
---

### Post by beauman on 2010-10-02
From Chris:
Forgive this message and for not posting it on a forum but it is
specific to ACER Timeline series laptop.

I have a problem installing the AMD64 Karmic on this (Acer Timeline x 1830TZ) system. 
After creating a USB installation I get to the
installation menu, tab the install on this PC option and then as it's
beginning to enter the installation the screen goes blank. The Ubuntu
sounds chims after a few minutes, then nothing.

I've tried many of the options in the boot menu, but none seem to work
and after 3 days navigating forums, help menus and trying to reinstall,
i'm at a loose end. (The 386 Karmic version works but none of the
networking drivers are installed, and i can't retrieve them as I can't
get on the net (through wireless or ethernet) - manual downloads aren't
working either because a heap of the dependancies (which aren't
installed) aren't met.)

Has anyone else had this problem or know a fix?

IF anyone could help with specifics (keep in mind i'm fairly new to
Ubuntu) I would really really appreciate it!

Thanks, Chris.

---

### Post by beauman on 2010-10-02
Hi Chris!

Always post your problems in the forum, its useless to
discuss it in private e-mails. 

Did I understand your mail correct, the Ubuntu Version from last year will boot from the stick, where as the ten point ten version
leaves you with a blank screen?

Ubuntu / Linux does a lot of logging, especially during the boot up. You should try to reach the file /var/log/messages. Did you try Ctrl+Alt+F1 to
get a console? If you are in a console you get some messages with Ctrl+F8, with Ctrl+F1 you go back to the console and Ctrl+F7 is your graph.
login. Maybe your X-Server has a problem. It has its own log file, can't remember its location or name.

So long,
jc

---

### Post by roach_chris on 2010-10-03
JC: Thanks for posting this on the forum 
 
... and to all those that gave some email suggestions thank you muchly!
 
... However, the problem still persists. I'm trying to install Ubuntu 10.04 AMD64 using a USB drive. 
 
My Laptop Acer Inspire Timeline X 1830TZ. I don't have a CD drive but will try and borrow an external one to boot from as this problem is really annoying. I used to have a ASUS EEE which recently broke at Everst Base Camp, hence the new one. Ubuntu pretty much worked flawlessly on that machine, shame ASUS wouldn't sponsor me a new one! :)  
 
I've tried a bunch of different boot commands, most of them i only have a limited knowledge of, including
 
acpi_backlight=vendor
acpi_backlight=video
acpi_osi=Linux
acpi=off noapic nolapic
 
Then this: intel_idle.max_cstate=0 which i must confess have no idea what it does but gave it a try anyway after i found it on a post somewhere. I feel a little like a blind peson stumbling in the dark.
 
The 10.04 386 version seemed to install ok, but as per the previous problem is a pain in the **** to get working on my machine. That and i would like a 64 bit machine to recognise the 4G of ram. 
 
Currently trying to download the 10.10 beta from slow internet cafes in Kathmandu and see if that works. 
 
If anyone else has any ideas/experience I'd appreciate the help. 
 
Thanks in advance, Chris

---

### Post by roach_chris on 2010-10-11
... So a week later I downloaded the new Maverick 10.10 AMD64 installed it and still having problems. It's taken a week now and i've gotten nowhere. 

I can run a live shell off the USB and everything seems fine. I install it then get kicked out to a prompt with a login, then after a while the screen goes blank. If i try and start the GUI the screen goes blank. 

The xorg.0.log system file off the USB live shell says something like this:

[    26.079] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    26.079] X Protocol Version 11, Revision 0
[    26.079] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    26.079] Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    26.079] Kernel command line: initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    26.079] Build Date: 16 September 2010  06:18:41PM
[    26.079] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.084] Current version of pixman: 0.18.4
[    26.084]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    26.084] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.084] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 07:45:42 2010
[    26.116] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.127] (==) No Layout section.  Using the first Screen section.
[    26.127] (==) No screen section available. Using defaults.
[    26.127] (**) |-->Screen "Default Screen Section" (0)
[    26.127] (**) |   |-->Monitor "<default monitor>"
[    26.128] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    26.128] (==) Automatically adding devices
[    26.128] (==) Automatically enabling devices
[    26.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.131]     Entry deleted from font path.
[    26.139] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    26.139] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.139] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.139] (II) Loader magic: 0x7d0200
[    26.139] (II) Module ABI versions:
[    26.139]     X.Org ANSI C Emulation: 0.4
[    26.139]     X.Org Video Driver: 8.0
[    26.139]     X.Org XInput driver : 11.0
[    26.139]     X.Org Server Extension : 4.0
[    26.140] (--) PCI:*(0:0:2:0) 8086:0046:1025:040e rev 2, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003050/8
[    26.140] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    26.140] (II) LoadModule: "extmod"
[    26.156] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.172] (II) Module extmod: vendor="X.Org Foundation"
[    26.172]     compiled for 1.9.0, module version = 1.0.0
[    26.172]     Module class: X.Org Server Extension
[    26.172]     ABI class: X.Org Server Extension, version 4.0
[    26.172] (II) Loading extension MIT-SCREEN-SAVER
[    26.172] (II) Loading extension XFree86-VidModeExtension
[    26.172] (II) Loading extension XFree86-DGA
[    26.172] (II) Loading extension DPMS
[    26.172] (II) Loading extension XVideo
[    26.172] (II) Loading extension XVideo-MotionCompensation
[    26.172] (II) Loading extension X-Resource
[    26.172] (II) LoadModule: "dbe"
[    26.173] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.184] (II) Module dbe: vendor="X.Org Foundation"
[    26.184]     compiled for 1.9.0, module version = 1.0.0
[    26.184]     Module class: X.Org Server Extension
[    26.184]     ABI class: X.Org Server Extension, version 4.0
[    26.184] (II) Loading extension DOUBLE-BUFFER
[    26.184] (II) LoadModule: "glx"
[    26.186] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.214] (II) Module glx: vendor="X.Org Foundation"
[    26.214]     compiled for 1.9.0, module version = 1.0.0
[    26.214]     ABI class: X.Org Server Extension, version 4.0
[    26.217] (==) AIGLX enabled
[    26.217] (II) Loading extension GLX
[    26.217] (II) LoadModule: "record"
[    26.266] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.293] (II) Module record: vendor="X.Org Foundation"
[    26.293]     compiled for 1.9.0, module version = 1.13.0
[    26.293]     Module class: X.Org Server Extension
[    26.293]     ABI class: X.Org Server Extension, version 4.0
[    26.293] (II) Loading extension RECORD
[    26.293] (II) LoadModule: "dri"
[    26.293] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.306] (II) Module dri: vendor="X.Org Foundation"
[    26.306]     compiled for 1.9.0, module version = 1.0.0
[    26.306]     ABI class: X.Org Server Extension, version 4.0
[    26.306] (II) Loading extension XFree86-DRI
[    26.306] (II) LoadModule: "dri2"
[    26.307] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.309] (II) Module dri2: vendor="X.Org Foundation"
[    26.309]     compiled for 1.9.0, module version = 1.2.0
[    26.309]     ABI class: X.Org Server Extension, version 4.0
[    26.310] (II) Loading extension DRI2
[    26.310] (==) Matched intel as autoconfigured driver 0
[    26.310] (==) Matched vesa as autoconfigured driver 1
[    26.310] (==) Matched fbdev as autoconfigured driver 2
[    26.310] (==) Assigned the driver to the xf86ConfigLayout
[    26.310] (II) LoadModule: "intel"
[    26.310] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.367] (II) Module intel: vendor="X.Org Foundation"
[    26.367]     compiled for 1.9.0, module version = 2.12.0
[    26.367]     Module class: X.Org Video Driver
[    26.367]     ABI class: X.Org Video Driver, version 8.0
[    26.367] (II) LoadModule: "vesa"
[    26.367] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.383] (II) Module vesa: vendor="X.Org Foundation"
[    26.383]     compiled for 1.8.99.905, module version = 2.3.0
[    26.383]     Module class: X.Org Video Driver
[    26.383]     ABI class: X.Org Video Driver, version 8.0
[    26.383] (II) LoadModule: "fbdev"
[    26.383] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.386] (II) Module fbdev: vendor="X.Org Foundation"
[    26.386]     compiled for 1.8.99.905, module version = 0.4.2
[    26.386]     ABI class: X.Org Video Driver, version 8.0
[    26.386] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    26.387] (II) VESA: driver for VESA chipsets: vesa
[    26.387] (II) FBDEV: driver for framebuffer: fbdev
[    26.387] (++) using VT number 7

[    26.387] (WW) Falling back to old probe method for vesa
[    26.387] (WW) Falling back to old probe method for fbdev
[    26.387] (II) Loading sub module "fbdevhw"
[    26.387] (II) LoadModule: "fbdevhw"
[    26.390] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.395] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.395]     compiled for 1.9.0, module version = 0.0.2
[    26.395]     ABI class: X.Org Video Driver, version 8.0
[    26.404] drmOpenDevice: node name is /dev/dri/card0
[    26.404] drmOpenDevice: open result is 8, (OK)
[    26.404] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.404] drmOpenDevice: node name is /dev/dri/card0
[    26.404] drmOpenDevice: open result is 8, (OK)
[    26.404] drmOpenByBusid: drmOpenMinor returns 8
[    26.404] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.404] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    26.404] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.404] (==) intel(0): RGB weight 888
[    26.404] (==) intel(0): Default visual is TrueColor
[    26.404] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    26.404] (--) intel(0): Chipset: "Arrandale"
[    26.404] (==) intel(0): video overlay key set to 0x101fe
[    26.421] (II) intel(0): Output VGA1 has no monitor section
[    26.421] (II) intel(0): Output LVDS1 has no monitor section
[    26.421] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.457] (II) intel(0): Output HDMI1 has no monitor section
[    26.463] (II) intel(0): Output DP1 has no monitor section
[    26.503] (II) intel(0): EDID for output VGA1
[    26.511] (II) intel(0): EDID for output LVDS1
[    26.511] (II) intel(0): Manufacturer: AUO  Model: 205c  Serial#: 0
[    26.511] (II) intel(0): Year: 2008  Week: 1
[    26.511] (II) intel(0): EDID Version: 1.3
[    26.511] (II) intel(0): Digital Display Input
[    26.511] (II) intel(0): Max Image Size [cm]: horiz.: 26  vert.: 14
[    26.511] (II) intel(0): Gamma: 2.20
[    26.511] (II) intel(0): No DPMS capabilities specified
[    26.511] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.511] (II) intel(0): First detailed timing is preferred mode
[    26.511] (II) intel(0): redX: 0.584 redY: 0.333   greenX: 0.338 greenY: 0.571
[    26.511] (II) intel(0): blueX: 0.158 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
[    26.511] (II) intel(0): Manufacturer's mask: 0
[    26.511] (II) intel(0): Supported detailed timing:
[    26.511] (II) intel(0): clock: 65.5 MHz   Image Size:  256 x 144 mm
[    26.511] (II) intel(0): h_active: 1366  h_sync: 1390  h_sync_end 1406 h_blank_end 1406 h_border: 0
[    26.511] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 774 v_blanking: 776 v_border: 0
[    26.511] (II) intel(0): Unknown vendor-specific block f
[    26.511] (II) intel(0):  AUO
[    26.511] (II) intel(0):  B116XW02 V0
[    26.511] (II) intel(0): EDID (in hex):
[    26.511] (II) intel(0):     00ffffffffffff0006af5c2000000000
[    26.511] (II) intel(0):     01120103801a0e780a99859555569228
[    26.511] (II) intel(0):     22505400000001010101010101010101
[    26.511] (II) intel(0):     01010101010196195628500008301810
[    26.511] (II) intel(0):     24000090100000180000000f00000000
[    26.511] (II) intel(0):     00000000000000000020000000fe0041
[    26.511] (II) intel(0):     554f0a202020202020202020000000fe
[    26.511] (II) intel(0):     004231313658573032205630200a00f8
[    26.512] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.512] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.512] (II) intel(0): Printing probed modes for output LVDS1
[    26.512] (II) intel(0): Modeline "1366x768"x60.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    26.512] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    26.512] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    26.512] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.512] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.512] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.512] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.533] (II) intel(0): EDID for output HDMI1
[    26.538] (II) intel(0): EDID for output DP1
[    26.538] (II) intel(0): Output VGA1 disconnected
[    26.538] (II) intel(0): Output LVDS1 connected
[    26.538] (II) intel(0): Output HDMI1 disconnected
[    26.538] (II) intel(0): Output DP1 disconnected
[    26.538] (II) intel(0): Using exact sizes for initial modes
[    26.538] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    26.538] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.538] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    26.538] (==) intel(0): DPI set to (96, 96)
[    26.538] (II) Loading sub module "fb"
[    26.538] (II) LoadModule: "fb"
[    26.539] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.560] (II) Module fb: vendor="X.Org Foundation"
[    26.560]     compiled for 1.9.0, module version = 1.0.0
[    26.560]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.560] (II) UnloadModule: "vesa"
[    26.560] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.560] (II) UnloadModule: "fbdev"
[    26.560] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.560] (II) UnloadModule: "fbdevhw"
[    26.560] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.560] (==) Depth 24 pixmap format is 32 bpp
[    26.560] (II) intel(0): [DRI2] Setup complete
[    26.560] (II) intel(0): [DRI2]   DRI driver: i965
[    26.560] (**) intel(0): Tiling enabled
[    26.560] (**) intel(0): SwapBuffers wait enabled
[    26.560] (==) intel(0): VideoRam: 262144 KB
[    26.560] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    26.586] (II) UXA(0): Driver registered support for the following operations:
[    26.586] (II)         solid
[    26.586] (II)         copy
[    26.586] (II)         composite (RENDER acceleration)
[    26.586] (II)         put_image
[    26.586] (II)         get_image
[    26.586] (==) intel(0): Backing store disabled
[    26.586] (==) intel(0): Silken mouse enabled
[    26.586] (II) intel(0): Initializing HW Cursor
[    26.640] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.652] (==) intel(0): DPMS enabled
[    26.653] (==) intel(0): Intel XvMC decoder enabled
[    26.653] (II) intel(0): Set up textured video
[    26.653] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    26.653] (II) intel(0): direct rendering: DRI2 Enabled
[    26.653] (--) RandR disabled
[    26.653] (II) Initializing built-in extension Generic Event Extension
[    26.653] (II) Initializing built-in extension SHAPE
[    26.653] (II) Initializing built-in extension MIT-SHM
[    26.653] (II) Initializing built-in extension XInputExtension
[    26.653] (II) Initializing built-in extension XTEST
[    26.653] (II) Initializing built-in extension BIG-REQUESTS
[    26.653] (II) Initializing built-in extension SYNC
[    26.653] (II) Initializing built-in extension XKEYBOARD
[    26.653] (II) Initializing built-in extension XC-MISC
[    26.653] (II) Initializing built-in extension SECURITY
[    26.653] (II) Initializing built-in extension XINERAMA
[    26.653] (II) Initializing built-in extension XFIXES
[    26.653] (II) Initializing built-in extension RENDER
[    26.653] (II) Initializing built-in extension RANDR
[    26.653] (II) Initializing built-in extension COMPOSITE
[    26.653] (II) Initializing built-in extension DAMAGE
[    26.653] (II) Initializing built-in extension GESTURE
[    26.809] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.809] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.809] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.809] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.809] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.809] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    26.809] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.813] (II) intel(0): Setting screen physical size to 361 x 203
[    26.966] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.174] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.174] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.174] (II) LoadModule: "evdev"
[    27.188] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.207] (II) Module evdev: vendor="X.Org Foundation"
[    27.207]     compiled for 1.9.0, module version = 2.3.2
[    27.207]     Module class: X.Org XInput Driver
[    27.207]     ABI class: X.Org XInput driver, version 11.0
[    27.207] (**) Power Button: always reports core events
[    27.207] (**) Power Button: Device: "/dev/input/event2"
[    27.220] (II) Power Button: Found keys
[    27.220] (II) Power Button: Configuring as keyboard
[    27.220] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.220] (**) Option "xkb_rules" "evdev"
[    27.220] (**) Option "xkb_model" "pc105"
[    27.220] (**) Option "xkb_layout" "us"
[    27.222] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    27.222] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.222] (**) Video Bus: always reports core events
[    27.222] (**) Video Bus: Device: "/dev/input/event4"
[    27.240] (II) Video Bus: Found keys
[    27.240] (II) Video Bus: Configuring as keyboard
[    27.240] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    27.240] (**) Option "xkb_rules" "evdev"
[    27.240] (**) Option "xkb_model" "pc105"
[    27.240] (**) Option "xkb_layout" "us"
[    27.244] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    27.244] (II) No input driver/identifier specified (ignoring)
[    27.244] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    27.244] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.244] (**) Sleep Button: always reports core events
[    27.244] (**) Sleep Button: Device: "/dev/input/event0"
[    27.281] (II) Sleep Button: Found keys
[    27.281] (II) Sleep Button: Configuring as keyboard
[    27.281] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    27.281] (**) Option "xkb_rules" "evdev"
[    27.281] (**) Option "xkb_model" "pc105"
[    27.281] (**) Option "xkb_layout" "us"
[    27.286] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event5)
[    27.286] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    27.286] (**) 1.3M WebCam: always reports core events
[    27.286] (**) 1.3M WebCam: Device: "/dev/input/event5"
[    27.300] (II) 1.3M WebCam: Found keys
[    27.300] (II) 1.3M WebCam: Configuring as keyboard
[    27.300] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    27.300] (**) Option "xkb_rules" "evdev"
[    27.300] (**) Option "xkb_model" "pc105"
[    27.300] (**) Option "xkb_layout" "us"
[    27.303] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.303] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.303] (**) AT Translated Set 2 keyboard: always reports core events
[    27.303] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.330] (II) AT Translated Set 2 keyboard: Found keys
[    27.330] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    27.330] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    27.330] (**) Option "xkb_rules" "evdev"
[    27.330] (**) Option "xkb_model" "pc105"
[    27.330] (**) Option "xkb_layout" "us"
[    27.330] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event6)
[    27.330] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    27.331] (**) PS/2 Generic Mouse: always reports core events
[    27.331] (**) PS/2 Generic Mouse: Device: "/dev/input/event6"
[    27.350] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    27.350] (II) PS/2 Generic Mouse: Found relative axes
[    27.350] (II) PS/2 Generic Mouse: Found x and y relative axes
[    27.350] (II) PS/2 Generic Mouse: Configuring as mouse
[    27.350] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    27.350] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.350] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    27.350] (II) PS/2 Generic Mouse: initialized for relative axes.
[    27.350] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    27.350] (II) No input driver/identifier specified (ignoring)
[    29.446] (II) intel(0): EDID vendor "AUO", prod id 8284
[    29.446] (II) intel(0): Printing DDC gathered Modelines:
[    29.446] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    29.481] (II) intel(0): EDID vendor "AUO", prod id 8284
[    29.485] (II) intel(0): Printing DDC gathered Modelines:
[    29.485] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    29.542] (II) intel(0): EDID vendor "AUO", prod id 8284
[    29.542] (II) intel(0): Printing DDC gathered Modelines:
[    29.542] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    29.577] (II) intel(0): EDID vendor "AUO", prod id 8284
[    29.577] (II) intel(0): Printing DDC gathered Modelines:
[    29.577] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    36.132] (II) intel(0): EDID vendor "AUO", prod id 8284
[    36.132] (II) intel(0): Printing DDC gathered Modelines:
[    36.132] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
[    40.042] (II) intel(0): EDID vendor "AUO", prod id 8284
[    40.042] (II) intel(0): Printing DDC gathered Modelines:
[    40.042] (II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)

Perhaps there's something in the boot parameters or systems files I could change?

Thanks in advance for the help.

---

### Post by scottme on 2010-10-11
I have been running Ubuntu on my Acer 3810TZ - which I believe is substantially similar in spec to the 1830TZ apart from screen size - since I got it nearly a year ago, and have never had any significant problems.  I do use the 32-bit version though; with the PAE kernel it is able to make use of all 4GB of installled RAM, so I really don't see the point of installing a 64-bit version. In your place I'd have a go with the 32-bit version.

---

### Post by roach_chris on 2010-10-12
Thanks for the tip, but the problem still persists in the x386 version. 

Here's an update on the problem so far:

I managed to get a semi working system together by changing the video driver to 'VESA' instead of 'intel' in the Xorg.conf file. As suggested here: [http://ubuntuforums.org/archive/index.php/t-379651.html](http://ubuntuforums.org/archive/index.php/t-379651.html)

Although the video is still buggy, flashing an dropping out every now and then, at least that at least gave me a GUI desktop to work with! :) 

I also edited the /etc/default/grub and add 'nomodeset' to GRUB_CMDLINE_LINUX, then run sudo update-grub as suggested here: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes). I'm not really sure that did anything, but i now have a low res version that i can use in the meantime. 

On boot it still throws the system out to a login prompt and then requires the 'startx' command to get the GUI up. Again i have no idea why this is. 

Ideas or suggestions are most welcome. :)

---

### Post by roach_chris on 2010-10-12
I should have also noted that the live version 10.10 in both x386 and AMD64 seems to work fine. I installed the latest release and now the ethernet works but the wireless and audio don't (I realise there are fixes mentioned in the forum for the latter 2 problems). 

On reboot, the same things happens: Get kicked out to login prompt, use startx to open GUI then a blank screen. :(

---

### Post by acrx on 2010-10-12
Hallo zusammen, ich habe 1830tz, erst habe ich Ubuntu 10.04 Desktop 64 bit installiert, dann habe Upgrade auf 10.10 gemacht und alles läuft perfekt, außer touchpad scrolling!

---

### Post by hemiscy on 2010-10-22
> **roach_chris said:**
> I should have also noted that the live version 10.10 in both x386 and AMD64 seems to work fine. I installed the latest release and now the ethernet works but the wireless and audio don't (I realise there are fixes mentioned in the forum for the latter 2 problems). 

On reboot, the same things happens: Get kicked out to login prompt, use startx to open GUI then a blank screen. :(

Exactly the same situation for my 1830TZ (CPU U5400). I have tried amd64, i386 and netbook versions, and I got always the same result: black screen......

---

### Post by roach_chris on 2010-10-23
@hemiscy

Good to know that it's not just me! :)

I got around the blank screen issue by changing the driver to 'VESA' instead of "Intel". (You'll need to edit the Xorg.conf file to do this - search ubuntu forums and you'll find info on what exactly to modify) It's still buggy (screen blanks out every now and then for a few seconds) but at least you get a GUI to work with. None of the compiz effects work tho. Worried that other graphics intensive programs for edit video etc will suffer :(

The sound is still an issue (i.e. doesn't work). Tried just about every combination of sound devices, but nothing. Really regretting the purchase of this machine. I'll try flashing the bios to version 1.11, if that doesn't work i'm going back to Win7. Maybe the next update of the Ubuntu Kernal will fix some of the bugs? Can only wait and hope.... (sigh).

Please post here if you find a workable solution to the sound and video problems. Cheers, Chris.

---

### Post by hemiscy on 2010-10-24
GUI and sound seem to work well in 10.04. I have compiz too. The only issue with 10.04 is no ethernet, no wifi either. The light of wifi is always off, and no way to enable wifi.

Then I upgraded to 10.10 via the iso file of alternate cd. In the boot menu, I choose linux image 2.6.32 (normal mode). I can now use 10.10 with GUI and sound support, but still no internet.

---

### Post by roach_chris on 2010-10-24
> **hemiscy said:**
> GUI and sound seem to work well in 10.04. I have compiz too. The only issue with 10.04 is no ethernet, no wifi either. The light of wifi is always off, and no way to enable wifi.
 
Then I upgraded to 10.10 via the iso file of alternate cd. In the boot menu, I choose linux image 2.6.32 (normal mode). I can now use 10.10 with GUI and sound support, but still no internet.
 
Which country did you buy your laptop from? I hear that Acer have different supplies/manufacturers in different parts of the world (that's a rumour I heard anyway...)
 
What version did you end up going with? The 64 or 32 bit for the 10.04? Desktop? Netbook? 
 
Also, When you did the upgrade via the iso file from the alternate CD did you choose to boot from the old kernal or the new one? ... and lastly, how did you install them? From Wubi, CD or USB (also which program). 
 
I'm going to try and reproduce exactly what you did and see if that works! :)
 
Thanks Hemiscy

---

### Post by hemiscy on 2010-10-26
> **roach_chris said:**
> Which country did you buy your laptop from? I hear that Acer have different supplies/manufacturers in different parts of the world (that's a rumour I heard anyway...)
 
What version did you end up going with? The 64 or 32 bit for the 10.04? Desktop? Netbook? 
 
Also, When you did the upgrade via the iso file from the alternate CD did you choose to boot from the old kernal or the new one? ... and lastly, how did you install them? From Wubi, CD or USB (also which program). 
 
I'm going to try and reproduce exactly what you did and see if that works! :)
 
Thanks Hemiscy

I bought this laptop in Taiwan. I list what I did as below:


[LIST=1]
[*]Download 10.04 amd64 iso
[*]In Windows 7, use Daemon Tool Lite to run wubi for installation
[*]Boot into 10.04. Video and sound work well, but no ethernet and wifi support
[*]Download 10.10 alternet cd iso
[*]Upgrade to 10.10 by following the instruction: [https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD) (Beware not to install grub in /dev/sd0 !)
[*]Restart computer, choose Ubuntu in the boot menu, then choose Linux image 2.6.32 in the next menu.
[*]Video and sound still work, but ethernet and wifi don't function... The other question is, am I really using 10.10?? (since I choose 2.6.32 in the menu)
[*]Try to install AR81Family driver. However, I don't know what I did wrong, I can't no more boot into Ubuntu.
[*]Back to Windows 7, uninstall Ubuntu......
[/LIST]
Chris, could you tell me how you install ubuntu? You use Wubi or real install (into another partition), live USB or live CD? 

It seems that it's Wubi who produces the issue of no video support. This weekend I will try to install from live CD into USB drive.

---

### Post by roach_chris on 2010-10-27
@hemiscy

Thanks for the steps... sounds like your having exactly the same issues. 

After reading your previous post I installed 10.04 32bit Desktop (thinking it would be more stable) using a bootable liveUSB created with Unetbootin (google it). I used the live USB to test it to see what works and what doesn't before installing. The sound and graphics worked as did the wireless after waiting a while for the device manager to recognize the broadcom wireless and installed the propriety software. Fortunately that worked otherwise I would have been stuffed! 

Still can't get ethernet working, nor the internal mic or the touchpad to work properly. Still trawling the forums looking for solutions. Haven't tried the card reader yet. Ubuntu chews the power on this little machine and the fan is pretty  noisy.  I heard on other acer machines that there's a fix for that. Kudos to the person who started this: [https://help.ubuntu.com/community/Aspire1830T](https://help.ubuntu.com/community/Aspire1830T). At least there is a central resource where we and the others can concentrate our efforts.

When I tried 10.10 x64 desktop using a LiveUSB setup, the graphics worked in the live version but **** itself after install. Had to revert back to vesa drivers, but that was dodgy. Let me know how you get on installing from CD.  

Might try and install Ubuntu AGAIN with the 10.10 netbook version. In another thread someone had success with that. Problem is I'm new at Ubuntu and don't really know what i'm doing. Stuff needs to be spoon fed! 

Btw: I contacted Acer who basically said that Acer is specified to work with windows only and anything else is your problem. Great support guys! ... no that's really helpful of you! - I know I will never buy another Acer again. 

... "Hello Windows, lets get reacquainted!"

---

### Post by roach_chris on 2010-10-29
Got the Atheros Ethernet card working by doing this really simple tweak to the Grub config. 

See here: [http://ubuntuforums.org/showpost.php?p=8446793&postcount=12](http://ubuntuforums.org/showpost.php?p=8446793&postcount=12)

Great, one problem down... no only if i could fix this internal microphone, touchpad and the power issues....

---

### Post by hemiscy on 2010-11-01
result of installing 10.10 into usb: fail again

I gave up and went back to 10.04. Now it works well except the cpu fan (always functions) and internal microphone (input level is always too low). Touchpad works with basic support (eg. no two-finger or scroll).

---

### Post by Kgaut on 2010-11-17
Hi guys!

I just bought an Acer Aspire Timeline X 1830TZ, and I'vent got any sound under 10.10, is there a way to set it up? or I've to downgrade to 10.04?

(Network is working fine, expect wifi always turned off)

Cheers

---

