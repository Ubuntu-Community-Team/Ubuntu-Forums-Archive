---
title: "help with sis graphics f&amp;h laptop - no supported modes"
date: 2011-03-09
forum: Hardware
---

### Post by ibiker on 2011-03-09
I have read lots of threads and have got as far as I can with and am hoping that I can get some help to overcome the last stage please...
 
I have my laptop working with Windows7, so know I am having issues with sis graphics - chipset sis671.
 
When I load the sis driver (64 bit) I get an error about being unable to detect any support modes for my screen. I read in another thread about using powerstrip in windows7 to help detect the modes of my laptop screen, but those instructions do not appear to work for me.
 
I will reboot this PC and an copy and paste my log file into this thread in the hope that someone can offer me more advice.
 
Thanks
IanB

---

### Post by ibiker on 2011-03-10
> **ibiker said:**
> I have read lots of threads and have got as far as I can with and am hoping that I can get some help to overcome the last stage please...
 
I have my laptop working with Windows7, so know I am having issues with sis graphics - chipset sis671.
 
When I load the sis driver (64 bit) I get an error about being unable to detect any support modes for my screen. I read in another thread about using powerstrip in windows7 to help detect the modes of my laptop screen, but those instructions do not appear to work for me.
 
I will reboot this PC and an copy and paste my log file into this thread in the hope that someone can offer me more advice.
 
Thanks
IanB

And the log file as promised:

[    20.518] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.518] X Protocol Version 11, Revision 0
[    20.518] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    20.518] Current Operating System: Linux ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64
[    20.518] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
[    20.518] Build Date: 09 January 2011  12:14:27PM
[    20.518] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.518] Current version of pixman: 0.18.4
[    20.518]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    20.518] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.518] (==) Log file: "/var/log/Xorg.2.log", Time: Sat Mar  5 21:50:54 2011
[    20.519] (==) Using config file: "/etc/X11/xorg.conf"
[    20.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.519] (==) No Layout section.  Using the first Screen section.
[    20.519] (**) |-->Screen "Default Screen" (0)
[    20.519] (**) |   |-->Monitor "Configured Monitor"
[    20.519] (**) |   |-->Device "Configured Video Device"
[    20.519] (==) Automatically adding devices
[    20.519] (==) Automatically enabling devices
[    20.519] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.519]     Entry deleted from font path.
[    20.519] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.519] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.519] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.519] (II) Loader magic: 0x7d17a0
[    20.519] (II) Module ABI versions:
[    20.519]     X.Org ANSI C Emulation: 0.4
[    20.519]     X.Org Video Driver: 8.0
[    20.519]     X.Org XInput driver : 11.0
[    20.519]     X.Org Server Extension : 4.0
[    20.520] (--) PCI:*(0:1:0:0) 1039:6351:1558:0801 rev 16, Mem @ 0xc0000000/268435456, 0xd8000000/131072, I/O @ 0x00009000/128
[    20.520] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.520] (II) LoadModule: "extmod"
[    20.521] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.521] (II) Module extmod: vendor="X.Org Foundation"
[    20.521]     compiled for 1.9.0, module version = 1.0.0
[    20.521]     Module class: X.Org Server Extension
[    20.521]     ABI class: X.Org Server Extension, version 4.0
[    20.521] (II) Loading extension MIT-SCREEN-SAVER
[    20.521] (II) Loading extension XFree86-VidModeExtension
[    20.521] (II) Loading extension XFree86-DGA
[    20.521] (II) Loading extension DPMS
[    20.521] (II) Loading extension XVideo
[    20.521] (II) Loading extension XVideo-MotionCompensation
[    20.521] (II) Loading extension X-Resource
[    20.521] (II) LoadModule: "dbe"
[    20.521] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.521] (II) Module dbe: vendor="X.Org Foundation"
[    20.521]     compiled for 1.9.0, module version = 1.0.0
[    20.522]     Module class: X.Org Server Extension
[    20.522]     ABI class: X.Org Server Extension, version 4.0
[    20.522] (II) Loading extension DOUBLE-BUFFER
[    20.522] (II) LoadModule: "glx"
[    20.522] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.522] (II) Module glx: vendor="X.Org Foundation"
[    20.522]     compiled for 1.9.0, module version = 1.0.0
[    20.522]     ABI class: X.Org Server Extension, version 4.0
[    20.522] (==) AIGLX enabled
[    20.522] (II) Loading extension GLX
[    20.522] (II) LoadModule: "record"
[    20.522] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.522] (II) Module record: vendor="X.Org Foundation"
[    20.522]     compiled for 1.9.0, module version = 1.13.0
[    20.522]     Module class: X.Org Server Extension
[    20.522]     ABI class: X.Org Server Extension, version 4.0
[    20.522] (II) Loading extension RECORD
[    20.522] (II) LoadModule: "dri"
[    20.523] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.523] (II) Module dri: vendor="X.Org Foundation"
[    20.523]     compiled for 1.9.0, module version = 1.0.0
[    20.523]     ABI class: X.Org Server Extension, version 4.0
[    20.523] (II) Loading extension XFree86-DRI
[    20.523] (II) LoadModule: "dri2"
[    20.523] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.523] (II) Module dri2: vendor="X.Org Foundation"
[    20.523]     compiled for 1.9.0, module version = 1.2.0
[    20.523]     ABI class: X.Org Server Extension, version 4.0
[    20.523] (II) Loading extension DRI2
[    20.523] (II) LoadModule: "sis671"
[    20.524] (II) Loading /usr/lib/xorg/modules/drivers/sis671_drv.so
[    20.524] (II) Module sis671: vendor="X.Org Foundation"
[    20.524]     compiled for 1.9.0, module version = 0.8.0
[    20.524]     Module class: X.Org Video Driver
[    20.524]     ABI class: X.Org Video Driver, version 8.0
[    20.524] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
    [M]670/[M]770[GX], [M]671/[M]771[GX]
