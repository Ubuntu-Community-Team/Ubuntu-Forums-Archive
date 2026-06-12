---
title: "Xubuntu 10.10 screen resolution problem"
date: 2011-03-25
forum: Hardware
---

### Post by websterhamster on 2011-03-25
Hi, This appears to be a very widespread problem, but I haven't found a solution that works yet. Here's hoping this thread will have that answer.

The problem is this: I am running Xubuntu 10.10 live on a CD on a Dell Inspiron 2500 laptop (older laptop). I want to know if it will work before installing it, but it won't give me a proper screen resolution. The laptop needs 1024x768, but Xubuntu will give me a maximum of 800x600. I tried xrandr, that didn't help. I can't edit the xorg.conf file because I don't have it (for some reason, there isn't one).

**So, I need a way to get it to use 1024x768 screen resolution.** :confused: I am a Windows Power User, but am a Linux Power Looser (been using win for most of my life, but lin for maybe a year, and very casually). I need a solution asap.

Thanks for the help, I really appreciate it.

---

### Post by realzippy on 2011-03-25
Install it,then fix the resolution.Also your XP might be bootable again,or is this solved? (had a look at your other post)

---

### Post by websterhamster on 2011-03-25
Actually, XP does boot on the laptop, but I guess something to do with the video card was messed up. It boots, but then I guess about when it begins to load video drivers the screen goes blank. 

I don't want to actually install the OS until I know for sure the screen res will be right after. Is this problem caused because I'm running it live?

Thanks for the help

---

### Post by Yellow Pasque on 2011-03-25
Post your /var/log/Xorg.0.log

---

### Post by realzippy on 2011-03-25
Yes,due to the live session.
Nowadays an xorg.conf is only needed when running proprietary drivers or when having resolution problems since the kernel sets the video driver,if it fails,setting up a xorg.conf is 1rst choice.
[Here]("http://ubuntuforums.org/showthread.php?t=750372") eg is one I would start with..


and welcome to ubuntuforums...

---

### Post by websterhamster on 2011-03-25
Thanks. I copied the xorg.conf into the /etc/x11 folder, do I have to do anything else to change the resolution?

---

### Post by realzippy on 2011-03-25
..the X11 folder,not x11 I hope.Linux is case-sensitive.
Do you still run the liveCD?


Edit:

Try Alt+Ctrl+Backspace to restart X server with new xorg.conf
I never tried this from a liveCD....

---

### Post by websterhamster on 2011-03-25
Yes, X11. I am still running the live CD. 

I did Ctrl+Alt+Backspace, and nothing happened. I typed Ctrl+Alt+F1, and it took me to the text-based shell. What command should I enter to restart the X server?

---

### Post by realzippy on 2011-03-25
Try
```
sudo kill `cat /tmp/.X0-lock`

```

```
startx
```

---

### Post by Yellow Pasque on 2011-03-25
> **Temüjin said:**
> Post your /var/log/Xorg.0.log

...

---

### Post by websterhamster on 2011-03-25
I think I found my problem. When I ran startx, it gave me a bunch of errors, including "No Drivers Available" and "No Screens Found". Does this mean I have to install drivers :0 ?

---

### Post by websterhamster on 2011-03-25
Here comes the log file

---

### Post by websterhamster on 2011-03-25
```
[   267.602] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   267.603] X Protocol Version 11, Revision 0
[   267.603] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   267.603] Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   267.603] Kernel command line: file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[   267.603] Build Date: 16 September 2010  05:39:22PM
[   267.603] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   267.965] Current version of pixman: 0.18.4
[   267.965]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   267.965] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   267.966] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 25 14:39:06 2011
[   268.181] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   269.213] (==) No Layout section.  Using the first Screen section.
[   269.213] (==) No screen section available. Using defaults.
[   269.214] (**) |-->Screen "Default Screen Section" (0)
[   269.214] (**) |   |-->Monitor "<default monitor>"
[   269.215] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   269.215] (==) Automatically adding devices
[   269.215] (==) Automatically enabling devices
[   269.236] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   269.236]     Entry deleted from font path.
[   269.360] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   269.360] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   269.360] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   269.360] (II) Loader magic: 0x81f8e00
[   269.360] (II) Module ABI versions:
[   269.360]     X.Org ANSI C Emulation: 0.4
[   269.360]     X.Org Video Driver: 8.0
[   269.360]     X.Org XInput driver : 11.0
[   269.360]     X.Org Server Extension : 4.0
[   269.363] (--) PCI:*(0:0:2:0) 8086:1132:1028:00c9 rev 17, Mem @ 0xf8000000/67108864, 0xf4000000/524288
[   269.384] (II) Open ACPI successful (/var/run/acpid.socket)
[   269.384] (II) LoadModule: "extmod"
[   269.508] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   269.784] (II) Module extmod: vendor="X.Org Foundation"
[   269.784]     compiled for 1.9.0, module version = 1.0.0
[   269.784]     Module class: X.Org Server Extension
[   269.784]     ABI class: X.Org Server Extension, version 4.0
[   269.784] (II) Loading extension MIT-SCREEN-SAVER
[   269.785] (II) Loading extension XFree86-VidModeExtension
[   269.785] (II) Loading extension XFree86-DGA
[   269.785] (II) Loading extension DPMS
[   269.785] (II) Loading extension XVideo
[   269.785] (II) Loading extension XVideo-MotionCompensation
[   269.785] (II) Loading extension X-Resource
[   269.785] (II) LoadModule: "dbe"
[   269.787] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   270.684] (II) Module dbe: vendor="X.Org Foundation"
[   270.684]     compiled for 1.9.0, module version = 1.0.0
[   270.684]     Module class: X.Org Server Extension
[   270.684]     ABI class: X.Org Server Extension, version 4.0
[   270.684] (II) Loading extension DOUBLE-BUFFER
[   270.685] (II) LoadModule: "glx"
[   270.697] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   271.161] (II) Module glx: vendor="X.Org Foundation"
[   271.161]     compiled for 1.9.0, module version = 1.0.0
[   271.162]     ABI class: X.Org Server Extension, version 4.0
[   271.187] (==) AIGLX enabled
[   271.187] (II) Loading extension GLX
[   271.238] (II) LoadModule: "record"
[   271.259] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   271.287] (II) Module record: vendor="X.Org Foundation"
[   271.287]     compiled for 1.9.0, module version = 1.13.0
[   271.287]     Module class: X.Org Server Extension
[   271.287]     ABI class: X.Org Server Extension, version 4.0
[   271.287] (II) Loading extension RECORD
[   271.287] (II) LoadModule: "dri"
[   271.289] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   271.356] (II) Module dri: vendor="X.Org Foundation"
[   271.356]     compiled for 1.9.0, module version = 1.0.0
[   271.356]     ABI class: X.Org Server Extension, version 4.0
[   271.356] (II) Loading extension XFree86-DRI
[   271.356] (II) LoadModule: "dri2"
[   271.358] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   271.404] (II) Module dri2: vendor="X.Org Foundation"
[   271.404]     compiled for 1.9.0, module version = 1.2.0
[   271.404]     ABI class: X.Org Server Extension, version 4.0
[   271.404] (II) Loading extension DRI2
[   271.405] (==) Matched intel as autoconfigured driver 0
[   271.405] (==) Matched vesa as autoconfigured driver 1
[   271.405] (==) Matched fbdev as autoconfigured driver 2
[   271.405] (==) Assigned the driver to the xf86ConfigLayout
[   271.405] (II) LoadModule: "intel"
[   271.406] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   272.345] (II) Module intel: vendor="X.Org Foundation"
[   272.345]     compiled for 1.9.0, module version = 2.12.0
[   272.345]     Module class: X.Org Video Driver
[   272.345]     ABI class: X.Org Video Driver, version 8.0
[   272.346] (II) LoadModule: "vesa"
[   272.347] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   272.637] (II) Module vesa: vendor="X.Org Foundation"
[   272.637]     compiled for 1.8.99.905, module version = 2.3.0
[   272.637]     Module class: X.Org Video Driver
[   272.637]     ABI class: X.Org Video Driver, version 8.0
[   272.637] (II) LoadModule: "fbdev"
[   272.639] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   273.217] (II) Module fbdev: vendor="X.Org Foundation"
[   273.217]     compiled for 1.8.99.905, module version = 0.4.2
[   273.218]     ABI class: X.Org Video Driver, version 8.0
[   273.218] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[   273.242] (II) VESA: driver for VESA chipsets: vesa
[   273.243] (II) FBDEV: driver for framebuffer: fbdev
[   273.243] (++) using VT number 7

[   273.248] (WW) Falling back to old probe method for vesa
[   273.248] (WW) Falling back to old probe method for fbdev
[   273.248] (II) Loading sub module "fbdevhw"
[   273.248] (II) LoadModule: "fbdevhw"
[   273.308] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   273.321] (II) Module fbdevhw: vendor="X.Org Foundation"
[   273.322]     compiled for 1.9.0, module version = 0.0.2
[   273.322]     ABI class: X.Org Video Driver, version 8.0
[   273.322] (EE) open /dev/fb0: No such file or directory
[   273.322] (II) Loading sub module "vgahw"
[   273.322] (II) LoadModule: "vgahw"
[   273.376] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   273.404] (II) Module vgahw: vendor="X.Org Foundation"
[   273.404]     compiled for 1.9.0, module version = 0.1.0
[   273.404]     ABI class: X.Org Video Driver, version 8.0
[   273.405] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
[   273.405] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[   273.405] (==) intel(0): RGB weight 565
[   273.405] (==) intel(0): Default visual is TrueColor
[   273.405] (II) Loading sub module "xaa"
[   273.405] (II) LoadModule: "xaa"
[   273.434] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   273.881] (II) Module xaa: vendor="X.Org Foundation"
[   273.881]     compiled for 1.9.0, module version = 1.2.1
[   273.881]     ABI class: X.Org Video Driver, version 8.0
[   273.881] (II) Loading sub module "vbe"
[   273.881] (II) LoadModule: "vbe"
[   273.883] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   273.915] (II) Module vbe: vendor="X.Org Foundation"
[   273.915]     compiled for 1.9.0, module version = 1.1.0
[   273.915]     ABI class: X.Org Video Driver, version 8.0
[   273.915] (II) Loading sub module "int10"
[   273.915] (II) LoadModule: "int10"
[   273.918] (II) Loading /usr/lib/xorg/modules/libint10.so
[   273.991] (II) Module int10: vendor="X.Org Foundation"
[   273.991]     compiled for 1.9.0, module version = 1.0.0
[   273.991]     ABI class: X.Org Video Driver, version 8.0
[   273.991] (II) intel(0): initializing int10
[   274.040] (II) intel(0): Bad V_BIOS checksum
[   274.041] (II) intel(0): Primary V_BIOS segment is: 0xc000
[   274.042] (II) intel(0): VESA BIOS detected
[   274.042] (II) intel(0): VESA VBE Version 3.0
[   274.042] (II) intel(0): VESA VBE Total Mem: 1024 kB
[   274.042] (II) intel(0): VESA VBE OEM: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
[   274.042] (II) intel(0): VESA VBE OEM Software Rev: 1.0
[   274.042] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[   274.042] (II) intel(0): VESA VBE OEM Product: i815M Graphics Controller
[   274.042] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[   274.042] (II) Loading sub module "ddc"
[   274.042] (II) LoadModule: "ddc"
[   274.042] (II) Module "ddc" already built-in
[   274.561] (II) intel(0): VESA VBE DDC supported
[   274.561] (II) intel(0): VESA VBE DDC Level none
[   274.561] (II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
[   274.893] (II) intel(0): VESA VBE DDC read failed
[   274.894] (--) intel(0): Chipset: "i815"
[   274.894] (--) intel(0): Linear framebuffer at 0xF8000000
[   274.894] (--) intel(0): IO registers at addr 0xF4000000
[   274.895] (II) intel(0): Kernel reported 108544 total, 1 used
[   274.895] (II) intel(0): I810CheckAvailableMemory: 434172k available
[   274.895] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[   274.895] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[   274.895] (II) intel(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
[   274.895] (II) intel(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[   274.895] (WW) intel(0): Unable to estimate virtual size
[   274.895] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[   274.895] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[   274.895] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   274.895] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[   274.895] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   274.895] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[   274.912] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[   274.912] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[   274.912] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "640x480" (hsync out of range)
[   274.912] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   274.912] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[   274.912] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[   274.913] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   274.913] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.913] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[   274.914] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[   274.914] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "832x624" (hsync out of range)
[   274.915] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   274.915] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.915] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   274.936] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[   274.936] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   274.937] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[   274.937] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   274.937] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[   274.937] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   274.937] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[   274.948] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[   274.948] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[   274.948] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[   274.948] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[   274.948] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   274.948] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[   274.949] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[   274.949] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[   274.949] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   274.949] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   274.950] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   274.950] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   274.950] (--) intel(0): Virtual size is 800x600 (pitch 1024)
[   274.950] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   274.950] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   274.950] (**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[   274.950] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   274.950] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   274.950] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   274.950] (==) intel(0): DPI set to (96, 96)
[   274.950] (II) Loading sub module "fb"
[   274.950] (II) LoadModule: "fb"
[   274.985] (II) Loading /usr/lib/xorg/modules/libfb.so
[   275.625] (II) Module fb: vendor="X.Org Foundation"
[   275.625]     compiled for 1.9.0, module version = 1.0.0
[   275.625]     ABI class: X.Org ANSI C Emulation, version 0.4
[   275.625] (II) Loading sub module "ramdac"
[   275.625] (II) LoadModule: "ramdac"
[   275.625] (II) Module "ramdac" already built-in
[   275.625] (**) intel(0): page flipping disabled
[   275.625] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[   275.626] (II) UnloadModule: "vesa"
[   275.626] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   275.626] (II) UnloadModule: "fbdev"
[   275.626] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   275.626] (II) UnloadModule: "fbdevhw"
[   275.626] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   275.626] drmOpenDevice: node name is /dev/dri/card0
[   275.666] drmOpenDevice: node name is /dev/dri/card0
[   277.355] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   277.355] drmOpenDevice: node name is /dev/dri/card0
[   277.355] drmOpenDevice: open result is 12, (OK)
[   277.355] drmOpenByBusid: drmOpenMinor returns 12
[   277.356] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   277.356] (II) [drm] loaded kernel module for "i810" driver.
[   277.356] (II) [drm] DRM interface version 1.3
[   277.356] (II) [drm] DRM open master succeeded.
[   277.356] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[   277.356] (II) intel(0): [drm] framebuffer handle = 0xf8000000
[   277.357] (II) intel(0): [drm] added 1 reserved context for kernel
[   277.357] (II) intel(0): X context handle = 0x1
[   277.357] (II) intel(0): [drm] installed DRM signal handler
[   277.357] (II) intel(0): [drm] Registers = 0xf4000000
[   277.358] (II) intel(0): [agp] dcacheHandle : 0x1
[   277.358] (II) intel(0): [agp] GART: Found 4096K Z buffer memory
[   277.407] (II) intel(0): [agp] Bound backbuffer memory
[   278.467] (II) intel(0): [agp] Bound System Texture Memory
[   278.496] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[   278.496] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[   278.497] (II) intel(0): Adding 768 scanlines for pixmap caching
[   278.497] (II) intel(0): Allocated Scratch Memory
[   278.497] (II) intel(0): [dri] Buffer map : 15cb000
[   278.497] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[   278.497] (II) intel(0): [drm] Init v1.4 interface.
[   278.522] (II) intel(0): [drm] dma control initialized, using IRQ -22
[   278.523] (II) intel(0): [dri] visual configs initialized.
[   278.631] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   279.108] (II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
[   279.108] (II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)
[   279.197] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[   279.198]     Screen to screen bit blits
[   279.198]     Solid filled rectangles
[   279.198]     8x8 mono pattern filled rectangles
[   279.198]     Indirect CPU to Screen color expansion
[   279.198]     Solid Horizontal and Vertical Lines
[   279.198]     Setting up tile and stipple cache:
[   279.198]         28 128x128 slots
[   279.198]         6 256x256 slots
[   279.198] (==) intel(0): Backing store disabled
[   279.198] (==) intel(0): Silken mouse enabled
[   279.199] (==) intel(0): DPMS enabled
[   279.199] (II) intel(0): [DRI] installation complete
[   279.199] (II) intel(0): Direct rendering enabled
[   279.225] (==) RandR enabled
[   279.225] (II) Initializing built-in extension Generic Event Extension
[   279.225] (II) Initializing built-in extension SHAPE
[   279.225] (II) Initializing built-in extension MIT-SHM
[   279.225] (II) Initializing built-in extension XInputExtension
[   279.225] (II) Initializing built-in extension XTEST
[   279.225] (II) Initializing built-in extension BIG-REQUESTS
[   279.225] (II) Initializing built-in extension SYNC
[   279.225] (II) Initializing built-in extension XKEYBOARD
[   279.225] (II) Initializing built-in extension XC-MISC
[   279.225] (II) Initializing built-in extension SECURITY
[   279.225] (II) Initializing built-in extension XINERAMA
[   279.225] (II) Initializing built-in extension XFIXES
[   279.225] (II) Initializing built-in extension RENDER
[   279.225] (II) Initializing built-in extension RANDR
[   279.226] (II) Initializing built-in extension COMPOSITE
[   279.226] (II) Initializing built-in extension DAMAGE
[   279.226] (II) Initializing built-in extension GESTURE
[   279.606] (II) AIGLX: Screen 0 is not DRI2 capable
[   279.606] drmOpenDevice: node name is /dev/dri/card0
[   279.606] drmOpenDevice: open result is 13, (OK)
[   282.608] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   282.608] drmOpenDevice: node name is /dev/dri/card0
[   282.609] drmOpenDevice: open result is 13, (OK)
[   282.609] drmOpenByBusid: drmOpenMinor returns 13
[   282.609] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   284.687] (II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
[   284.687] (II) GLX: Initialized DRI GL provider for screen 0
[   288.069] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   291.445] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   291.445] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   291.445] (II) LoadModule: "evdev"
[   291.473] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   292.351] (II) Module evdev: vendor="X.Org Foundation"
[   292.352]     compiled for 1.9.0, module version = 2.3.2
[   292.352]     Module class: X.Org XInput Driver
[   292.352]     ABI class: X.Org XInput driver, version 11.0
[   292.352] (**) Power Button: always reports core events
[   292.352] (**) Power Button: Device: "/dev/input/event2"
[   292.352] (II) Power Button: Found keys
[   292.352] (II) Power Button: Configuring as keyboard
[   292.352] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   292.352] (**) Option "xkb_rules" "evdev"
[   292.353] (**) Option "xkb_model" "pc105"
[   292.353] (**) Option "xkb_layout" "us"
[   292.380] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   292.380] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   292.380] (**) Video Bus: always reports core events
[   292.380] (**) Video Bus: Device: "/dev/input/event4"
[   292.381] (II) Video Bus: Found keys
[   292.381] (II) Video Bus: Configuring as keyboard
[   292.381] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   292.381] (**) Option "xkb_rules" "evdev"
[   292.381] (**) Option "xkb_model" "pc105"
[   292.381] (**) Option "xkb_layout" "us"
[   292.411] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   292.411] (II) No input driver/identifier specified (ignoring)
[   292.437] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   292.437] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   292.437] (**) Sleep Button: always reports core events
[   292.437] (**) Sleep Button: Device: "/dev/input/event1"
[   292.438] (II) Sleep Button: Found keys
[   292.438] (II) Sleep Button: Configuring as keyboard
[   292.438] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   292.438] (**) Option "xkb_rules" "evdev"
[   292.438] (**) Option "xkb_model" "pc105"
[   292.438] (**) Option "xkb_layout" "us"
[   292.604] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   292.604] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   292.605] (**) AT Translated Set 2 keyboard: always reports core events
[   292.605] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   292.605] (II) AT Translated Set 2 keyboard: Found keys
[   292.605] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   292.605] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   292.605] (**) Option "xkb_rules" "evdev"
[   292.605] (**) Option "xkb_model" "pc105"
[   292.605] (**) Option "xkb_layout" "us"
[   292.632] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   292.632] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   292.632] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   292.632] (II) LoadModule: "synaptics"
[   292.634] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   292.660] (II) Module synaptics: vendor="X.Org Foundation"
[   292.660]     compiled for 1.9.0, module version = 1.2.2
[   292.660]     Module class: X.Org XInput Driver
[   292.660]     ABI class: X.Org XInput driver, version 11.0
[   292.660] (II) Synaptics touchpad driver version 1.2.2
[   292.661] (**) Option "Device" "/dev/input/event5"
[   292.661] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   292.661] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   292.661] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   292.661] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   292.661] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   292.661] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   292.661] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   292.661] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   292.662] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   292.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   292.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   292.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   292.663] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   292.693] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   292.693] (II) No input driver/identifier specified (ignoring)
```

---

### Post by Yellow Pasque on 2011-03-25
Ok, you need to specify some things manually, because X is not autodetecting them correctly. Try using this as an /etc/X11/xorg.conf file:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
EndSection

Section "Files"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Virtual     1024 768
    EndSubSection
EndSection
```

---

### Post by realzippy on 2011-03-26
[I]Try using this as an /etc/X11/xorg.conf
[/I]
@Temüjin

... you have an idea how to restart X from running LiveCD Xubuntu ?

... why not using formerly suggested xorg.conf?

... why 
Depth       16
Virtual     1024 768   ?

---

### Post by realzippy on 2011-03-26
> **websterhamster said:**
> Yes, X11. I am still running the live CD. 

I did Ctrl+Alt+Backspace, and nothing happened. I typed Ctrl+Alt+F1, and it took me to the text-based shell. What command should I enter to restart the X server?

...just noticed that alt+ctrl+backspace is disabled by default now.
To enable:

```
setxkbmap -option terminate:ctrl_alt_bksp
```

---

