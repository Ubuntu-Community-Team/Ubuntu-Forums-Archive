---
title: "LightDM won't start after Grub - Cannot Access TTY unless closing and re-opening lid"
date: 2014-09-27
forum: Hardware
---

### Post by ceegee on 2014-09-27
I am running Ubuntu 14.04 on an hp envy 17 3D. New installation + ATI Drivers
I have a AMD Radeon HD 7800M Series  Graphics Card.

I would appreciate some help troubleshooting what I thin is a LightDM issue which I have not been able to solve.
 

When I boot the computer after selecting Ubuntu at grub - the laptop  seems to go through the regular boot process. The screen will flicker a  second and I will hear the login screen prompt, but the login screen  will not appear. 

  Attempting to switch to TTY mode will make the screen flicker again. I  am able to run commands - but i cannot see the terminal. I have  successfully rebooted, and attempted to start lightdm this way, but  after running:
  sudo service lightDM restart
  It shows me the desktop background and cursor and just hangs.
  I am able to still use the computer, if when I hear the login prompt,  I close the lid to tell it to go to sleep, and then turn it back on.  LightDM login shows up and I can use the computer normally. 
  Does this correctly seem like a lightdm issue? or is this xorg? What logs should I be looking at to troubleshoot if I can only do so  after putting the computer to sleep before logging in? What should I be  looking for in those logs based on the issue above?

Since the laptop works fine with the ATI driver with the workaround above - I wonder if there is a way to find out what is fixing it with the sleep cycle and how I can replicate that automatically at boot?


  Thanks!

---

### Post by ceegee on 2014-09-27
[Update]
If I attempt to logout, the same issue happens. I hear the Ubuntu login screen chime, but cannot see the login screen or switch to a TTY or login by typing. I can though shutdown by pressing the power button then enter. 

I followed this bug to see if it applied, adding a sleep to start of lightdm and telling it to wait for udev, while this has prolonged the time it takes to hear the chime, it has not made the login screen appear. 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410)

---

### Post by ceegee on 2014-09-27
I have also verified that my /etc/X11/default-display-manager has the correct line /usr/sbin/lightdm

---

### Post by ceegee on 2014-09-28
I figured I could update with the latest.

I started by looking through the x logs and a couple errors. in  /var/log/Xorg.0.log

I had 
[    10.550] (EE) open /dev/dri/card0: No such file or directory
[    10.769] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    10.769] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    10.769] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]

and some others I cannot find. 
Following these two posts helped clear those errors up, but alas - still have the same problem
[http://askubuntu.com/questions/465243/how-to-use-fglrx-proprietary-driver-for-dual-ati-radeon-hd-5670-crossfirex-in-ub](http://askubuntu.com/questions/465243/how-to-use-fglrx-proprietary-driver-for-dual-ati-radeon-hd-5670-crossfirex-in-ub)
[http://askubuntu.com/questions/94272/ati-driver-issue-fglrxinfo-returning-null-display-error-xorg-conf-file-looks-f/175677#175677](http://askubuntu.com/questions/94272/ati-driver-issue-fglrxinfo-returning-null-display-error-xorg-conf-file-looks-f/175677#175677)

I also followed the instructions here for some troubleshooting to remove all errors
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)


LightDM has some pretty gnarly errors that don't show up on Google else. 

I  am adding logs and settings files that I think should be pointing me to  how to fix this, I am just not there yet and would appreciate some help


=================
Output of fglrxinfo
```

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7800M Series 
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005

```
=================
Output of /etc/X11/xorg.conf
------------------
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

Section "Files"
        ModulePath "/usr/lib/fglrx"
        ModulePath "/usr/lib/xorg/modules"
        ModulePath "/usr/lib/dri/"
EndSection
```


==============================
Output of /var/log/Xorg.0.log
-----------------
```

[    12.926] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    12.926] X Protocol Version 11, Revision 0
[    12.926] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    12.926] Current Operating System: Linux Ulster 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64
[     12.926] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic  root=UUID=8c084118-427f-4a4e-89f2-bb32977d993d ro persistent splash  nomodeset
[    12.926] Build Date: 30 July 2014  12:21:54AM
[    12.926] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    12.926] Current version of pixman: 0.30.2
[    12.926]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.926] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.927] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 28 00:47:48 2014
[    12.927] (==) Using config file: "/etc/X11/xorg.conf"
[    12.927] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.928] (==) ServerLayout "aticonfig Layout"
[    12.928] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    12.928] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    12.928] (**) |   |-->Device "aticonfig-Device[0]-0"
[    12.928] (==) Automatically adding devices
[    12.928] (==) Automatically enabling devices
[    12.928] (==) Automatically adding GPU devices
[    12.928] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.928]     Entry deleted from font path.
[    12.928] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.928]     Entry deleted from font path.
[    12.928] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.928]     Entry deleted from font path.
[    12.928] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.928]     Entry deleted from font path.
[    12.928] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.928]     Entry deleted from font path.
[    12.928] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    12.928] (**) ModulePath set to "/usr/lib/fglrx,/usr/lib/xorg/modules,/usr/lib/dri/"
[    12.928] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.928] (II) Loader magic: 0x7f39ccf2dd40
[    12.928] (II) Module ABI versions:
[    12.928]     X.Org ANSI C Emulation: 0.4
[    12.928]     X.Org Video Driver: 15.0
[    12.928]     X.Org XInput driver : 20.0
[    12.928]     X.Org Server Extension : 8.0
[     12.930] (--) PCI:*(0:1:0:0) 1002:6827:103c:1852 rev 0, Mem @  0xb0000000/268435456, 0xc2000000/262144, I/O @ 0x00004000/256, BIOS @  0x????????/131072
[    12.930] Initializing built-in extension Generic Event Extension
[    12.930] Initializing built-in extension SHAPE
[    12.930] Initializing built-in extension MIT-SHM
[    12.930] Initializing built-in extension XInputExtension
[    12.930] Initializing built-in extension XTEST
[    12.930] Initializing built-in extension BIG-REQUESTS
[    12.930] Initializing built-in extension SYNC
[    12.931] Initializing built-in extension XKEYBOARD
[    12.931] Initializing built-in extension XC-MISC
[    12.931] Initializing built-in extension SECURITY
[    12.931] Initializing built-in extension XINERAMA
[    12.931] Initializing built-in extension XFIXES
[    12.931] Initializing built-in extension RENDER
[    12.931] Initializing built-in extension RANDR
[    12.931] Initializing built-in extension COMPOSITE
[    12.931] Initializing built-in extension DAMAGE
[    12.931] Initializing built-in extension MIT-SCREEN-SAVER
[    12.931] Initializing built-in extension DOUBLE-BUFFER
[    12.931] Initializing built-in extension RECORD
[    12.931] Initializing built-in extension DPMS
[    12.931] Initializing built-in extension Present
[    12.931] Initializing built-in extension DRI3
[    12.931] Initializing built-in extension X-Resource
[    12.931] Initializing built-in extension XVideo
[    12.931] Initializing built-in extension XVideo-MotionCompensation
[    12.931] Initializing built-in extension SELinux
[    12.931] Initializing built-in extension XFree86-VidModeExtension
[    12.931] Initializing built-in extension XFree86-DGA
[    12.931] Initializing built-in extension XFree86-DRI
[    12.931] Initializing built-in extension DRI2
[    12.931] (II) "glx" will be loaded by default.
[    12.931] (WW) "xmir" is not to be loaded by default. Skipping.
[    12.931] (II) LoadModule: "glx"
[    12.944] (II) Loading /usr/lib/fglrx/xorg/modules/extensions/libglx.so
[    12.944] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    12.944]     compiled for 6.9.0, module version = 1.0.0
[    12.945] Loading extension GLX
[    12.945] (II) LoadModule: "fglrx"
[    12.945] (II) Loading /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
[    12.984] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    12.984]     compiled for 1.4.99.906, module version = 13.35.5
[    12.984]     Module class: X.Org Video Driver
[    12.984] (II) Loading sub module "fglrxdrm"
[    12.984] (II) LoadModule: "fglrxdrm"
[    12.985] (II) Loading /usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
[    12.986] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.986]     compiled for 1.4.99.906, module version = 13.35.5
[    12.986] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
[    12.986] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
[    12.986] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
[    12.986] (++) using VT number 7