[    20.524] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40/XG42)
[    20.524] (--) using VT number 8

[    20.527] (WW) Falling back to old probe method for sis671
[    20.527] (--) Assigning device section with no busID to primary device
[    20.527] (--) Chipset [M]671/[M]771[GX] found
[    20.527] (II) SIS(0): SiS driver (2006/10/17-1, compiled for X.org 1.9.0.0)
[    20.527] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[    20.527] (II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
[    20.527] (II) SIS(0): *** for documentation, updates and a Premium Version.
[    20.527] (II) SIS(0): RandR rotation support not available in this version.
[    20.527] (II) SIS(0): Dynamic modelist support not available in this version.
[    20.527] (II) SIS(0): Screen growing support not available in this version.
[    20.527] (II) SIS(0): Advanced Xv video blitter not available in this version.
[    20.527] (II) SIS(0): Advanced MergedFB support not available in this version.
[    20.527] (--) SIS(0): sisfb not found
[    20.528] (--) SIS(0): Relocated I/O registers at 0x9000
[    20.528] (II) Loading sub module "ramdac"
[    20.528] (II) LoadModule: "ramdac"
[    20.528] (II) Module "ramdac" already built-in
[    20.528] (II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    20.528] (**) SIS(0): Depth 24, (--) framebuffer bpp 32
[    20.528] (==) SIS(0): RGB weight 888
[    20.528] (==) SIS(0): Default visual is TrueColor
[    20.528] (WW) SIS(0): Could not find/read video BIOS
[    20.528] (==) SIS(0): Color HW cursor is enabled
[    20.528] (II) SIS(0): Using VRAM command queue, size 512k
[    20.528] (==) SIS(0): Hotkey display switching is enabled
[    20.528] (==) SIS(0): SiSCtrl utility interface is disabled
[    20.528] (II) SIS(0): For information on SiSCtrl, see
        [http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
[    20.528] (==) SIS(0): X server will not keep DPI constant for all screen sizes
[    20.528] (==) SIS(0): DRI enabled
[    20.528] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[    20.528] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[    20.528] (--) SIS(0): 262144K shared video RAM (UMA)
[    20.528] (--) SIS(0): DRAM type: DDR SDRAM
[    20.528] (--) SIS(0): Memory clock: 596.582 MHz
[    20.528] (--) SIS(0): DRAM bus width: 64 bit
[    20.528] (--) SIS(0): Linear framebuffer at 0xC0000000
[    20.528] (--) SIS(0): MMIO registers at 0xD8000000 (size 64K)
[    20.528] (--) SIS(0): VideoRAM: 262144 KB
[    20.528] (II) SIS(0): Using 20480K of framebuffer memory at offset 0K
[    20.528] (II) Loading sub module "ddc"
[    20.528] (II) LoadModule: "ddc"
[    20.528] (II) Module "ddc" already built-in
[    20.528] (--) SIS(0): Detected SiS307LV video bridge (Charter/UMC-1, ID 7; Rev 0xe1)
[    22.304] (--) SIS(0): No CRT1/VGA detected
[    22.304] (--) SIS(0): Detected LCD/Plasma panel (max. X 0 Y 0, pref. 0x0, RGB24)
[    22.304] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.304] (II) SIS(0): CRT1 gamma correction is enabled
[    22.304] (II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
[    22.304] (II) SIS(0): CRT2 gamma correction is enabled
[    22.304] (--) SIS(0): Memory bandwidth at 32 bpp is 1193.16 MHz
[    22.304] (--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT2)
[    22.304] (--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT1)
[    22.304] (--) SIS(0): 302LV/302ELV: Using EMI 0x0a0d7038 (LCD)
[    22.304] (--) SIS(0): CRT2 DDC probing failed
[    22.304] (==) SIS(0): Min pixel clock is 10 MHz
[    22.304] (--) SIS(0): Max pixel clock is 340 MHz
[    22.304] (II) SIS(0): Replaced entire mode list with built-in modes
[    22.304] (II) SIS(0): Correcting bogus CRT2 monitor HSync range
[    22.304] (II) SIS(0): Correcting bogus CRT2 monitor VRefresh range
[    22.304] (II) SIS(0): "Unknown reason" in the following list means that the mode
[    22.304] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[    22.305] (II) SIS(0): Configured Monitor: Using hsync range of 30.00-80.00 kHz
[    22.305] (II) SIS(0): Configured Monitor: Using vrefresh range of 59.00-61.00 Hz
[    22.305] (II) SIS(0): Configured Monitor: Using vrefresh value of 71.00 Hz
[    22.305] (WW) SIS(0): Unable to estimate virtual size
[    22.305] (II) SIS(0): Clock range:  10.00 to 340.00 MHz
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "800x600" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "640x480" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1024x768" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.305] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    22.306] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    22.306] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    22.306] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    22.306] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    22.306] (WW) SIS(0): Mode pool is empty
[    22.306] (EE) SIS(0): **************************************************
[    22.306] (EE) SIS(0):                       ERROR:
[    22.306] (EE) SIS(0): No valid modes found - check VertRefresh/HorizSync
[    22.306] (EE) SIS(0):                   END OF MESSAGE
[    22.306] (EE) SIS(0): **************************************************
[    22.306] (II) UnloadModule: "sis671"
[    22.306] (EE) Screen(s) found, but none have a usable configuration.
[    22.306] 
Fatal server error:
[    22.306] no screens found
[    22.306] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    22.306] Please also check the log file at "/var/log/Xorg.2.log" for additional information.
[    22.306] 
[    22.310]  ddxSigGiveUp: Closing log

---

### Post by ibiker on 2011-03-10
And my xorg.conf currently stands as:
  
Section "Device" 
    Identifier    "Configured Video Device" 
    Driver        "vesa" 
#        Driver "sisimedia" 
#    Driver        "sis671" 
     
EndSection 
 
Section "Monitor" 
 Identifier "Configured Monitor 
 HorizSync 28-72 
 VertRefresh 43-60 
# Modeline "1366x768_60.00" 
 Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
 Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync 
 Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync 
 Option   "PreferredMode" "1024x768_60.00" 
EndSection 
 
Section "Screen" 
    Identifier    "Default Screen" 
    Monitor        "Configured Monitor" 
    Device        "Configured Video Device" 
    DefaultDepth     24 
EndSection 

Thanks
IanB

---

