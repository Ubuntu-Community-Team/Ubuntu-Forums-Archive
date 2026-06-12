---
title: "Xorg catches segmentation fault on boot after installing fglrx on 13.10"
date: 2014-01-17
forum: Hardware
---

### Post by a2r on 2014-01-17
Hello this is a continuation of an other thread but I openend a new one to be more specific (the old one: [http://ubuntuforums.org/showthread.php?t=2198047](http://ubuntuforums.org/showthread.php?t=2198047))

I couldn't get any fglrx working on any distro newer then 13.04. In the old thread I was on 14.04 but since it isn't released yet I wanted to be sure that my problem and my debuging info is not influenced by an unstable build.
My graphics card is a Mobility Radeon HD 5650
 Here is a step by step description of what I did:

1. Installed 13.10 and only made an apt-get upgrade

2. Compared the version of fglrx and fglrx-updates (both the same)

3. I installed fglrx and ran "amdconfig --inital -f the output is here:
```
arthur@Nostromo:~$ sudo apt-cache policy fglrx
fglrx:
  Installed: (none)
  Candidate: 2:13.101-0ubuntu3
  Version table:
     2:13.101-0ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ saucy/restricted amd64 Packages
arthur@Nostromo:~$ sudo apt-cache policy fglrx-updates
fglrx-updates:
  Installed: (none)
  Candidate: 2:13.101-0ubuntu3
  Version table:
     2:13.101-0ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ saucy/restricted amd64 Packages
arthur@Nostromo:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle lib32gcc1 libc6-i386
The following NEW packages will be installed:
  fglrx fglrx-amdcccle lib32gcc1 libc6-i386
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 92,4 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://de.archive.ubuntu.com/ubuntu/ saucy/main libc6-i386 amd64 2.17-93ubuntu4 [4.140 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ saucy-updates/main lib32gcc1 amd64 1:4.8.1-10ubuntu9 [53,5 kB]                                             
Get:3 http://de.archive.ubuntu.com/ubuntu/ saucy/restricted fglrx amd64 2:13.101-0ubuntu3 [82,3 MB]                                                   
Get:4 http://de.archive.ubuntu.com/ubuntu/ saucy/restricted fglrx-amdcccle amd64 2:13.101-0ubuntu3 [5.964 kB]                                         
Fetched 92,4 MB in 2min 26s (632 kB/s)                                                                                                                
Selecting previously unselected package libc6-i386.
(Reading database ... 193629 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.17-93ubuntu4_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.8.1-10ubuntu9_amd64.deb) ...
Selecting previously unselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a13.101-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a13.101-0ubuntu3_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libc6-i386 (2.17-93ubuntu4) ...
Setting up lib32gcc1 (1:4.8.1-10ubuntu9) ...
Setting up fglrx (2:13.101-0ubuntu3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-13.101 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-15-generic
Building for architecture x86_64
Building initial module for 3.11.0-15-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-15-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:13.101-0ubuntu3) ...
Processing triggers for libc-bin ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
arthur@Nostromo:~$ sudo amdconfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
arthur@Nostromo:~$ 


```

Here is the created xorg.conf
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

4. Reboot

5. First I saw just a purple screen. 
Then a TTY was popping up but just for a second. 
Then there was just a black screen. CTRL + ALT+F2 and any other F Key weren't getting me to a TTY.
CTRL+ALT+Print+REISUB was working.
Here is the Xorg.0.log
```
[    22.597] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    22.597] X Protocol Version 11, Revision 0
[    22.597] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    22.597] Current Operating System: Linux Nostromo 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64
[    22.597] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=842d1e61-0898-4812-a1cb-0b0ff53acac6 ro quiet splash vt.handoff=7
[    22.597] Build Date: 17 December 2013  10:06:15AM
[    22.597] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    22.597] Current version of pixman: 0.30.2
[    22.597]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.597] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.597] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 14 21:46:22 2014
[    22.607] (==) Using config file: "/etc/X11/xorg.conf"
[    22.607] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.655] (==) ServerLayout "aticonfig Layout"
[    22.655] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    22.655] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    22.656] (**) |   |-->Device "aticonfig-Device[0]-0"
[    22.656] (==) Automatically adding devices
[    22.656] (==) Automatically enabling devices
[    22.656] (==) Automatically adding GPU devices
[    22.710] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.710]     Entry deleted from font path.
[    22.710] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.710]     Entry deleted from font path.
[    22.710] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.710]     Entry deleted from font path.
[    22.710] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.710]     Entry deleted from font path.
[    22.710] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.710]     Entry deleted from font path.
[    22.710] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.710] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.710] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.710] (II) Loader magic: 0x7f1197319d20
[    22.710] (II) Module ABI versions:
[    22.710]     X.Org ANSI C Emulation: 0.4
[    22.710]     X.Org Video Driver: 14.1
[    22.710]     X.Org XInput driver : 19.1
[    22.710]     X.Org Server Extension : 7.0
[    22.712] (--) PCI:*(0:1:0:0) 1002:68c1:1025:035c rev 0, Mem @ 0xc0000000/134217728, 0xcc000000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    22.712] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.712] Initializing built-in extension Generic Event Extension
[    22.712] Initializing built-in extension SHAPE
[    22.712] Initializing built-in extension MIT-SHM
[    22.712] Initializing built-in extension XInputExtension
[    22.712] Initializing built-in extension XTEST
[    22.712] Initializing built-in extension BIG-REQUESTS
[    22.712] Initializing built-in extension SYNC
[    22.712] Initializing built-in extension XKEYBOARD
[    22.712] Initializing built-in extension XC-MISC
[    22.712] Initializing built-in extension SECURITY
[    22.712] Initializing built-in extension XINERAMA
[    22.712] Initializing built-in extension XFIXES
[    22.712] Initializing built-in extension RENDER
[    22.712] Initializing built-in extension RANDR
[    22.712] Initializing built-in extension COMPOSITE
[    22.712] Initializing built-in extension DAMAGE
[    22.712] Initializing built-in extension MIT-SCREEN-SAVER
[    22.712] Initializing built-in extension DOUBLE-BUFFER
[    22.712] Initializing built-in extension RECORD
[    22.712] Initializing built-in extension DPMS
[    22.712] Initializing built-in extension X-Resource
[    22.712] Initializing built-in extension XVideo
[    22.712] Initializing built-in extension XVideo-MotionCompensation
[    22.712] Initializing built-in extension SELinux
[    22.712] Initializing built-in extension XFree86-VidModeExtension
[    22.712] Initializing built-in extension XFree86-DGA
[    22.712] Initializing built-in extension XFree86-DRI
[    22.712] Initializing built-in extension DRI2
[    22.712] (II) "glx" will be loaded by default.
[    22.712] (WW) "xmir" is not to be loaded by default. Skipping.
[    22.712] (II) LoadModule: "glx"
[    22.746] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    22.787] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    22.787]     compiled for 6.9.0, module version = 1.0.0
[    22.787] Loading extension GLX
[    22.787] (II) LoadModule: "fglrx"
[    22.788] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    23.040] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    23.040]     compiled for 1.4.99.906, module version = 13.10.10
[    23.040]     Module class: X.Org Video Driver
[    23.040] (II) Loading sub module "fglrxdrm"
[    23.040] (II) LoadModule: "fglrxdrm"
[    23.040] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    23.103] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.103]     compiled for 1.4.99.906, module version = 13.10.10
[    23.103] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[    23.103] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[    23.103] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[    23.103] (++) using VT number 7

[    23.106] (WW) Falling back to old probe method for fglrx
[    23.157] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    23.160] ukiDynamicMajor: found major device number 250
[    23.160] ukiDynamicMajor: found major device number 250
[    23.160] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.160] ukiOpenDevice: node name is /dev/ati/card0
[    23.160] ukiOpenDevice: open result is 10, (OK)
[    23.379] ukiOpenDevice: open result is 10, (OK)
[    23.379] ukiOpenByBusid: ukiOpenMinor returns 10
[    23.379] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.400] (--) Chipset Supported AMD Graphics Processor (0x68C1) found
[    23.416] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    23.418] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    23.418] (II) AMD Video driver is signed
[    23.419] (II) fglrx(0): pEnt->device->identifier=0x7f11983052e0
[    23.419] (II) fglrx(0): === [xdl_xs114_atiddxPreInit] === begin
[    23.419] (II) Loading sub module "vgahw"
[    23.419] (II) LoadModule: "vgahw"
[    23.485] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    23.533] (II) Module vgahw: vendor="X.Org Foundation"
[    23.533]     compiled for 1.14.5, module version = 0.1.0
[    23.533]     ABI class: X.Org Video Driver, version 14.1
[    23.533] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    23.533] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.533] (==) fglrx(0): Default visual is TrueColor
[    23.533] (**) fglrx(0): Option "DPMS" "true"
[    23.533] (==) fglrx(0): RGB weight 888
[    23.533] (II) fglrx(0): Using 8 bits per RGB 
[    23.533] (==) fglrx(0): Buffer Tiling is ON
[    23.533] (II) Loading sub module "fglrxdrm"
[    23.533] (II) LoadModule: "fglrxdrm"
[    23.533] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    23.533] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.533]     compiled for 1.4.99.906, module version = 13.10.10
[    23.535] ukiDynamicMajor: found major device number 250
[    23.535] ukiDynamicMajor: found major device number 250
[    23.535] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.535] ukiOpenDevice: node name is /dev/ati/card0
[    23.535] ukiOpenDevice: open result is 13, (OK)
[    23.535] ukiOpenByBusid: ukiOpenMinor returns 13
[    23.535] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.535] (**) fglrx(0): NoAccel = NO
[    23.535] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    23.535] (--) fglrx(0): Chipset: "AMD Radeon HD 6500M/5600/5700 Series" (Chipset = 0x68c1)
[    23.535] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x035c)
[    23.535] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    23.535] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    23.535] (--) fglrx(0): MMIO registers at 0xcc000000
[    23.535] (--) fglrx(0): I/O port at 0x00003000
[    23.535] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    23.568] (II) fglrx(0): AC Adapter is used
[    23.608] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    23.610] (II) Loading sub module "vbe"
[    23.610] (II) LoadModule: "vbe"
[    23.610] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    23.611] (II) Module vbe: vendor="X.Org Foundation"
[    23.611]     compiled for 1.14.5, module version = 1.1.0
[    23.611]     ABI class: X.Org Video Driver, version 14.1
[    23.612] (II) fglrx(0): VESA BIOS detected
[    23.612] (II) fglrx(0): VESA VBE Version 3.0
[    23.612] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    23.612] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    23.612] (II) fglrx(0): VESA VBE OEM Software Rev: 12.20
[    23.612] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    23.612] (II) fglrx(0): VESA VBE OEM Product: MADISON
[    23.612] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    23.612] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    23.612] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    23.612] (II) fglrx(0): PCIE card detected
[    23.612] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    23.612] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    23.612] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    23.612] (II) fglrx(0): RandR 1.2 support is enabled!
[    23.612] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    23.612] (==) fglrx(0): Center Mode is disabled 
[    23.612] (II) Loading sub module "fb"
[    23.612] (II) LoadModule: "fb"
[    23.612] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.689] (II) Module fb: vendor="X.Org Foundation"
[    23.690]     compiled for 1.14.5, module version = 1.0.0
[    23.690]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.690] (II) Loading sub module "ddc"
[    23.690] (II) LoadModule: "ddc"
[    23.690] (II) Module "ddc" already built-in
[    23.925] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    23.925] (II) fglrx(0): Output DFP1 has no monitor section
[    23.925] (II) fglrx(0): Output CRT1 has no monitor section
[    23.925] (II) Loading sub module "ddc"
[    23.925] (II) LoadModule: "ddc"
[    23.925] (II) Module "ddc" already built-in
[    23.925] (II) fglrx(0): Connected Display0: LVDS
[    23.925] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    23.925] (II) fglrx(0): EDID for output LVDS
[    23.925] (II) fglrx(0): Manufacturer: AUO  Model: 40ec  Serial#: 1
[    23.925] (II) fglrx(0): Year: 2009  Week: 1
[    23.925] (II) fglrx(0): EDID Version: 1.3
[    23.925] (II) fglrx(0): Digital Display Input
[    23.925] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    23.925] (II) fglrx(0): Gamma: 2.20
[    23.925] (II) fglrx(0): No DPMS capabilities specified
[    23.925] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.925] (II) fglrx(0): First detailed timing is preferred mode
[    23.925] (II) fglrx(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    23.925] (II) fglrx(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    23.925] (II) fglrx(0): Manufacturer's mask: 0
[    23.925] (II) fglrx(0): Supported detailed timing:
[    23.925] (II) fglrx(0): clock: 71.9 MHz   Image Size:  344 x 193 mm
[    23.925] (II) fglrx(0): h_active: 1366  h_sync: 1374  h_sync_end 1384 h_blank_end 1544 h_border: 0
[    23.925] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 772 v_blanking: 776 v_border: 0
[    23.925] (II) fglrx(0): Unknown vendor-specific block f
[    23.925] (II) fglrx(0):  AUO
[    23.925] (II) fglrx(0):  B156XW04 V0
[    23.925] (II) fglrx(0): EDID (in hex):
[    23.925] (II) fglrx(0):     00ffffffffffff0006afec4001000000
[    23.925] (II) fglrx(0):     01130103802213780ad7759355558d29
[    23.925] (II) fglrx(0):     24505400000001010101010101010101
[    23.925] (II) fglrx(0):     010101010101151c56b250000830080a
[    23.925] (II) fglrx(0):     310058c1100000180000000f00000000
[    23.925] (II) fglrx(0):     00000000000000000020000000fe0041
[    23.925] (II) fglrx(0):     554f0a202020202020202020000000fe
[    23.925] (II) fglrx(0):     004231353658573034205630200a007e
[    23.925] (II) fglrx(0): EDID vendor "AUO", prod id 16620
[    23.925] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.925] (II) fglrx(0): Modeline "1366x768"x0.0   71.89  1366 1374 1384 1544  768 771 772 776 -hsync -vsync (46.6 kHz eP)
[    23.926] (II) fglrx(0): Printing probed modes for output LVDS
[    23.926] (II) fglrx(0): Modeline "1366x768"x60.0   71.89  1366 1374 1384 1544  768 771 772 776 -hsync -vsync (46.6 kHz eP)
[    23.926] (II) fglrx(0): Modeline "1360x768"x60.0   71.89  1360 1374 1384 1544  768 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "1280x768"x60.0   71.89  1280 1374 1384 1544  768 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "1280x720"x60.0   71.89  1280 1374 1384 1544  720 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "1024x768"x60.0   71.89  1024 1374 1384 1544  768 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "1024x600"x60.0   71.89  1024 1374 1384 1544  600 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "800x600"x60.0   71.89  800 1374 1384 1544  600 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "800x480"x60.0   71.89  800 1374 1384 1544  480 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): Modeline "640x480"x60.0   71.89  640 1374 1384 1544  480 771 772 776 -hsync -vsync (46.6 kHz e)
[    23.926] (II) fglrx(0): EDID for output DFP1
[    23.926] (II) fglrx(0): EDID for output CRT1
[    23.926] (II) fglrx(0): Output LVDS connected
[    23.926] (II) fglrx(0): Output DFP1 disconnected
[    23.926] (II) fglrx(0): Output CRT1 disconnected
[    23.926] (II) fglrx(0): Using exact sizes for initial modes
[    23.926] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    23.926] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.926] (II) fglrx(0): Display dimensions: (340, 190) mm
[    23.926] (II) fglrx(0): DPI set to (102, 102)
[    23.926] (II) fglrx(0): Eyefinity capable adapter detected.
[    23.926] (II) fglrx(0): Adapter AMD Radeon HD 6500M/5600/5700 Series has 6 configurable heads and 1 displays connected.
[    23.926] (==) fglrx(0):  PseudoColor visuals disabled
[    23.926] (II) Loading sub module "ramdac"
[    23.926] (II) LoadModule: "ramdac"
[    23.926] (II) Module "ramdac" already built-in
[    23.926] (==) fglrx(0): NoDRI = NO
[    23.926] (==) fglrx(0): Capabilities: 0x00000000
[    23.926] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    23.926] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    23.926] (==) fglrx(0): UseFastTLS=0
[    23.926] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    23.926] (--) Depth 24 pixmap format is 32 bpp
[    23.927] Loading extension ATIFGLRXDRI
[    23.927] (II) fglrx(0): doing swlDriScreenInit
[    23.927] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    23.928] ukiDynamicMajor: found major device number 250
[    23.928] ukiDynamicMajor: found major device number 250
[    23.928] ukiDynamicMajor: found major device number 250
[    23.928] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.928] ukiOpenDevice: node name is /dev/ati/card0
[    23.928] ukiOpenDevice: open result is 14, (OK)
[    23.928] ukiOpenByBusid: ukiOpenMinor returns 14
[    23.928] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.928] (II) fglrx(0): [uki] DRM interface version 1.0
[    23.928] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    23.928] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    23.928] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f1196edc000
[    23.928] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    23.928] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    23.928] (II) fglrx(0): swlDriScreenInit done
[    23.928] (II) fglrx(0): Kernel Module Version Information:
[    23.928] (II) fglrx(0):     Name: fglrx
[    23.928] (II) fglrx(0):     Version: 13.10.10
[    23.928] (II) fglrx(0):     Date: May 23 2013
[    23.928] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    23.928] (II) fglrx(0): Kernel Module version matches driver.
[    23.928] (II) fglrx(0): Kernel Module Build Time Information:
[    23.928] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.11.0-15-generic
[    23.928] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    23.928] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    23.928] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    23.928] (II) fglrx(0): [uki] register handle = 0x00004000
[    23.928] (EE) fglrx(0): Failed to open CMMQS connection.
[    23.928] (EE) 
[    23.928] (EE) Backtrace:
[    23.964] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7f1197098fdd]
[    23.964] (EE) 1: /usr/bin/X (0x7f1196ef6000+0x1a6d49) [0x7f119709cd49]
[    23.964] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f1195ff6000+0xfbb0) [0x7f1196005bb0]
[    23.964] (EE) 3: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDrmFreeSurfaces+0x42) [0x7f1192ee5ef2]
[    23.964] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs114_atiddxDriCloseScreen+0x14d) [0x7f1192ead72d]
[    23.964] (EE) 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs114_atiddxDriScreenInit+0x8e7) [0x7f1192eacdd7]
[    23.964] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs114_atiddxScreenInit+0xe31) [0x7f1192ea6ae1]
[    23.964] (EE) 7: /usr/bin/X (AddScreen+0x71) [0x7f1196f4b4d1]
[    23.964] (EE) 8: /usr/bin/X (InitOutput+0x3f8) [0x7f1196f8bd88]
[    23.964] (EE) 9: /usr/bin/X (0x7f1196ef6000+0x445cb) [0x7f1196f3a5cb]
[    23.964] (EE) 10: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f1194c31de5]
[    23.964] (EE) 11: /usr/bin/X (0x7f1196ef6000+0x44aff) [0x7f1196f3aaff]
[    23.964] (EE) 
[    23.964] (EE) Segmentation fault at address 0x890
[    23.964] (EE) 
Fatal server error:
[    23.964] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    23.964] (EE) 
[    23.964] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    23.964] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    23.964] (EE) 

```

6. Then I ran 2 commands (instructed from the guy in the older thread) to get some info about the system, but I had to boot into text mode because obviously I can't boot and then login via TTY (replaced "quite splash" with "text" in grub):

sudo lshw -C display:
```
output from "sudo lshw -C display" 
  *-display
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:c0000000-c7ffffff memory:cc000000-cc01ffff ioport:3000(size=256) memory:cc040000-cc05ffff
```

lspci -nnk | grep -iA3 vga
```
output of "lspci -nnk | grep -iA3 vga"
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]
    Subsystem: Acer Incorporated [ALI] Mobility Radeon HD 5650 [1025:035c]
    Kernel driver in use: fglrx_pci
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series] [1002:aa60]
```

---

### Post by slooksterpsv on 2014-01-17
[http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86&rev=13.1](http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86&rev=13.1)

AMD stopped support for drivers past 13.1 13.1 is the last driver support from AMD for the Mobility radeon 5600 series

---

### Post by a2r on 2014-01-17
[http://support.amd.com/en-us/kb-articles/Pages/amdcatalyst13-12linreleasenotes.aspx](http://support.amd.com/en-us/kb-articles/Pages/amdcatalyst13-12linreleasenotes.aspx) 
This are the release notes of 13.12 and if you scroll down it says **"****ATI Mobility Radeon&#8482; HD 5000 Series"** in **"**[B]AMD Mobility Product Family Compatibility".

[/B]So the release notes say the card IS supported.

Also, there is no downloadable file on the site your link refers to.

---

### Post by slooksterpsv on 2014-01-17
it does state that only 12.04.02 and 13.04 are supported, no support for 13.10 - might need to wait til April when 14.04 comes out then another few months for AMD to hopefully have support for it.

---

### Post by 95kreaninw95 on 2014-02-04
This is a bug. And it doesn't seem to fix anytime soon...
[COLOR=#000000][FONT=Verdana]
[http://ati.cchtml.com/show_bug.cgi?id=831](http://ati.cchtml.com/show_bug.cgi?id=831)

I think if I want to use Ubuntu 14.04 when it came out, the only option for me is open source driver. I hope there will be no heating issue which drive me to proprietary driver like when I tried it in 12.04.[/FONT][/COLOR]

---

### Post by jp734 on 2014-02-04
I have Lubuntu 13.10 installed on my pc and installed fglrx using synaptic package manager. Works like a charm. I can also remember using the driver from AMD website as well and it worked. Driver downloaded from AMD was **amd-driver-installer-catalyst-13-4-x86.x86_64.zip** and still have a copy of it.

---

### Post by 95kreaninw95 on 2014-02-04
> **jp734 said:**
> I have Lubuntu 13.10 installed on my pc and installed fglrx using synaptic package manager. Works like a charm. I can also remember using the driver from AMD website as well and it worked. Driver downloaded from AMD was **amd-driver-installer-catalyst-13-4-x86.x86_64.zip** and still have a copy of it.

Are you using Mobility Radeon HD 5000 series?

---

### Post by jp734 on 2014-02-04
This is what lspci gives me. I am using two video cards for my triple monitor setup. As you can see the different BusId for each device

**lspci result:**
[COLOR="#0000FF"]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series][/COLOR]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
[COLOR="#0000FF"]04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]
04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series][/COLOR]

**uname -r**
[COLOR="#0000FF"]3.11.0-15-generic[/COLOR]

---

### Post by kyselejsyrecek on 2014-02-18
I have the same problem with my Acer Aspire 8943G and AMD Mobility Radeon HD 5850 sometime from 12.11 if I remember correctly. The last working Ubuntu version with fglrx I was able to install was Ubuntu GNOME 13.04 with fglrx-updates from repository (plain fglrx from repository, nor any version from the official AMD website, did not work - it hangs the PC before login screen appears). The same happens with all newer Ubuntu and fglrx versions including Ubuntu 14.04, its fglrx versions from repository and the latest fglrx version 14.1 beta 1 from AMD website. The drivers in 13.04 are buggy, though (virtual TTY shows only blank screen and GNOME 3 often hangs - I have no idea if this is related to GNOME or fglrx but I suspect the latter is the cause).

I have only seen the "fglrx(0): Failed to open CMMQS connection." error in xorg.filesafe.log from Ubuntu 14.04 made from recovery mode when I was trying to run X at least in failsafe mode with fglrx installed (unsuccessfully, did freeze as usual). Normal xorg log files list absolutely no error, only a bunch of NULL values at the end (probably the buffers weren't flushed properly and the error entry would normally be there). ALT+SysRq+REISUB is absolutely worthless here.

After how many, 15 months? you are the first person experiencing exactly the same issue as I do. It makes me sad noone has a solusion yet or even cares.

Having Core i5 inside my laptop, I have an Intel+AMD combo too. However, the integrated GPU is disabled all the time (VGA set to Discrete in BIOS) as it only caused problems and worked never since I bought the computer in 2011. It would make things a lot easier if the power consumption was lower (during courses at university or travels home) and the fact that the fglrx driver worked never since I got the laptop makes me totally bored and yes, I'm sick of it even more now. As an IT student I can't imagine working in a company that successful, not being able to produce ONE SINGLE working driver ever since 2008 when only I experienced no fglrx bugs at all with my ATI Radeon HD 2400 AGP. What a shame...

---