[    12.989] (WW) Falling back to old probe method for fglrx
[    13.001] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    13.014] ukiDynamicMajor: found major device number 250
[    13.014] ukiDynamicMajor: found major device number 250
[    13.014] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.014] ukiOpenDevice: node name is /dev/ati/card0
[    13.014] ukiOpenDevice: open result is 9, (OK)
[    13.592] ukiOpenByBusid: ukiOpenMinor returns 9
[    13.592] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.596] (--) Chipset Supported AMD Graphics Processor (0x6827) found
[    13.596] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    13.597] (II) fglrx(0): pEnt->device->identifier=0x7f39cd19f3d0
[    13.597] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    13.597] (II) Loading sub module "vgahw"
[    13.597] (II) LoadModule: "vgahw"
[    13.600] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.600] (II) Module vgahw: vendor="X.Org Foundation"
[    13.600]     compiled for 1.15.1, module version = 0.1.0
[    13.600]     ABI class: X.Org Video Driver, version 15.0
[    13.601] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    13.601] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    13.601] (==) fglrx(0): Default visual is TrueColor
[    13.601] (**) fglrx(0): Option "DPMS" "true"
[    13.601] (==) fglrx(0): RGB weight 888
[    13.601] (II) fglrx(0): Using 8 bits per RGB 
[    13.601] (==) fglrx(0): Buffer Tiling is ON
[    13.601] (II) Loading sub module "fglrxdrm"
[    13.601] (II) LoadModule: "fglrxdrm"
[    13.602] (II) Loading /usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
[    13.602] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    13.602]     compiled for 1.4.99.906, module version = 13.35.5
[    13.614] ukiDynamicMajor: found major device number 250
[    13.615] ukiDynamicMajor: found major device number 250
[    13.615] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.615] ukiOpenDevice: node name is /dev/ati/card0
[    13.615] ukiOpenDevice: open result is 11, (OK)
[    13.615] ukiOpenByBusid: ukiOpenMinor returns 11
[    13.615] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.615] (**) fglrx(0): NoAccel = NO
[    13.615] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    13.615] (--) fglrx(0): Chipset: "AMD Radeon HD 7800M Series " (Chipset = 0x6827)
[    13.615] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1852)
[    13.615] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    13.615] (--) fglrx(0): Linear framebuffer (phys) at 0xb0000000
[    13.615] (--) fglrx(0): MMIO registers at 0xc2000000
[    13.615] (--) fglrx(0): I/O port at 0x00004000
[    13.615] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.616] (II) fglrx(0): ATIF platform detected
[    13.617] (II) fglrx(0): Battery is used
[    13.617] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    13.690] (II) Loading sub module "vbe"
[    13.691] (II) LoadModule: "vbe"
[    13.691] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.691] (II) Module vbe: vendor="X.Org Foundation"
[    13.691]     compiled for 1.15.1, module version = 1.1.0
[    13.691]     ABI class: X.Org Video Driver, version 15.0
[    13.692] (II) fglrx(0): VESA BIOS detected
[    13.692] (II) fglrx(0): VESA VBE Version 3.0
[    13.692] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    13.692] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    13.692] (II) fglrx(0): VESA VBE OEM Software Rev: 15.21
[    13.692] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[    13.692] (II) fglrx(0): VESA VBE OEM Product: HEATHROW
[    13.692] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.692] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    13.692] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    13.692] (II) fglrx(0): PCIE card detected
[    13.692] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.692] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.692] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[    13.692] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.692] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.692] (II) Loading sub module "fb"
[    13.692] (II) LoadModule: "fb"
[    13.693] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.693] (II) Module fb: vendor="X.Org Foundation"
[    13.693]     compiled for 1.15.1, module version = 1.0.0
[    13.693]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.693] (II) fglrx(0): EDID Management option: EDID Management is enabled
[    13.693] (II) Loading sub module "ddc"
[    13.693] (II) LoadModule: "ddc"
[    13.693] (II) Module "ddc" already built-in
[    13.787] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    13.787] (II) fglrx(0): Output DFP1 has no monitor section
[    13.787] (II) fglrx(0): Output DFP2 has no monitor section
[    13.787] (II) fglrx(0): Output DFP3 has no monitor section
[    13.787] (II) fglrx(0): Output DFP4 has no monitor section
[    13.787] (II) fglrx(0): Output DFP5 has no monitor section
[    13.787] (II) fglrx(0): Output DFP6 has no monitor section
[    13.787] (II) fglrx(0): Output DFP7 has no monitor section
[    13.788] (II) fglrx(0): Output DFP8 has no monitor section
[    13.788] (II) fglrx(0): Output DFP9 has no monitor section
[    13.788] (II) Loading sub module "ddc"
[    13.788] (II) LoadModule: "ddc"
[    13.788] (II) Module "ddc" already built-in
[    13.788] (II) fglrx(0): Connected Display0: LVDS
[    13.788] (II) fglrx(0): Display0 EDID data ---------------------------
[    13.788] (II) fglrx(0): Manufacturer: LGD  Model: 2c4  Serial#: 0
[    13.788] (II) fglrx(0): Year: 2011  Week: 0
[    13.788] (II) fglrx(0): EDID Version: 1.4
[    13.788] (II) fglrx(0): Digital Display Input
[    13.788] (II) fglrx(0): 6 bits per channel
[    13.788] (II) fglrx(0): Digital interface is DisplayPort
[    13.788] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    13.788] (II) fglrx(0): Gamma: 2.20
[    13.788] (II) fglrx(0): No DPMS capabilities specified
[    13.788] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[    13.788] (II) fglrx(0): First detailed timing is preferred mode
[    13.788] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[    13.788] (II) fglrx(0): redX: 0.642 redY: 0.345   greenX: 0.339 greenY: 0.620
[    13.788] (II) fglrx(0): blueX: 0.148 blueY: 0.062   whiteX: 0.313 whiteY: 0.329
[    13.788] (II) fglrx(0): Manufacturer's mask: 0
[    13.788] (II) fglrx(0): Supported detailed timing:
[    13.788] (II) fglrx(0): clock: 148.5 MHz   Image Size:  382 x 215 mm
[    13.788] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    13.788] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    13.788] (II) fglrx(0): Supported detailed timing:
[    13.788] (II) fglrx(0): clock: 392.2 MHz   Image Size:  382 x 215 mm
[    13.788] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    13.788] (II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1964 v_border: 0
[    13.788] (II) fglrx(0): Supported detailed timing:
[    13.788] (II) fglrx(0): clock: 396.4 MHz   Image Size:  382 x 215 mm
[    13.788] (II) fglrx(0): h_active: 1920  h_sync: 1940  h_sync_end 1960 h_blank_end 2080 h_border: 0
[    13.788] (II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1588 v_border: 0
[    13.788] (II) fglrx(0):  LP173WF2-TPB3
[    13.788] (II) fglrx(0): EDID (in hex):
[    13.788] (II) fglrx(0):     00ffffffffffff0030e4c40200000000
[    13.788] (II) fglrx(0):     0015010495261578025f35a458569e26
[    13.788] (II) fglrx(0):     0f505400000001010101010101010101
[    13.788] (II) fglrx(0):     010101010101023a801871382d40582c
[    13.788] (II) fglrx(0):     45007ed710000019319980a070387443
[    13.788] (II) fglrx(0):     302035007ed710000019d39a80a07038
[    13.788] (II) fglrx(0):     fc41141435007ed710000019000000fe
[    13.788] (II) fglrx(0):     004c503137335746322d545042330047
[    13.788] (II) fglrx(0): End of Display0 EDID data --------------------
[    13.788] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    13.790] (II) fglrx(0): EDID for output LVDS
[    13.790] (II) fglrx(0): Manufacturer: LGD  Model: 2c4  Serial#: 0
[    13.790] (II) fglrx(0): Year: 2011  Week: 0
[    13.790] (II) fglrx(0): EDID Version: 1.4
[    13.790] (II) fglrx(0): Digital Display Input
[    13.790] (II) fglrx(0): 6 bits per channel
[    13.790] (II) fglrx(0): Digital interface is DisplayPort
[    13.790] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    13.790] (II) fglrx(0): Gamma: 2.20
[    13.790] (II) fglrx(0): No DPMS capabilities specified
[    13.790] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[    13.790] (II) fglrx(0): First detailed timing is preferred mode
[    13.790] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[    13.790] (II) fglrx(0): redX: 0.642 redY: 0.345   greenX: 0.339 greenY: 0.620
[    13.790] (II) fglrx(0): blueX: 0.148 blueY: 0.062   whiteX: 0.313 whiteY: 0.329
[    13.790] (II) fglrx(0): Manufacturer's mask: 0
[    13.790] (II) fglrx(0): Supported detailed timing:
[    13.790] (II) fglrx(0): clock: 148.5 MHz   Image Size:  382 x 215 mm
[    13.790] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    13.790] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    13.790] (II) fglrx(0): Supported detailed timing:
[    13.790] (II) fglrx(0): clock: 392.2 MHz   Image Size:  382 x 215 mm
[    13.790] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    13.790] (II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1964 v_border: 0
[    13.790] (II) fglrx(0): Supported detailed timing:
[    13.790] (II) fglrx(0): clock: 396.4 MHz   Image Size:  382 x 215 mm
[    13.790] (II) fglrx(0): h_active: 1920  h_sync: 1940  h_sync_end 1960 h_blank_end 2080 h_border: 0
[    13.790] (II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1588 v_border: 0
[    13.790] (II) fglrx(0):  LP173WF2-TPB3
[    13.790] (II) fglrx(0): EDID (in hex):
[    13.790] (II) fglrx(0):     00ffffffffffff0030e4c40200000000
[    13.790] (II) fglrx(0):     0015010495261578025f35a458569e26
[    13.790] (II) fglrx(0):     0f505400000001010101010101010101
[    13.790] (II) fglrx(0):     010101010101023a801871382d40582c
[    13.790] (II) fglrx(0):     45007ed710000019319980a070387443
[    13.790] (II) fglrx(0):     302035007ed710000019d39a80a07038
[    13.790] (II) fglrx(0):     fc41141435007ed710000019000000fe
[    13.790] (II) fglrx(0):     004c503137335746322d545042330047
[    13.791] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    13.791] (II) fglrx(0): Printing DDC gathered Modelines:
[     13.791] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    13.791]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II) fglrx(0): Printing probed modes for output LVDS
[     13.791] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008  2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[     13.791] (II) fglrx(0): Modeline "1920x1080"x120.0  396.35  1920 1940  1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1920x1080"x96.0  392.17  1920 1968 2000  2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791]  (II) fglrx(0): Modeline "1680x1050"x60.0  148.50  1680 2008 2052 2200   1050 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1400x1050"x120.0  396.35  1400 1940 1960 2080  1050  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1400x1050"x96.0  392.17  1400 1968 2000 2080  1050  1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1400x1050"x60.0  148.50  1400 2008 2052 2200  1050  1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1600x900"x60.0  148.50  1600 2008 2052 2200  900 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x1024"x120.0  396.35  1280 1940  1960 2080  1024 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x1024"x96.0  392.17  1280 1968 2000  2080  1024 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791]  (II) fglrx(0): Modeline "1280x1024"x60.0  148.50  1280 2008 2052 2200   1024 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1440x900"x120.0  396.35  1440 1940 1960 2080  900  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II)  fglrx(0): Modeline "1440x900"x96.0  392.17  1440 1968 2000 2080  900  1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1440x900"x60.0  148.50  1440 2008 2052 2200  900 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x960"x120.0  396.35  1280 1940  1960 2080  960 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x960"x96.0  392.17  1280 1968 2000  2080  960 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1280x960"x60.0  148.50  1280 2008 2052 2200  960 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x768"x120.0  396.35  1280 1940  1960 2080  768 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x768"x96.0  392.17  1280 1968 2000  2080  768 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1280x768"x60.0  148.50  1280 2008 2052 2200  768 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x720"x120.0  396.35  1280 1940  1960 2080  720 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1280x720"x96.0  392.17  1280 1968 2000  2080  720 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1280x720"x60.0  148.50  1280 2008 2052 2200  720 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1024x768"x120.0  396.35  1024 1940  1960 2080  768 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1024x768"x96.0  392.17  1024 1968 2000  2080  768 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1024x768"x60.0  148.50  1024 2008 2052 2200  768 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     13.791] (II) fglrx(0): Modeline "1024x600"x120.0  396.35  1024 1940  1960 2080  600 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[     13.791] (II) fglrx(0): Modeline "1024x600"x96.0  392.17  1024 1968 2000  2080  600 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "1024x600"x60.0  148.50  1024 2008 2052 2200  600 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x600"x120.0  396.35  800 1940 1960 2080  600 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x600"x96.0  392.17  800 1968 2000 2080  600 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x600"x60.0  148.50  800 2008 2052 2200  600 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x480"x120.0  396.35  800 1940 1960 2080  480 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x480"x96.0  392.17  800 1968 2000 2080  480 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "800x480"x60.0  148.50  800 2008 2052 2200  480 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "640x480"x120.0  396.35  640 1940 1960 2080  480 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    13.791] (II) fglrx(0): Modeline "640x480"x96.0  392.17  640 1968 2000 2080  480 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    13.791] (II) fglrx(0): Modeline "640x480"x60.0  148.50  640 2008 2052 2200  480 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    13.791] (II) fglrx(0): EDID for output DFP1
[    13.791] (II) fglrx(0): EDID for output DFP2
[    13.791] (II) fglrx(0): EDID for output DFP3
[    13.792] (II) fglrx(0): EDID for output DFP4
[    13.792] (II) fglrx(0): EDID for output DFP5
[    13.792] (II) fglrx(0): EDID for output DFP6
[    13.792] (II) fglrx(0): EDID for output DFP7
[    13.792] (II) fglrx(0): EDID for output DFP8
[    13.792] (II) fglrx(0): EDID for output DFP9
[    13.792] (II) fglrx(0): Output LVDS connected
[    13.792] (II) fglrx(0): Output DFP1 disconnected
[    13.792] (II) fglrx(0): Output DFP2 disconnected
[    13.792] (II) fglrx(0): Output DFP3 disconnected
[    13.792] (II) fglrx(0): Output DFP4 disconnected
[    13.792] (II) fglrx(0): Output DFP5 disconnected
[    13.792] (II) fglrx(0): Output DFP6 disconnected
[    13.792] (II) fglrx(0): Output DFP7 disconnected
[    13.792] (II) fglrx(0): Output DFP8 disconnected
[    13.792] (II) fglrx(0): Output DFP9 disconnected
[    13.792] (II) fglrx(0): Using exact sizes for initial modes
[    13.792] (II) fglrx(0): Output LVDS using initial mode 1920x1080
[    13.792] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.792] (II) fglrx(0): Display dimensions: (380, 210) mm
[    13.792] (II) fglrx(0): DPI set to (128, 130)
[    13.792] (II) fglrx(0): Eyefinity capable adapter detected.
[    13.792] (II) fglrx(0): Adapter AMD Radeon HD 7800M Series  has 6 configurable heads and 1 displays connected.
[    13.792] (==) fglrx(0):  PseudoColor visuals disabled
[    13.792] (II) Loading sub module "ramdac"
[    13.792] (II) LoadModule: "ramdac"
[    13.792] (II) Module "ramdac" already built-in
[    13.792] (==) fglrx(0): NoDRI = NO
[    13.792] (==) fglrx(0): Capabilities: 0x00000000
[    13.792] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.792] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.792] (==) fglrx(0): UseFastTLS=0
[    13.792] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    13.792] (--) Depth 24 pixmap format is 32 bpp
[    13.805] Loading extension ATIFGLRXDRI
[    13.806] (II) fglrx(0): doing swlDriScreenInit
[    13.806] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    13.806] ukiDynamicMajor: found major device number 250
[    13.806] ukiDynamicMajor: found major device number 250
[    13.806] ukiDynamicMajor: found major device number 250
[    13.806] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.806] ukiOpenDevice: node name is /dev/ati/card0
[    13.806] ukiOpenDevice: open result is 12, (OK)
[    13.806] ukiOpenByBusid: ukiOpenMinor returns 12
[    13.806] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.806] (II) fglrx(0): [uki] DRM interface version 1.0
[    13.806] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    13.806] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    13.806] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f39ccaf8000
[    13.806] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    13.806] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    13.806] (II) fglrx(0): swlDriScreenInit done
[    13.806] (II) fglrx(0): Kernel Module Version Information:
[    13.806] (II) fglrx(0):     Name: fglrx
[    13.806] (II) fglrx(0):     Version: 13.35.5
[    13.806] (II) fglrx(0):     Date: Mar 12 2014
[    13.806] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    13.806] (II) fglrx(0): Kernel Module version matches driver.
[    13.806] (II) fglrx(0): Kernel Module Build Time Information:
[    13.806] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-36-generic
[    13.806] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    13.806] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    13.806] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    13.806] (II) fglrx(0): [uki] register handle = 0x00004000
[    13.807] (II) fglrx(0): DRI initialization successfull
[    13.807] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x010e0000
[    13.808] (==) fglrx(0): Backing store enabled
[    13.808] Loading extension FGLRXEXTENSION
[    13.808] (**) fglrx(0): DPMS enabled
[    13.808] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.808] (**) fglrx(0): Textured Video is enabled.
[    13.808] (II) LoadModule: "glesx"
[    13.809] (II) Loading /usr/lib/fglrx/xorg/modules/glesx.so
[    13.809] (II) Module glesx: vendor="X.Org Foundation"
[    13.809]     compiled for 1.4.99.906, module version = 1.0.0
[    13.809] Loading extension GLESX
[    13.809] (II) fglrx(0): GLESX enableFlags = 8784
[    13.809] (II) fglrx(0): GLESX is enabled
[    13.809] (II) LoadModule: "amdxmm"
[    13.810] (II) Loading /usr/lib/fglrx/xorg/modules/amdxmm.so
[    13.810] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.810]     compiled for 1.4.99.906, module version = 2.0.0
[    13.833] Loading extension AMDXVOPL
[    13.833] Loading extension AMDXVBA
[    13.834] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    13.838] (II) fglrx(0): Enable composite support successfully
[    13.838] (WW) fglrx(0): Option "VendorName" is not used
[    13.838] (WW) fglrx(0): Option "ModelName" is not used
[    13.838] (II) fglrx(0): X context handle = 0x1
[    13.838] (II) fglrx(0): [DRI] installation complete
[    13.838] (==) fglrx(0): Silken mouse enabled
[    13.838] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.839] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.839] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    15.452] (--) RandR disabled
[    15.461] (II) SELinux: Disabled on system
[    15.462] ukiDynamicMajor: found major device number 250
[    15.462] ukiDynamicMajor: found major device number 250
[    15.462] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.462] ukiOpenDevice: node name is /dev/ati/card0
[    15.462] ukiOpenDevice: open result is 13, (OK)
[    15.462] ukiOpenByBusid: ukiOpenMinor returns 13
[    15.462] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.487] ukiDynamicMajor: found major device number 250
[    15.487] ukiDynamicMajor: found major device number 250
[    15.487] ukiDynamicMajor: found major device number 250
[    15.487] ukiOpenDevice: node name is /dev/ati/card0
[    15.487] ukiOpenDevice: open result is 14, (OK)
[    15.487] ukiGetBusid returned 'PCI:1:0:0'
[    15.487] ukiOpenDevice: node name is /dev/ati/card1
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card2
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card3
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card4
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card5
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card6
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: open result is -1, (No such device)
[    15.487] ukiOpenDevice: Open failed
[    15.487] ukiOpenDevice: node name is /dev/ati/card7
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card8
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card9
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card10
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card11
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card12
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card13
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card14
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiOpenDevice: node name is /dev/ati/card15
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: open result is -1, (No such device)
[    15.488] ukiOpenDevice: Open failed
[    15.488] ukiDynamicMajor: found major device number 250
[    15.488] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.488] ukiOpenDevice: node name is /dev/ati/card0
[    15.488] ukiOpenDevice: open result is 14, (OK)
[    15.488] ukiOpenByBusid: ukiOpenMinor returns 14
[    15.488] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.558] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    15.559] ukiDynamicMajor: found major device number 250
[    15.559] ukiDynamicMajor: found major device number 250
[    15.559] ukiDynamicMajor: found major device number 250
[    15.559] ukiOpenDevice: node name is /dev/ati/card0
[    15.559] ukiOpenDevice: open result is 15, (OK)
[    15.559] ukiGetBusid returned 'PCI:1:0:0'
[    15.559] ukiOpenDevice: node name is /dev/ati/card1
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: Open failed
[    15.559] ukiOpenDevice: node name is /dev/ati/card2
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: Open failed
[    15.559] ukiOpenDevice: node name is /dev/ati/card3
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.559] ukiOpenDevice: Open failed
[    15.559] ukiOpenDevice: node name is /dev/ati/card4
[    15.559] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card5
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card6
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card7
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card8
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card9
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card10
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card11
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card12
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card13
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card14
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.560] ukiOpenDevice: Open failed
[    15.560] ukiOpenDevice: node name is /dev/ati/card15
[    15.560] ukiOpenDevice: open result is -1, (No such device)
[    15.561] ukiOpenDevice: open result is -1, (No such device)
[    15.561] ukiOpenDevice: Open failed
[    15.561] ukiDynamicMajor: found major device number 250
[    15.561] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.561] ukiOpenDevice: node name is /dev/ati/card0
[    15.561] ukiOpenDevice: open result is 15, (OK)
[    15.561] ukiOpenByBusid: ukiOpenMinor returns 15
[    15.561] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.583] (II) fglrx(0): Setting screen physical size to 508 x 285
[    15.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.599] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.599] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.599] (II) LoadModule: "evdev"
[    15.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.601] (II) Module evdev: vendor="X.Org Foundation"
[    15.601]     compiled for 1.15.0, module version = 2.8.2
[    15.601]     Module class: X.Org XInput Driver
[    15.601]     ABI class: X.Org XInput driver, version 20.0
[    15.601] (II) Using input driver 'evdev' for 'Power Button'
[    15.601] (**) Power Button: always reports core events
[    15.601] (**) evdev: Power Button: Device: "/dev/input/event2"
[    15.601] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.601] (--) evdev: Power Button: Found keys
[    15.601] (II) evdev: Power Button: Configuring as keyboard
[    15.601] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    15.601] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.601] (**) Option "xkb_rules" "evdev"
[    15.601] (**) Option "xkb_model" "pc105"
[    15.601] (**) Option "xkb_layout" "us"
[    15.602] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    15.602] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.602] (II) Using input driver 'evdev' for 'Video Bus'
[    15.602] (**) Video Bus: always reports core events
[    15.602] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    15.602] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.602] (--) evdev: Video Bus: Found keys
[    15.602] (II) evdev: Video Bus: Configuring as keyboard
[     15.602] (**) Option "config_info"  "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input8/event7"
[    15.602] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    15.602] (**) Option "xkb_rules" "evdev"
[    15.602] (**) Option "xkb_model" "pc105"
[    15.602] (**) Option "xkb_layout" "us"
[    15.603] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.603] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.603] (II) Using input driver 'evdev' for 'Power Button'
[    15.603] (**) Power Button: always reports core events
[    15.603] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.603] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.603] (--) evdev: Power Button: Found keys
[    15.603] (II) evdev: Power Button: Configuring as keyboard
[    15.603] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    15.603] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    15.603] (**) Option "xkb_rules" "evdev"
[    15.603] (**) Option "xkb_model" "pc105"
[    15.603] (**) Option "xkb_layout" "us"
[    15.604] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.604] (II) No input driver specified, ignoring this device.
[    15.604] (II) This device may have been added with another device file.
[    15.604] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    15.604] (II) No input driver specified, ignoring this device.
[    15.604] (II) This device may have been added with another device file.
[    15.604] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event11)
[    15.604] (II) No input driver specified, ignoring this device.
[    15.605] (II) This device may have been added with another device file.
[    15.605] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event10)
[    15.605] (II) No input driver specified, ignoring this device.
[    15.605] (II) This device may have been added with another device file.
[    15.605] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    15.605] (II) No input driver specified, ignoring this device.
[    15.605] (II) This device may have been added with another device file.
[    15.605] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[    15.606] (II) No input driver specified, ignoring this device.
[    15.606] (II) This device may have been added with another device file.
[    15.606] (II) config/udev: Adding input device Standard Microsystems Corp. HP Wireless Audio Adapter (/dev/input/event5)
[    15.606] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: Applying InputClass "evdev keyboard catchall"
[    15.606] (II) Using input driver 'evdev' for 'Standard Microsystems Corp. HP Wireless Audio Adapter'
[    15.606] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: always reports core events
[    15.606] (**) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Device: "/dev/input/event5"
[    15.606] (--) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Vendor 0x424 Product 0xb832
[    15.606] (--) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Found 1 mouse buttons
[    15.606] (--) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Found absolute axes
[    15.606] (II) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Forcing absolute x/y axes to exist.
[    15.606] (--) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Found keys
[    15.606] (II) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Forcing relative x/y axes to exist.
[    15.606] (II) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Configuring as mouse
[    15.606] (II) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: Configuring as keyboard
[    15.606] (**) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: YAxisMapping: buttons 4 and 5
[     15.606] (**) evdev: Standard Microsystems Corp. HP Wireless Audio  Adapter: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
[    15.606] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.3/input/input6/event5"
[     15.606] (II) XINPUT: Adding extended input device "Standard  Microsystems Corp. HP Wireless Audio Adapter" (type: KEYBOARD, id 9)
[    15.606] (**) Option "xkb_rules" "evdev"
[    15.606] (**) Option "xkb_model" "pc105"
[    15.606] (**) Option "xkb_layout" "us"
[    15.607] (II) evdev: Standard Microsystems Corp. HP Wireless Audio Adapter: initialized for absolute axes.
[    15.607] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: (accel) keeping acceleration scheme 1
[    15.607] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: (accel) acceleration profile 0
[    15.607] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: (accel) acceleration factor: 2.000
[    15.607] (**) Standard Microsystems Corp. HP Wireless Audio Adapter: (accel) acceleration threshold: 4
[    15.608] (II) config/udev: Adding input device HP TrueVision HD (/dev/input/event13)
[    15.608] (**) HP TrueVision HD: Applying InputClass "evdev keyboard catchall"
[    15.608] (II) Using input driver 'evdev' for 'HP TrueVision HD'
[    15.608] (**) HP TrueVision HD: always reports core events
[    15.608] (**) evdev: HP TrueVision HD: Device: "/dev/input/event13"
[    15.608] (--) evdev: HP TrueVision HD: Vendor 0x10f1 Product 0x1a37
[    15.608] (--) evdev: HP TrueVision HD: Found keys
[    15.608] (II) evdev: HP TrueVision HD: Configuring as keyboard
[     15.608] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input14/event13"
[    15.608] (II) XINPUT: Adding extended input device "HP TrueVision HD" (type: KEYBOARD, id 10)
[    15.608] (**) Option "xkb_rules" "evdev"
[    15.608] (**) Option "xkb_model" "pc105"
[    15.608] (**) Option "xkb_layout" "us"
[    15.609] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.609] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.609] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.609] (**) AT Translated Set 2 keyboard: always reports core events
[    15.609] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.609] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.609] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.609] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.609] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    15.609] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    15.609] (**) Option "xkb_rules" "evdev"
[    15.609] (**) Option "xkb_model" "pc105"
[    15.609] (**) Option "xkb_layout" "us"
[    15.610] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    15.610] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.610] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.610] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    15.610] (II) LoadModule: "synaptics"
[    15.610] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.610] (II) Module synaptics: vendor="X.Org Foundation"
[    15.610]     compiled for 1.15.0, module version = 1.7.4
[    15.610]     Module class: X.Org XInput Driver
[    15.610]     ABI class: X.Org XInput driver, version 20.0
[    15.610] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    15.610] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.611] (**) Option "Device" "/dev/input/event4"
[    15.636] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5662 (res 42)
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4708 (res 58)
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    15.636] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    15.636] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    15.636] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    15.648] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    15.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    15.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    15.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    15.648] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    15.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.649] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    15.649] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    15.649] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    15.650] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event14)
[    15.650] (II) No input driver specified, ignoring this device.
[    15.650] (II) This device may have been added with another device file.
[    15.650] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    15.650] (II) No input driver specified, ignoring this device.
[    15.650] (II) This device may have been added with another device file.
[    15.653] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event15)
[    15.653] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.653] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    15.653] (**) HP WMI hotkeys: always reports core events
[    15.653] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event15"
[    15.653] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    15.653] (--) evdev: HP WMI hotkeys: Found keys
[    15.653] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    15.653] (**) Option "config_info" "udev:/sys/devices/virtual/input/input15/event15"
[    15.653] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    15.653] (**) Option "xkb_rules" "evdev"
[    15.653] (**) Option "xkb_model" "pc105"
[    15.653] (**) Option "xkb_layout" "us"
[    15.654] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event6)
[    15.654] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.654] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    15.654] (**) HP Wireless hotkeys: always reports core events
[    15.654] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event6"
[    15.654] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    15.654] (--) evdev: HP Wireless hotkeys: Found keys
[    15.654] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    15.654] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event6"
[    15.654] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 14)
[    15.654] (**) Option "xkb_rules" "evdev"
[    15.654] (**) Option "xkb_model" "pc105"
[    15.654] (**) Option "xkb_layout" "us"
[    15.660] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    16.513] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    16.513] (II) fglrx(0): Printing DDC gathered Modelines:
[     16.513] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    16.513]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    16.513] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    16.893] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    16.893] (II) fglrx(0): Printing DDC gathered Modelines:
[     16.893] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    16.893]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    16.893] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    21.271] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    21.271] (II) fglrx(0): Printing DDC gathered Modelines:
[     21.271] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    21.271]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    21.271] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    21.585] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    21.585] (II) fglrx(0): Printing DDC gathered Modelines:
[     21.585] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    21.585]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    21.585] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    21.600] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.956] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    21.956] (II) fglrx(0): Printing DDC gathered Modelines:
[     21.956] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    21.956]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    21.956] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    22.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.102] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.124] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    22.124] (II) fglrx(0): Printing DDC gathered Modelines:
[     22.124] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    22.124]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    22.124] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    22.401] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    22.401] (II) fglrx(0): Printing DDC gathered Modelines:
[     22.401] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    22.401]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    22.401] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    24.077] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    36.052] (II) fglrx(0): Lid Close Received
[    36.067] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    36.067] (II) fglrx(0): Printing DDC gathered Modelines:
[     36.067] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    36.067]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    36.067] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    36.092] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    36.092] (II) fglrx(0): Printing DDC gathered Modelines:
[     36.092] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    36.092]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    36.092] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    37.812] (II) AIGLX: Suspending AIGLX clients for VT switch
[    37.813] (II) fglrx(0): Backup framebuffer data.
[    37.880] (II) fglrx(0): Backup complete.
[    39.551] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    45.896] (II) AIGLX: Resuming AIGLX clients after VT switch
[    45.899] (II) fglrx(0): Restore framebuffer data.
[    45.959] (II) fglrx(0): Restore complete.
[    48.516] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    48.516] (II) fglrx(0): Printing DDC gathered Modelines:
[     48.516] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    48.516]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    48.516] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    48.527] (II) fglrx(0): Lid Open Received
[    48.527] (II) fglrx(0): System Power Source: AC
[    48.537] (II) fglrx(0): Lid Open Received
[    48.566] [dix] couldn't enable device 12
[    48.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.587] (II) fglrx(0): EDID vendor "LGD", prod id 708
[    48.587] (II) fglrx(0): Printing DDC gathered Modelines:
[     48.587] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052  2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    48.587]  (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080   1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    48.587] (II)  fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080  1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    48.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.596] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.607] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.617] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   496.910] (II) fglrx(0): EDID vendor "LGD", prod id 708
[   496.910] (II) fglrx(0): Printing DDC gathered Modelines:
[    496.910] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008  2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    496.910] (II) fglrx(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000  2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[   496.911]  (II) fglrx(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080   1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
```

==============================
Output of /var/log/lightdm/lightdm.log
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.1, UID=0 PID=1160
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.01s] DEBUG: Adding default seat
[+0.01s] DEBUG: Seat: Starting
[+0.01s] DEBUG: Seat: Creating greeter session
[+0.01s] DEBUG: Seat: Creating display server of type x
[+0.01s] DEBUG: Deactivating Plymouth
[+0.04s] DEBUG: Using VT 7
[+0.04s] DEBUG: Seat: Starting local X display on VT 7
[+0.04s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.04s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.04s] DEBUG: DisplayServer x-0: Launching X Server
[+0.04s] DEBUG: Launching process 1214: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.04s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.04s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.04s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.08s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.08s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+2.79s] DEBUG: Got signal 10 from process 1214
[+2.79s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+2.79s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+2.82s] DEBUG: Quitting Plymouth; retaining splash
[+2.85s] DEBUG: Seat: Display server ready, starting session authentication
[+2.85s] DEBUG: Session pid=1376: Started with service 'lightdm-greeter', username 'lightdm'
[+2.88s] DEBUG: Session pid=1376: Authentication complete with return value 0: Success
[+2.88s] DEBUG: Seat: Session authenticated, running command
[+2.88s] DEBUG: Session pid=1376: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+2.88s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+2.88s] DEBUG: Session pid=1376: Logging to /var/log/lightdm/x-0-greeter.log
[+2.90s] DEBUG: Activating VT 7
[+2.90s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+3.10s] DEBUG: Session pid=1376: Greeter connected version=1.10.1
[+3.42s] DEBUG: Session pid=1376: Greeter start authentication for ceegee
[+3.42s] DEBUG: Session pid=1439: Started with service 'lightdm', username 'ceegee'
[+3.43s] DEBUG: Session pid=1439: Got 1 message(s) from PAM
[+3.43s] DEBUG: Session pid=1376: Prompt greeter with 1 message(s)
[+7.61s] DEBUG: Session pid=1376: Continue authentication
[+7.65s] DEBUG: Session pid=1439: Authentication complete with return value 0: Success
[+7.65s] DEBUG: Session pid=1376: Authenticate result for user ceegee: Success
[+7.65s] DEBUG: Session pid=1376: User ceegee authorized
[+7.66s] DEBUG: Session pid=1376: Greeter requests session ubuntu
[+7.66s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+7.66s] DEBUG: Session pid=1376: Sending SIGTERM
[+7.67s] DEBUG: Session pid=1376: Exited with return value 0
[+7.67s] DEBUG: Seat: Session stopped
[+7.67s] DEBUG: Seat: Greeter stopped, running session
[+7.67s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+7.68s] DEBUG: Session pid=1439: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+7.68s] DEBUG: Creating shared data directory /var/lib/lightdm-data/ceegee
[+7.68s] DEBUG: Session pid=1439: Logging to .xsession-errors
[+7.70s] DEBUG: Activating VT 7
[+7.70s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c2
[+8.88s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+95.53s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
```

=================================
Output of /var/log/lightdm/x-0.log

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=8c084118-427f-4a4e-89f2-bb32977d993d ro persistent splash nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000af2befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af2bf000-0x00000000af6befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000af6bf000-0x00000000af7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000af7bf000-0x00000000af7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000af7ff000-0x00000000af7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af800000-0x00000000afffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000044effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP ENVY 17 NOTEBOOK/1852, BIOS F.0B 01/02/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x44f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0AF800000 mask FFF800000 uncachable
[    0.000000]   3 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0FFB00000 mask FFFF00000 write-protect
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask E00000000 write-back
[    0.000000]   8 base 400000000 mask F80000000 write-back
[    0.000000]   9 base 44F000000 mask FFF000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xaf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x44ee00000-0x44effffff]
[    0.000000]  [mem 0x44ee00000-0x44effffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x44c000000-0x44edfffff]
[    0.000000]  [mem 0x44c000000-0x44edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x44bffffff]
[    0.000000]  [mem 0x400000000-0x44bffffff] page 2M
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0xaf2befff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xaf1fffff] page 2M
[    0.000000]  [mem 0xaf200000-0xaf2befff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaf7ff000-0xaf7fffff]
[    0.000000]  [mem 0xaf7ff000-0xaf7fffff] page 4k
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35b5a000-0x36da4fff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000af7fe210 0000A4 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000af7fb000 00010C (v05 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: DSDT 00000000af7e8000 00F4A5 (v01 HPQOEM 1852     00000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000af7ba000 000040
[    0.000000] ACPI: UEFI 00000000af7fd000 000236 (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: ASF! 00000000af7fc000 0000A5 (v32 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: HPET 00000000af7fa000 000038 (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: APIC 00000000af7f9000 00008C (v03 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: MCFG 00000000af7f8000 00003C (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: SLIC 00000000af7e7000 000176 (v01 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000af7e5000 001066 (v01 HPQOEM 1852     00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000af7e3000 000028 (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000af7e0000 0003D1 (v01 HPQOEM 1852     00001000 ACPI 00040000)
[    0.000000] ACPI: ASPT 00000000af7de000 000034 (v07 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: FPDT 00000000af7db000 000044 (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000af7da000 0009AA (v01 HPQOEM 1852     00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000af7d9000 000A92 (v01 HPQOEM 1852     00003000 ACPI 00040000)
[    0.000000] ACPI: DMAR 00000000af7d8000 000080 (v01 HPQOEM 1852     00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000af7d7000 000F5A (v01 HPQOEM 1852     00001000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000044effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x44effffff]
[    0.000000]   NODE_DATA [mem 0x44efec000-0x44eff0fff]
[    0.000000]  [ffffea0000000000-ffffea00113fffff] PMD -> [ffff88043e600000-ffff88044e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x44effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xaf2befff]
[    0.000000]   node   0: [mem 0xaf7ff000-0xaf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x44effffff]
[    0.000000] On node 0 totalpages: 4186716
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11147 pages used for memmap
[    0.000000]   DMA32 zone: 713408 pages, LIFO batch:31
[    0.000000]   Normal zone: 54208 pages used for memmap
[    0.000000]   Normal zone: 3469312 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf2bf000-0xaf6befff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf6bf000-0xaf7befff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf7bf000-0xaf7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf800000-0xafffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xb0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] e820: [mem 0xb0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88044ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4121276
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=8c084118-427f-4a4e-89f2-bb32977d993d ro persistent splash nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16382308K/16746864K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 364556K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2693.813 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.62 BogoMIPS (lpj=10775252)
[    0.000072] pid_max: default: 32768 minimum: 301
[    0.000123] Security Framework initialized
[    0.000172] AppArmor: AppArmor initialized
[    0.000206] Yama: becoming mindful.
[    0.001175] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004850] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.006486] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006537] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006777] Initializing cgroup subsys memory
[    0.006815] Initializing cgroup subsys devices
[    0.006850] Initializing cgroup subsys freezer
[    0.006885] Initializing cgroup subsys blkio
[    0.006919] Initializing cgroup subsys perf_event
[    0.006954] Initializing cgroup subsys hugetlb
[    0.007006] CPU: Physical Processor ID: 0
[    0.007040] CPU: Processor Core ID: 0
[    0.007077] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.007077] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007451] mce: CPU supports 9 MCE banks
[    0.007497] CPU0: Thermal monitoring enabled (TM1)
[    0.007540] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007540] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.007540] tlb_flushall_shift: 2
[    0.007701] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.008810] ACPI: Core revision 20131115
[    0.014449] ACPI: All ACPI Tables successfully acquired
[    0.048117] ftrace: allocating 28537 entries in 112 pages
[    0.060210] dmar: Host address width 36
[    0.060245] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.060292] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.062862] dmar: RMRR base: 0x000000af68f000 end: 0x000000af6aefff
[    0.062968] IOAPIC id 0 under DRHD base  0xfed90000 IOMMU 0
[    0.063004] HPET id 0 under DRHD base 0xfed90000
[    0.063103] Enabled IRQ remapping in x2apic mode
[    0.063137] Enabling x2apic
[    0.063171] Enabled x2apic
[    0.063207] Switched APIC routing to cluster x2apic.
[    0.063680] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.103384] smpboot: CPU0: Intel(R) Core(TM) i7-3820QM CPU @ 2.70GHz (fam: 06, model: 3a, stepping: 09)
[    0.103509] TSC deadline timer enabled
[    0.103517] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.103695] ... version:                3
[    0.103730] ... bit width:              48
[    0.103764] ... generic registers:      4
[    0.103798] ... value mask:             0000ffffffffffff
[    0.103833] ... max period:             0000ffffffffffff
[    0.103868] ... fixed-purpose events:   3
[    0.103902] ... event mask:             000000070000000f
[    0.105321] x86: Booting SMP configuration:
[    0.119003] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.105356] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.199723] x86: Booted up 1 node, 8 CPUs
[    0.199790] smpboot: Total of 8 processors activated (43101.00 BogoMIPS)
[    0.207638] devtmpfs: initialized
[    0.210313] EVM: security.selinux
[    0.210347] EVM: security.SMACK64
[    0.210380] EVM: security.ima
[    0.210412] EVM: security.capability
[    0.210483] PM: Registering ACPI NVS region [mem 0xaf6bf000-0xaf7befff] (1048576 bytes)
[    0.211218] pinctrl core: initialized pinctrl subsystem
[    0.211298] regulator-dummy: no parameters
[    0.211377] RTC time:  0:47:35, date: 09/28/14
[    0.211441] NET: Registered protocol family 16
[    0.211562] cpuidle: using governor ladder
[    0.211596] cpuidle: using governor menu
[    0.211661] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.211703] ACPI: bus type PCI registered
[    0.211738] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.211822] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.211866] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.228257] PCI: Using configuration type 1 for base access
[    0.229109] bio: create slab <bio-0> at 0
[    0.229286] ACPI: Added _OSI(Module Device)
[    0.229321] ACPI: Added _OSI(Processor Device)
[    0.229355] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.229390] ACPI: Added _OSI(Processor Aggregator Device)
[    0.231834] ACPI: Executed 1 blocks of module-level executable AML code
[    0.235477] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.393925] ACPI: SSDT 00000000af5fb018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.394331] ACPI: Dynamic OEM Table Load:
[    0.394419] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.395669] ACPI: SSDT 00000000af5fca98 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.396094] ACPI: Dynamic OEM Table Load:
[    0.396181] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.399568] ACPI: SSDT 00000000af5fad98 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.399968] ACPI: Dynamic OEM Table Load:
[    0.400055] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    1.250266] ACPI: Interpreter enabled
[    1.250306] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    1.250403] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    1.250510] ACPI: (supports S0 S3 S4 S5)
[    1.250545] ACPI: Using IOAPIC for interrupt routing
[    1.250599] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.250761] ACPI: No dock devices found.
[    1.272039] ACPI: Power Resource [FN00] (on)
[    1.272611] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.272650] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    1.272786] \_SB_.PCI0:_OSC invalid UUID
[    1.272787] _OSC request data:1 1f 0 
[    1.272791] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    1.273351] PCI host bridge to bus 0000:00
[    1.273387] pci_bus 0000:00: root bus resource [bus 00-fe]
[    1.273422] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.273458] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.273494] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.273530] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xfeafffff]
[    1.273571] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.273639] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    1.273666] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.273697] pci 0000:00:01.0: System wakeup disabled by ACPI
[    1.273781] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.273804] pci 0000:00:14.0: reg 0x10: [mem 0xc3200000-0xc320ffff 64bit]
[    1.273874] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.273909] pci 0000:00:14.0: System wakeup disabled by ACPI
[    1.273970] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.273992] pci 0000:00:16.0: reg 0x10: [mem 0xc3214000-0xc321400f 64bit]
[    1.274067] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.274135] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.274431] pci 0000:00:1a.0: reg 0x10: [mem 0xc3219000-0xc32193ff]
[    1.276145] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.276196] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    1.276259] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.276274] pci 0000:00:1b.0: reg 0x10: [mem 0xc3210000-0xc3213fff 64bit]
[    1.276342] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.276379] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    1.276443] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.276572] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.276619] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    1.276683] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.276812] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.276860] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    1.276921] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    1.276999] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.277038] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    1.277104] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.277398] pci 0000:00:1d.0: reg 0x10: [mem 0xc3218000-0xc32183ff]
[    1.279119] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.279166] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    1.279230] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    1.279388] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.279406] pci 0000:00:1f.2: reg 0x10: [io  0x5048-0x504f]
[    1.279414] pci 0000:00:1f.2: reg 0x14: [io  0x5054-0x5057]
[    1.279422] pci 0000:00:1f.2: reg 0x18: [io  0x5040-0x5047]
[    1.279430] pci 0000:00:1f.2: reg 0x1c: [io  0x5050-0x5053]
[    1.279438] pci 0000:00:1f.2: reg 0x20: [io  0x5020-0x503f]
[    1.279446] pci 0000:00:1f.2: reg 0x24: [mem 0xc3217000-0xc32177ff]
[    1.279490] pci 0000:00:1f.2: PME# supported from D3hot
[    1.279544] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.279564] pci 0000:00:1f.3: reg 0x10: [mem 0xc3215000-0xc32150ff 64bit]
[    1.279584] pci 0000:00:1f.3: reg 0x20: [io  0x5000-0x501f]
[    1.279680] pci 0000:01:00.0: [1002:6827] type 00 class 0x030000
[    1.279689] pci 0000:01:00.0: reg 0x10: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.279696] pci 0000:01:00.0: reg 0x18: [mem 0xc2000000-0xc203ffff 64bit]
[    1.279701] pci 0000:01:00.0: reg 0x20: [io  0x4000-0x40ff]
[    1.279710] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    1.279731] pci 0000:01:00.0: supports D1 D2
[    1.279732] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    1.279747] pci 0000:01:00.0: System wakeup disabled by ACPI
[    1.279803] pci 0000:01:00.1: [1002:aab0] type 00 class 0x040300
[    1.279812] pci 0000:01:00.1: reg 0x10: [mem 0xc2040000-0xc2043fff 64bit]
[    1.279850] pci 0000:01:00.1: supports D1 D2
[    1.291574] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    1.291630] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.291633] pci 0000:00:01.0:   bridge window [mem 0xc2000000-0xc2ffffff]
[    1.291635] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.291933] pci 0000:07:00.0: [8086:088e] type 00 class 0x028000
[    1.292083] pci 0000:07:00.0: reg 0x10: [mem 0xc3100000-0xc3101fff 64bit]
[    1.292787] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    1.292941] pci 0000:07:00.0: System wakeup disabled by ACPI
[    1.303680] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    1.303722] pci 0000:00:1c.0:   bridge window [mem 0xc3100000-0xc31fffff]
[    1.303913] pci 0000:08:00.0: [10ec:5229] type 00 class 0xff0000
[    1.303975] pci 0000:08:00.0: reg 0x10: [mem 0xc1000000-0xc1000fff]
[    1.304466] pci 0000:08:00.0: supports D1 D2
[    1.304467] pci 0000:08:00.0: PME# supported from D1 D2 D3hot
[    1.304551] pci 0000:08:00.0: System wakeup disabled by ACPI
[    1.315636] pci 0000:00:1c.2: PCI bridge to [bus 08-0d]
[    1.315675] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    1.315680] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.315688] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.315848] pci 0000:0e:00.0: [1969:1083] type 00 class 0x020000
[    1.315942] pci 0000:0e:00.0: reg 0x10: [mem 0xc3000000-0xc303ffff 64bit]
[    1.315991] pci 0000:0e:00.0: reg 0x18: [io  0x2000-0x207f]
[    1.316450] pci 0000:0e:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.316570] pci 0000:0e:00.0: System wakeup disabled by ACPI
[    1.327632] pci 0000:00:1c.4: PCI bridge to [bus 0e]
[    1.327670] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    1.327674] pci 0000:00:1c.4:   bridge window [mem 0xc3000000-0xc30fffff]
[    1.328103] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.328531] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.328924] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.329316] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.329710] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.330136] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.330529] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.330922] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.331629] ACPI: Enabled 4 GPEs in block 00 to 3F
[    1.331720] ACPI: \_SB_.PCI0: notify handler is installed
[    1.331766] Found 1 acpi root devices
[    1.331802] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.331909] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.331950] vgaarb: loaded
[    1.331983] vgaarb: bridge control possible 0000:01:00.0
[    1.332132] SCSI subsystem initialized
[    1.332200] libata version 3.00 loaded.
[    1.332215] ACPI: bus type USB registered
[    1.332260] usbcore: registered new interface driver usbfs
[    1.332299] usbcore: registered new interface driver hub
[    1.332350] usbcore: registered new device driver usb
[    1.332479] PCI: Using ACPI for IRQ routing
[    1.339653] PCI: pci_cache_line_size set to 64 bytes
[    1.339802] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    1.339803] e820: reserve RAM buffer [mem 0xaf2bf000-0xafffffff]
[    1.339805] e820: reserve RAM buffer [mem 0xaf800000-0xafffffff]
[    1.339806] e820: reserve RAM buffer [mem 0x44f000000-0x44fffffff]
[    1.339867] NetLabel: Initializing
[    1.339901] NetLabel:  domain hash size = 128
[    1.339935] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.339979] NetLabel:  unlabeled traffic allowed by default
[    1.340056] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.340333] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.342397] Switched to clocksource hpet
[    1.345868] AppArmor: AppArmor Filesystem Enabled
[    1.345919] pnp: PnP ACPI init
[    1.345961] ACPI: bus type PNP registered
[    1.346024] pnp 00:00: [dma 4]
[    1.346038] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.346054] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    1.346126] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.346151] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.346181] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.346218] system 00:04: [io  0x1000-0x100f] has been reserved
[    1.346253] system 00:04: [io  0xffff] has been reserved
[    1.346288] system 00:04: [io  0xffff] has been reserved
[    1.346324] system 00:04: [io  0x0400-0x0453] could not be reserved
[    1.346359] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.346405] system 00:04: [io  0x0700-0x077f] has been reserved
[    1.346439] system 00:04: [io  0x0500-0x0501] has been reserved
[    1.346476] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.346497] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.346531] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.346567] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.346590] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.346610] pnp 00:08: Plug and Play ACPI device, IDs SYN1e67 SYN1e00 SYN0002 PNP0f13 (active)
[    1.346636] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.346718] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.346754] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.346790] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.346826] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.346862] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.346899] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.346935] system 00:0a: [mem 0xfed90000-0xfed93fff] could not be reserved
[    1.346971] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.347008] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.347042] system 00:0a: [mem 0xc3300000-0xc3300fff] has been reserved
[    1.347079] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.347320] system 00:0b: [mem 0x20000000-0x201fffff] could not be reserved
[    1.347357] system 00:0b: [mem 0x40004000-0x40004fff] could not be reserved
[    1.347393] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.347408] pnp: PnP ACPI: found 12 devices
[    1.347443] ACPI: bus type PNP unregistered
[    1.353465] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.353544] pci 0000:01:00.0: BAR 6: assigned [mem 0xc2060000-0xc207ffff pref]
[    1.353586] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    1.353622] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.353659] pci 0000:00:01.0:   bridge window [mem 0xc2000000-0xc2ffffff]
[    1.353696] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.353739] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    1.353779] pci 0000:00:1c.0:   bridge window [mem 0xc3100000-0xc31fffff]
[    1.353825] pci 0000:00:1c.2: PCI bridge to [bus 08-0d]
[    1.353862] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    1.353902] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.353940] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.353989] pci 0000:00:1c.4: PCI bridge to [bus 0e]
[    1.354024] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    1.356547] pci 0000:00:1c.4:   bridge window [mem 0xc3000000-0xc30fffff]
[    1.356590] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.356591] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.356593] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.356594] pci_bus 0000:00: resource 7 [mem 0xb0000000-0xfeafffff]
[    1.356595] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.356597] pci_bus 0000:01: resource 1 [mem 0xc2000000-0xc2ffffff]
[    1.356598] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.356600] pci_bus 0000:07: resource 1 [mem 0xc3100000-0xc31fffff]
[    1.356601] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    1.356602] pci_bus 0000:08: resource 1 [mem 0xc1000000-0xc1ffffff]
[    1.356604] pci_bus 0000:08: resource 2 [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.356605] pci_bus 0000:0e: resource 0 [io  0x2000-0x2fff]
[    1.356606] pci_bus 0000:0e: resource 1 [mem 0xc3000000-0xc30fffff]
[    1.356628] NET: Registered protocol family 2
[    1.356813] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.357059] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.357206] TCP: Hash tables configured (established 131072 bind 65536)
[    1.357253] TCP: reno registered
[    1.357301] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.357384] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.357490] NET: Registered protocol family 1
[    1.390488] pci 0000:01:00.0: Boot video device
[    1.390550] PCI: CLS 64 bytes, default 64
[    1.390591] Trying to unpack rootfs image as initramfs...
[    1.643597] Freeing initrd memory: 18732K (ffff880035b5a000 - ffff880036da5000)
[    1.643680] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.643718] software IO TLB [mem 0xab2bf000-0xaf2bf000] (64MB) mapped at [ffff8800ab2bf000-ffff8800af2befff]
[    1.643799] Simple Boot Flag at 0x44 set to 0x1
[    1.644066] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    1.644107] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    1.644148] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    1.644190] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    1.644228] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x15
[    1.644268] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x15
[    1.644311] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x15
[    1.644354] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x15
[    1.644432] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.644475] Scanning for low memory corruption every 60 seconds
[    1.644723] Initialise system trusted keyring
[    1.644789] audit: initializing netlink socket (disabled)
[    1.644832] type=2000 audit(1411865256.604:1): initialized
[    1.668246] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.669211] zbud: loaded
[    1.669361] VFS: Disk quotas dquot_6.5.2
[    1.669424] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.669753] fuse init (API version 7.22)
[    1.669839] msgmni has been set to 32033
[    1.669910] Key type big_key registered
[    1.670346] Key type asymmetric registered
[    1.670381] Asymmetric key parser 'x509' registered
[    1.670434] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.670516] io scheduler noop registered
[    1.670551] io scheduler deadline registered (default)
[    1.670601] io scheduler cfq registered
[    1.670784] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    1.671157] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.671201] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.671266] intel_idle: MWAIT substates: 0x21120
[    1.671267] intel_idle: v0.4 model 0x3A
[    1.671268] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.671400] ipmi message handler version 39.2
[    1.874465] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.875396] ACPI: AC Adapter [AC] (off-line)
[    1.875522] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.876172] ACPI: Lid Switch [LID0]
[    1.876286] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.876335] ACPI: Power Button [PWRB]
[    1.876419] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.876461] ACPI: Power Button [PWRF]
[    1.876541] ACPI: Fan [FAN0] (on)
[    1.879477] thermal LNXTHERM:00: registered as thermal_zone0
[    1.879514] ACPI: Thermal Zone [TZ00] (0 C)
[    1.880307] thermal LNXTHERM:01: registered as thermal_zone1
[    1.880343] ACPI: Thermal Zone [TZ01] (51 C)
[    1.880396] GHES: HEST is not enabled!
[    1.880544] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.882827] Linux agpgart interface v0.103
[    1.884316] brd: module loaded
[    1.884596] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.884646] ACPI: Battery Slot [BAT0] (battery present)
[    1.884987] loop: module loaded
[    1.885277] libphy: Fixed MDIO Bus: probed
[    1.885369] tun: Universal TUN/TAP device driver, 1.6
[    1.885404] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.885476] PPP generic driver version 2.4.2
[    1.885538] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.885576] ehci-pci: EHCI PCI platform driver
[    1.885708] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.885747] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.885800] ehci-pci 0000:00:1a.0: debug port 2
[    1.889726] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.889747] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc3219000
[    1.898233] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.898298] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.898333] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.898374] usb usb1: Product: EHCI Host Controller
[    1.898409] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.898445] usb usb1: SerialNumber: 0000:00:1a.0
[    1.898557] hub 1-0:1.0: USB hub found
[    1.898596] hub 1-0:1.0: 2 ports detected
[    1.898782] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.898820] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.898870] ehci-pci 0000:00:1d.0: debug port 2
[    1.902784] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.902799] ehci-pci 0000:00:1d.0: irq 20, io mem 0xc3218000
[    1.914227] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.914292] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.914329] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.914370] usb usb2: Product: EHCI Host Controller
[    1.914406] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.914441] usb usb2: SerialNumber: 0000:00:1d.0
[    1.914574] hub 2-0:1.0: USB hub found
[    1.914611] hub 2-0:1.0: 2 ports detected
[    1.914721] ehci-platform: EHCI generic platform driver
[    1.914761] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.914797] ohci-pci: OHCI PCI platform driver
[    1.914837] ohci-platform: OHCI generic platform driver
[    1.914874] uhci_hcd: USB Universal Host Controller Interface driver
[    1.914995] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.915034] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.915167] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.915192] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    1.915243] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.915279] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.915320] usb usb3: Product: xHCI Host Controller
[    1.915355] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.915390] usb usb3: SerialNumber: 0000:00:14.0
[    1.915521] hub 3-0:1.0: USB hub found
[    1.915562] hub 3-0:1.0: 4 ports detected
[    1.915834] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.915871] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.915940] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.915977] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.916018] usb usb4: Product: xHCI Host Controller
[    1.916053] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.916089] usb usb4: SerialNumber: 0000:00:14.0
[    1.916213] hub 4-0:1.0: USB hub found
[    1.916254] hub 4-0:1.0: 4 ports detected
[    1.922425] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.924538] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.924581] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.924833] mousedev: PS/2 mouse device common for all mice
[    1.925114] rtc_cmos 00:05: RTC can wake from S4
[    1.925352] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.925424] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.925516] device-mapper: uevent: version 1.0.3
[    1.925629] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.925676] ledtrig-cpu: registered to indicate activity on CPUs
[    1.925790] TCP: cubic registered
[    1.925878] NET: Registered protocol family 10
[    1.926041] NET: Registered protocol family 17
[    1.926081] Key type dns_resolver registered
[    1.926421] Loading compiled-in X.509 certificates
[    1.927208] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    1.927261] registered taskstats version 1
[    1.929622] Key type trusted registered
[    1.931626] Key type encrypted registered
[    1.933365] AppArmor: AppArmor sha1 policy hashing enabled
[    1.933403] IMA: No TPM chip found, activating TPM-bypass!
[    1.933852] regulator-dummy: disabling
[    1.934030]   Magic number: 14:355:760
[    1.934208] rtc_cmos 00:05: setting system clock to 2014-09-28 00:47:37 UTC (1411865257)
[    1.935502] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.935544] EDD information not available.
[    1.935597] PM: Hibernation image not present or could not be loaded.
[    1.936241] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    1.936279] Write protecting the kernel read-only data: 12288k
[    1.937741] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    1.938990] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.946718] systemd-udevd[144]: starting version 204
[    1.961811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.972269] rtsx_pci 0000:08:00.0: irq 43 for MSI/MSI-X
[    1.972306] rtsx_pci 0000:08:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 43
[    1.975761] ahci 0000:00:1f.2: version 3.0
[    1.975910] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.975942] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.990235] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1f impl SATA mode
[    1.990283] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    2.004174] atl1c 0000:0e:00.0: version 1.0.1.1-NAPI
[    2.022747] scsi0 : ahci
[    2.022960] scsi1 : ahci
[    2.023100] scsi2 : ahci
[    2.023268] scsi3 : ahci
[    2.023485] scsi4 : ahci
[    2.023715] scsi5 : ahci
[    2.023800] ata1: SATA max UDMA/133 abar m2048@0xc3217000 port 0xc3217100 irq 44
[    2.023845] ata2: SATA max UDMA/133 abar m2048@0xc3217000 port 0xc3217180 irq 44
[    2.023884] ata3: SATA max UDMA/133 abar m2048@0xc3217000 port 0xc3217200 irq 44
[    2.023923] ata4: SATA max UDMA/133 abar m2048@0xc3217000 port 0xc3217280 irq 44
[    2.023962] ata5: SATA max UDMA/133 abar m2048@0xc3217000 port 0xc3217300 irq 44
[    2.024000] ata6: DUMMY
[    2.210297] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.342188] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.342411] ata1.00: supports DRM functions and may not be fully accessible
[    2.342526] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.342529] ata1.00: ATA-9: Samsung SSD 840 EVO 1TB mSATA, EXT41B6Q, max UDMA/133
[    2.342568] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.342569] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.342651] ata1.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.342861] hub 1-1:1.0: USB hub found
[    2.342906] ata1.00: supports DRM functions and may not be fully accessible
[    2.342992] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.343035] ata1.00: configured for UDMA/133
[    2.343066] hub 1-1:1.0: 6 ports detected
[    2.343321] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT4 PQ: 0 ANSI: 5
[    2.343479] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.343486] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.343523] sd 0:0:0:0: [sda] Write Protect is off
[    2.343533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.343544] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.346398]  sda: sda1 < sda5 > sda2
[    2.346948] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.454190] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.586524] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.586578] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.586895] hub 2-1:1.0: USB hub found
[    2.587124] hub 2-1:1.0: 6 ports detected
[    2.642076] tsc: Refined TSC clocksource calibration: 2693.880 MHz
[    2.658261] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.662044] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.720239] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x126c00, board id: 2128, fw id: 1103674
[    2.723762] ata2.00: ATA-8: LITEONIT LCT-256M3S, VRDC, max UDMA/133
[    2.723800] ata2.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.724131] ata2.00: configured for UDMA/133
[    2.724387] scsi 1:0:0:0: Direct-Access     ATA      LITEONIT LCT-256 VRDC PQ: 0 ANSI: 5
[    2.724558] sd 1:0:0:0: [sdb] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.724639] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.724649] sd 1:0:0:0: [sdb] Write Protect is off
[    2.724650] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.724658] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.725291]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 sdb8 >
[    2.725590] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.752406] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.754733] usb 1-1.1: New USB device found, idVendor=8087, idProduct=07da
[    2.754806] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.858166] usb 2-1.5: new high-speed USB device number 3 using ehci-pci
[    2.958847] usb 2-1.5: New USB device found, idVendor=0424, idProduct=b832
[    2.958910] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.958948] usb 2-1.5: Product: HP Wireless Audio Adapter
[    2.958981] usb 2-1.5: Manufacturer: Standard Microsystems Corp.
[    2.963785] hidraw: raw HID events driver (C) Jiri Kosina
[    2.968531] usbcore: registered new interface driver usbhid
[    2.968569] usbhid: USB HID core driver
[    2.974631] input: Standard Microsystems Corp. HP Wireless Audio Adapter as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.3/input/input6
[    2.974774] hid-generic 0003:0424:B832.0001: input,hiddev0,hidraw0: USB HID v1.10 Device [Standard Microsystems Corp. HP Wireless Audio Adapter] on usb-0000:00:1d.0-1.5/input3
[    3.030146] usb 2-1.6: new high-speed USB device number 4 using ehci-pci
[    3.041967] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.048444] ata3.00: ATA-9: ST1000LM024 HN-M101MBB, 2AR10002, max UDMA/133
[    3.048480] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.054990] ata3.00: configured for UDMA/133
[    3.055243] scsi 2:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR1 PQ: 0 ANSI: 5
[    3.055435] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.055448] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.055533] sd 2:0:0:0: [sdc] 4096-byte physical blocks
[    3.055611] sd 2:0:0:0: [sdc] Write Protect is off
[    3.055642] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.055650] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.163046] usb 2-1.6: New USB device found, idVendor=10f1, idProduct=1a37
[    3.163112] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.163151] usb 2-1.6: Product: HP TrueVision HD
[    3.163182] usb 2-1.6: Manufacturer: Importek
[    3.373863] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.374882] ata4.00: ATAPI: hp      BD E  DC6E2SH, WH61, max UDMA/100
[    3.376521] ata4.00: configured for UDMA/100
[    3.383488] scsi 3:0:0:0: CD-ROM            hp       BD E  DC6E2SH    WH61 PQ: 0 ANSI: 5
[    3.387524] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    3.387592] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.387822] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.387918] sr 3:0:0:0: Attached scsi generic sg3 type 5
[    3.422548]  sdc: sdc1
[    3.422907] sd 2:0:0:0: [sdc] Attached SCSI disk
[    3.642056] Switched to clocksource tsc
[    3.705743] ata5: SATA link down (SStatus 0 SControl 300)
[    3.770742] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.997708] random: init urandom read with 116 bits of entropy available
[    4.103055] init: plymouth-upstart-bridge main process (227) terminated with status 1
[    4.103101] init: plymouth-upstart-bridge main process ended, respawning
[    4.104909] init: plymouth-upstart-bridge main process (238) terminated with status 1
[    4.104951] init: plymouth-upstart-bridge main process ended, respawning
[    4.107691] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    4.107735] init: plymouth-upstart-bridge main process ended, respawning
[    4.145634] random: nonblocking pool is initialized
[    4.430864] Adding 16777212k swap on /dev/sda2.  Priority:-1 extents:1 across:16777212k SSFS
[    4.437144] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.454259] systemd-udevd[349]: starting version 204
[    4.482333] lp: driver loaded but no devices found
[    4.483595] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    4.483597] AMD IOMMUv2 functionality not available on this system
[    4.485085] Initializing HPQ6001 module
[    4.485164] input: HP Wireless hotkeys as /devices/virtual/input/input7
[    4.486477] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    4.486479] Disabling lock debugging due to kernel taint
[    4.488931] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[    4.489433] ppdev: user-space parallel port driver
[    4.494154] <6>[fglrx] Maximum main memory to use for locked dma buffers: 15645 MBytes.
[    4.494275] hp_accel: laptop model unknown, using default axes configuration
[    4.494303] <6>[fglrx]   vendor: 1002 device: 6827 count: 1
[    4.494498] <6>[fglrx] ioport: bar 4, base 0x4000, size: 0x100
[    4.495626] <6>[fglrx] Kernel PAT support is enabled
[    4.495644] <6>[fglrx] module loaded - fglrx 13.35.5 [Mar 12 2014] with 1 minors
[    4.504240] wmi: Mapper loaded
[    4.504415] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[    4.507092] lis3lv02d: 8 bits 3DC sensor found
[    4.508080] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    4.508085] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMBS 2 (20131115/utaddress-251)
[    4.508087] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.508090] ACPI Warning: 0x0000000000000730-0x000000000000073f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.508092] ACPI Warning: 0x0000000000000730-0x000000000000073f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPIO 2 (20131115/utaddress-251)
[    4.508093] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.508094] ACPI Warning: 0x0000000000000700-0x000000000000072f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.508095] ACPI Warning: 0x0000000000000700-0x000000000000072f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPIO 2 (20131115/utaddress-251)
[    4.508097] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.508098] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    4.508511] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    4.509434] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.509438] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD01._BQC] (Node ffff880438540e88), AE_NOT_FOUND (20131115/psparse-536)
[    4.509444] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.512767] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.512772] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD01._BCM] (Node ffff880438540eb0), AE_NOT_FOUND (20131115/psparse-536)
[    4.512779] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.514413] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.514418] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD02._BQC] (Node ffff880438542000), AE_NOT_FOUND (20131115/psparse-536)
[    4.514423] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.516525] acpi LNXVIDEO:01: registered as cooling_device9
[    4.517025] cfg80211: Calling CRDA to update world regulatory domain
[    4.517589] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    4.518385] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.518390] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD03._BQC] (Node ffff880438542190), AE_NOT_FOUND (20131115/psparse-536)
[    4.518396] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.519342] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.519348] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD03._BCM] (Node ffff8804385421b8), AE_NOT_FOUND (20131115/psparse-536)
[    4.519356] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.521199] Bluetooth: Core ver 2.17
[    4.521207] NET: Registered protocol family 31
[    4.521208] Bluetooth: HCI device and connection manager initialized
[    4.521214] Bluetooth: HCI socket layer initialized
[    4.521215] Bluetooth: L2CAP socket layer initialized
[    4.521217] Bluetooth: SCO socket layer initialized
[    4.521600] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    4.521602] Copyright(c) 2003-2013 Intel Corporation
[    4.522312] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.522325] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD04._BQC] (Node ffff880438542320), AE_NOT_FOUND (20131115/psparse-536)
[    4.522338] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.523195] iwlwifi 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.524169] usbcore: registered new interface driver btusb
[    4.524508] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.524513] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD04._BCM] (Node ffff880438542348), AE_NOT_FOUND (20131115/psparse-536)
[    4.524520] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.526032] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.526036] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD05._BQC] (Node ffff8804385424b0), AE_NOT_FOUND (20131115/psparse-536)
[    4.526041] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.526800] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.526804] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD05._BCM] (Node ffff8804385424d8), AE_NOT_FOUND (20131115/psparse-536)
[    4.526808] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.528002] mute LED gpio 8 polarity 1
[    4.528113] iwlwifi 0000:07:00.0: irq 47 for MSI/MSI-X
[    4.528243] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[    4.528244]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.528245]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[    4.528245]    mono: mono_out=0x0
[    4.528246]    inputs:
[    4.528247]      Internal Mic=0x11
[    4.528248]      Mic=0xc
[    4.528550] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.528554] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD06._BQC] (Node ffff880438542640), AE_NOT_FOUND (20131115/psparse-536)
[    4.528560] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.529449] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.529453] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD06._BCM] (Node ffff880438542668), AE_NOT_FOUND (20131115/psparse-536)
[    4.529461] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.536677] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.536681] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD07._BQC] (Node ffff8804385427d0), AE_NOT_FOUND (20131115/psparse-536)
[    4.536685] ACPI Warning: Evaluating _BQC failed (20131115/video-665)
[    4.537342] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.BLVL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    4.537345] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD07._BCM] (Node ffff8804385427f8), AE_NOT_FOUND (20131115/psparse-536)
[    4.537349] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    4.538738] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input8
[    4.538790] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    4.538793] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    4.538796] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    4.538799] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    4.538804] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    4.547779] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.549438] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.550166] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    4.550168] hda-intel 0000:01:00.1: Using LPIB position fix
[    4.550169] hda-intel 0000:01:00.1: Force to non-snoop mode
[    4.550202] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[    4.550405] type=1400 audit(1411879660.115:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=447 comm="apparmor_parser"
[    4.550411] type=1400 audit(1411879660.115:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=447 comm="apparmor_parser"
[    4.550415] type=1400 audit(1411879660.115:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[    4.550781] type=1400 audit(1411879660.115:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=447 comm="apparmor_parser"
[    4.550786] type=1400 audit(1411879660.115:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[    4.550972] type=1400 audit(1411879660.115:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[    4.552606] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[    4.562541] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    4.562593] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    4.562638] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    4.567259] iwlwifi 0000:07:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.573181] usbcore: registered new interface driver snd-usb-audio
[    4.578190] Linux video capture interface: v2.00
[    4.583671] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.583674] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.583676] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.583678] iwlwifi 0000:07:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[    4.583825] iwlwifi 0000:07:00.0: L1 Enabled; Disabling L0S
[    4.584617] uvcvideo: Found UVC 1.00 device HP TrueVision HD (10f1:1a37)
[    4.587548] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input14
[    4.587726] usbcore: registered new interface driver uvcvideo
[    4.587727] USB Video Class driver (1.1.1)
[    4.605254] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.653606] Adding 5337084k swap on /dev/sdb8.  Priority:-2 extents:1 across:5337084k SSFS
[    4.702199] cfg80211: World regulatory domain updated:
[    4.702201] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.702202] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.702203] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.702204] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.702205] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.702205] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.716399] intel_rapl: domain uncore energy ctr 0:0 not working, skip
[    4.741371] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input16
[    4.801154] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    4.934753] init: failsafe main process (700) killed by TERM signal
[    5.029089] type=1400 audit(1411879660.591:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=799 comm="apparmor_parser"
[    5.029094] type=1400 audit(1411879660.591:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=799 comm="apparmor_parser"
[    5.029429] type=1400 audit(1411879660.595:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=799 comm="apparmor_parser"
[    5.059816] Bluetooth: RFCOMM TTY layer initialized
[    5.059825] Bluetooth: RFCOMM socket layer initialized
[    5.059829] Bluetooth: RFCOMM ver 1.11
[    5.060728] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.060731] Bluetooth: BNEP filters: protocol multicast
[    5.060734] Bluetooth: BNEP socket layer initialized
[    5.073379] input: HP WMI hotkeys as /devices/virtual/input/input15
[    5.096322] init: cups main process (801) killed by HUP signal
[    5.096328] init: cups main process ended, respawning
[    5.404150] iwlwifi 0000:07:00.0: L1 Enabled; Disabling L0S
[    5.410687] iwlwifi 0000:07:00.0: Radio type=0x2-0x1-0x0
```

====================================
Output of /var/log/lightdm/x-0-greeter.log
```

Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:496: Starting unity-greeter 14.04.10 UID=112 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:499: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:513: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:541: Setting GTK+ settings

** (at-spi2-registryd:1408): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:1408): WARNING **: Unable to register client with session manager
[+0.09s] DEBUG: unity-greeter.vala:564: Creating Unity Greeter
[+0.09s] DEBUG: unity-greeter.vala:57: Creating background surface
[+0.11s] DEBUG: Connecting to display manager...
[+0.11s] DEBUG: Wrote 18 bytes to daemon
[+0.11s] DEBUG: Read 8 bytes from daemon
[+0.11s] DEBUG: Read 149 bytes from daemon
[+0.11s] DEBUG: Connected version=1.10.1 default-session=ubuntu show-manual-login=true hide-users=false has-guest-account=true show-remote-login=true
[+0.22s] DEBUG: menubar.vala:335: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.29s] DEBUG: menubar.vala:367: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.30s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.30s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.32s] DEBUG: user-list.vala:1030: Adding/updating user ceegee (ceegee)
[+0.32s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.40s] DEBUG: user-list.vala:1012: Adding guest account entry
[+0.42s] DEBUG: Ignoring configuration file /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf~, it does not have .conf suffix
[+0.42s] DEBUG: Ignoring configuration file /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf~, it does not have .conf suffix
[+0.42s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.42s] DEBUG: Starting authentication for user ceegee...
[+0.42s] DEBUG: Wrote 22 bytes to daemon
[+0.43s] DEBUG: main-window.vala:185: Screen is 1920x1080 pixels
[+0.43s] DEBUG: main-window.vala:193: Monitor 0 is 1920x1080 pixels at 0,0
[+0.43s] DEBUG: unity-greeter.vala:567: Showing greeter
[+0.43s] DEBUG: unity-greeter.vala:252: Showing main window
[+0.44s] DEBUG: background.vala:483: Regenerating backgrounds
[+0.44s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1080
[+0.45s] DEBUG: unity-greeter.vala:610: Starting main loop
[+0.45s] DEBUG: Read 8 bytes from daemon
[+0.45s] DEBUG: Read 36 bytes from daemon
[+0.45s] DEBUG: Prompt user with 1 message(s)
[+0.47s] DEBUG: settings-daemon.vala:75: Acquired org.gnome.SessionManager
[+0.47s] DEBUG: settings-daemon.vala:102: Acquired org.gnome.ScreenSaver
[+0.47s] DEBUG: settings-daemon.vala:159: All bus names acquired, starting unity-settings-daemon
[+0.57s] DEBUG: Connected to Application Indicator Service.
[+0.60s] DEBUG: menubar.vala:537: Adding indicator object 0x8f6710 at position 0
[+0.60s] DEBUG: menubar.vala:537: Adding indicator object 0x8f69d0 at position 1
[+0.64s] DEBUG: Request current apps
[+0.65s] DEBUG: unity-greeter.vala:235: starting system-ready sound

** (unity-settings-daemon:1462): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'
[+0.85s] DEBUG: menubar.vala:537: Adding indicator object 0x8f6450 at position 2

** (nm-applet:1444): CRITICAL **: nm_secret_agent_register: assertion 'priv->registered == FALSE' failed
[+0.98s] DEBUG: Building new application entry: :1.21  with icon: nm-no-connection at position 0
[+0.98s] DEBUG: menubar.vala:537: Adding indicator object 0xa12b00 at position 3
[+1.01s] DEBUG: menubar.vala:537: Adding indicator object 0x8f6f50 at position 2

(unity-settings-daemon:1462): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
[+1.06s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete

(unity-settings-daemon:1462): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS: unable to get EDID for output
[+1.21s] DEBUG: menubar.vala:537: Adding indicator object 0x8f6c90 at position 3
[+4.62s] DEBUG: Providing response to display manager
[+4.62s] DEBUG: Wrote 23 bytes to daemon
[+4.66s] DEBUG: Read 8 bytes from daemon
[+4.66s] DEBUG: Read 18 bytes from daemon
[+4.66s] DEBUG: Authentication complete for user ceegee with return code 0
[+4.67s] DEBUG: Starting session ubuntu
[+4.67s] DEBUG: Wrote 18 bytes to daemon
[+4.67s] DEBUG: Read 8 bytes from daemon
[+4.67s] DEBUG: Read 4 bytes from daemon
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
[+4.67s] DEBUG: unity-greeter.vala:605: Got a SIGTERM
[+4.67s] DEBUG: settings-daemon.vala:78: Failed to acquire name org.gnome.SessionManager
[+4.67s] DEBUG: settings-daemon.vala:105: Failed to acquire name org.gnome.ScreenSaver
[+4.67s] DEBUG: unity-greeter.vala:135: Failed to acquire name com.canonical.Unity
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
init: indicator-messages main process ended, respawning
[+4.67s] DEBUG: unity-greeter.vala:613: Cleaning up
[+4.67s] DEBUG: unity-greeter.vala:621: Upstart exited with return value 0
[+4.67s] DEBUG: unity-greeter.vala:633: AT-SPI exited with return value 0
[+4.67s] DEBUG: unity-greeter.vala:639: Exiting
init: indicator-session main process (1460) killed by TERM signal
init: indicator-application main process (1463) killed by TERM signal

** (unity-settings-daemon:1462): WARNING **: Name taken or bus went away - shutting down
init: indicator-bluetooth main process (1448) killed by TERM signal
init: indicator-power main process (1450) killed by TERM signal
init: indicator-datetime main process (1452) killed by TERM signal
init: indicator-messages main process (1783) killed by TERM signal

(unity-settings-daemon:1462): dconf-WARNING **: failed to commit changes to dconf: The connection is closed
g_dbus_connection_real_closed: Remote peer vanished with error: Error receiving message: Connection reset by peer (g-io-error-quark, 0). Exiting.
```

=====================================================
output of /var/log/boot.log

```
 * Starting Read required files in advance[74G[ OK ] 
 * Starting Mount filesystems on boot[74G[ OK ] 
 * Starting Populate /dev filesystem[74G[ OK ] 
 * Starting Populate and link to /run filesystem[74G[ OK ] 
 * Stopping Populate /dev filesystem[74G[ OK ] 
 * Stopping Populate and link to /run filesystem[74G[ OK ] 
 * Stopping Track if upstart is running in a container[74G[ OK ] 
 * Starting Initialize or finalize resolvconf[74G[ OK ] 
 * Starting set console keymap[74G[ OK ] 
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ] 
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ] 
 * Starting Bridge udev events into upstart[74G[ OK ] 
 * Starting Signal sysvinit that remote filesystems are mounted[74G[ OK ] 
 * Starting device node and kernel event manager[74G[ OK ] 
 * Starting load modules from /etc/modules[74G[ OK ] 
 * Starting cold plug devices[74G[ OK ] 
 * Starting log initial device creation[74G[ OK ] 
 * Stopping set console keymap[74G[ OK ] 
 * Stopping load modules from /etc/modules[74G[ OK ] 
 * Starting Uncomplicated firewall[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting Mount network filesystems[74G[ OK ] 
 * Stopping Mount network filesystems[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
 * Starting Bridge socket events into upstart[74G[ OK ] 
 * Starting Signal sysvinit that the rootfs is mounted[74G[ OK ] 
 * Starting Clean /tmp directory[74G[ OK ] 
 * Stopping Clean /tmp directory[74G[ OK ] 
 * Starting Signal sysvinit that local filesystems are mounted[74G[ OK ] 
 * Starting restore software rfkill state[74G[ OK ] 
 * Stopping restore software rfkill state[74G[ OK ] 
 * Starting Flush boot log to disk[74G[ OK ] 
 * Starting flush early job output to logs[74G[ OK ] 
 * Stopping Failsafe Boot Delay[74G[ OK ] 
 * Stopping Mount filesystems on boot[74G[ OK ] 
 * Starting System V initialisation compatibility[74G[ OK ] 
 * Stopping Flush boot log to disk[74G[ OK ] 
 * Stopping flush early job output to logs[74G[ OK ] 
 * Starting D-Bus system message bus[74G[ OK ] 
 * Starting modem connection manager[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting system logging daemon[74G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting Bridge file events into upstart[74G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting SystemD login management service[74G[ OK ] 
 * Starting bluetooth daemon[74G[ OK ] 
 * Starting mDNS/DNS-SD daemon[74G[ OK ] 
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[74G[ OK ] 
 * Stopping Reload cups, upon starting avahi-daemon to make sure remote queues are populated[74G[ OK ] 
 * Starting network connection manager[74G[ OK ] 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
 * Setting up X socket directories...       [80G  [74G[ OK ] 
 * Stopping System V initialisation compatibility[74G[ OK ] 
 * Starting System V runlevel compatibility[74G[ OK ] 
 * Starting save kernel messages[74G[ OK ] 
 * Starting Restore Sound Card State[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting anac(h)ronistic cron[74G[ OK ] 
 * Stopping Restore Sound Card State[74G[ OK ] 
 * Starting cups-browsed - Bonjour remote printer browsing daemon[74G[ OK ] 
 * Stopping Restore Sound Card State[74G[ OK ] 
 * Starting regular background program processing daemon[74G[ OK ] 
 * Starting CPU interrupts balancing daemon[74G[ OK ] 
 * Stopping cold plug devices[74G[ OK ] 
 * Stopping save kernel messages[74G[ OK ] 
 * Stopping log initial device creation[74G[ OK ] 
 * Starting configure virtual network devices[74G[ OK ] 
 * Starting load fallback graphics devices[74G[ OK ] 
 * Starting load fallback graphics devices[74G[[31mfail[39;49m] 
 * Starting save udev log and update rules[74G[ OK ] 
 * Starting automatic crash report generation[74G[ OK ] 
 * Stopping save udev log and update rules[74G[ OK ] 
 * Starting set console font[74G[ OK ] 
 * speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
 * Stopping Read required files in advance[74G[ OK ] 
 * Stopping set console font[74G[ OK ] 
saned disabled; edit /etc/default/saned 
 * Starting userspace bootsplash[74G[ OK ] 
 * Restoring resolver state...        * Starting crash report submission daemon[74G[ OK ] 
 * Stopping userspace bootsplash[74G[ OK ] 
[80G  [74G[ OK ] 
 * Starting Send an event to indicate plymouth is up[74G[ OK ] 
 * Starting ACPI daemon[74G[ OK ] 
 * Stopping System V runlevel compatibility[74G[ OK ] 
 * Starting LightDM Display Manager[74G[ OK ] 
 * Stopping Send an event to indicate plymouth is up[74G[ OK ]
```

---

### Post by andrew102 on 2014-09-28
I'm having a similar issue. Ubuntu 14.04 doesn't work properly with the fglrx (ATI) driver. I spent ages trying to get it to work - even installed Gnome and still Xorg server crashed.

So you went through and manually added the symbolic links but it still doesn't work? Same here.

My solution was to login to type ```
sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-dev -y
```
You should also remove /etc/X11/xorg.conf so that it won't try and load the fglrx driver.

On reboot I had a kernal panic but a couple more reboots got it going.

Anyway, looks like I'm going to have to buy a new PC that doesn't have ATI graphics for Ubuntu to work.

---

### Post by ceegee on 2014-09-28
Hey Andrew -

As of this morning it is working. 

Let me verify-

Why don't you output the same logs I put here? Are you able to login if you close your laptop lid, let it go to sleep and then wake it up again?

Happy to help if I can.

---

### Post by ceegee on 2014-09-29
Just an update for anyone else that comes this way, I think this is a lightdm bug, possible brightness issue. I have opened a ticket here. 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1375528](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1375528)

---

