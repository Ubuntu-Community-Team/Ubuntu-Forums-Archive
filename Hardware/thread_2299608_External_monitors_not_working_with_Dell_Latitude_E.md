---
title: "External monitors not working with Dell Latitude E7250+EPort Plus"
date: 2015-10-19
forum: Hardware
---

### Post by appleshampooid on 2015-10-19
I am running Xubuntu 14.04 on a Dell Lattitude E7250 (intel video card) and have a Dell E-Port Plus docking station. The docking station has 2 DVI ports and 2 DP (DisplayPort) ports on the back. The monitors accept DVI or DP, but I currently only have DVI cables. The 2 monitors are Dell 22 inch monitors (Model P2210).

When I dock the laptop and run xrandr, it doesn't even see the monitors as connected at all (neither does Xubuntu's graphical Display config). xrandr output is:

```
~ $ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+   47.5  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```
As you can see, it doesn't even list any DVI outputs. If I dock the laptop powered down and turn it on, X won't even start.

I soldiered on writing an xorg.conf that I hoped would work based on previous configurations like this (same monitors and dock, older laptop). My preferred setup is for each monitor to have it's own X screen, hence the usage of ZaphodHeads.

Using this config, X won't start. Here's my current xorg.conf:
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Dell"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Dell"
    ModelName      "DELL P2210"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    BusID "PCI:0:2:0"
    Option "ZaphodHeads" "DVI1"
    Option      "AccelMethod"  "sna"
    Screen 0
    Option "Monitor-DVI1" "Monitor0"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "intel"
    BusID "PCI:0:2:0"
    Option "ZaphodHeads" "DVI2"
    Option      "AccelMethod"  "sna"
    Screen 1
    Option "Monitor-DVI2" "Monitor1"
EndSection

```
I tried this with HDMI1/2, DP1/2, and DVI1/2 (shown here) as the outputs.


My most recent Xorg log looks like this:
```

[     3.967] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     3.967] X Protocol Version 11, Revision 0
[     3.967] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     3.967] Current Operating System: Linux nphilbrook 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64
[     3.967] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic root=UUID=c8acba09-c8ab-4cf0-a1cb-e0d65877fbc3 ro quiet splash vt.handoff=7
[     3.967] Build Date: 12 February 2015  02:49:29PM
[     3.967] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     3.967] Current version of pixman: 0.30.2
[     3.967] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     3.967] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.967] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 19 18:45:29 2015
[     3.967] (==) Using config file: "/etc/X11/xorg.conf"
[     3.967] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.968] (==) ServerLayout "Layout0"
[     3.968] (**) |-->Screen "Screen0" (0)
[     3.968] (**) |   |-->Monitor "Monitor0"
[     3.968] (**) |   |-->Device "Device0"
[     3.968] (**) |-->Screen "Screen1" (1)
[     3.968] (**) |   |-->Monitor "Monitor1"
[     3.968] (**) |   |-->Device "Device1"
[     3.968] (==) Automatically adding devices
[     3.968] (==) Automatically enabling devices
[     3.968] (==) Automatically adding GPU devices
[     3.968] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.968] 	Entry deleted from font path.
[     3.968] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.968] 	Entry deleted from font path.
[     3.968] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.968] 	Entry deleted from font path.
[     3.968] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.968] 	Entry deleted from font path.
[     3.968] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.968] 	Entry deleted from font path.
[     3.968] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     3.968] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.968] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.968] (II) Loader magic: 0x7f345daadd40
[     3.968] (II) Module ABI versions:
[     3.968] 	X.Org ANSI C Emulation: 0.4
[     3.968] 	X.Org Video Driver: 15.0
[     3.968] 	X.Org XInput driver : 20.0
[     3.968] 	X.Org Server Extension : 8.0
[     3.968] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.973] (--) PCI:*(0:0:2:0) 8086:1616:1028:062d rev 9, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     3.973] Initializing built-in extension Generic Event Extension
[     3.973] Initializing built-in extension SHAPE
[     3.973] Initializing built-in extension MIT-SHM
[     3.973] Initializing built-in extension XInputExtension
[     3.973] Initializing built-in extension XTEST
[     3.973] Initializing built-in extension BIG-REQUESTS
[     3.973] Initializing built-in extension SYNC
[     3.973] Initializing built-in extension XKEYBOARD
[     3.973] Initializing built-in extension XC-MISC
[     3.973] Initializing built-in extension SECURITY
[     3.973] Initializing built-in extension XINERAMA
[     3.973] Initializing built-in extension XFIXES
[     3.973] Initializing built-in extension RENDER
[     3.973] Initializing built-in extension RANDR
[     3.973] Initializing built-in extension COMPOSITE
[     3.973] Initializing built-in extension DAMAGE
[     3.973] Initializing built-in extension MIT-SCREEN-SAVER
[     3.973] Initializing built-in extension DOUBLE-BUFFER
[     3.973] Initializing built-in extension RECORD
[     3.973] Initializing built-in extension DPMS
[     3.973] Initializing built-in extension Present
[     3.973] Initializing built-in extension DRI3
[     3.973] Initializing built-in extension X-Resource
[     3.973] Initializing built-in extension XVideo
[     3.973] Initializing built-in extension XVideo-MotionCompensation
[     3.973] Initializing built-in extension SELinux
[     3.973] Initializing built-in extension XFree86-VidModeExtension
[     3.973] Initializing built-in extension XFree86-DGA
[     3.973] Initializing built-in extension XFree86-DRI
[     3.973] Initializing built-in extension DRI2
[     3.973] (II) LoadModule: "glx"
[     3.974] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.981] (II) Module glx: vendor="X.Org Foundation"
[     3.981] 	compiled for 1.15.1, module version = 1.0.0
[     3.981] 	ABI class: X.Org Server Extension, version 8.0
[     3.981] (==) AIGLX enabled
[     3.981] Loading extension GLX
[     3.981] (II) LoadModule: "intel"
[     3.982] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.982] (II) Module intel: vendor="X.Org Foundation"
[     3.982] 	compiled for 1.15.1, module version = 2.99.910
[     3.982] 	Module class: X.Org Video Driver
[     3.982] 	ABI class: X.Org Video Driver, version 15.0
[     3.982] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     3.983] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     3.983] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     3.983] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     3.983] (++) using VT number 7

[     3.983] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[     3.983] (II) intel(1): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[     3.983] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD graphics 5500
[     3.983] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     3.983] (II) intel(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
[     3.983] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     3.983] (==) intel(0): RGB weight 888
[     3.983] (==) intel(0): Default visual is TrueColor
[     3.983] (**) intel(0): Option "AccelMethod" "sna"
[     3.983] (**) intel(0): Option "ZaphodHeads" "DVI1"
[     3.983] (**) intel(0): Framebuffer tiled
[     3.983] (**) intel(0): Pixmaps tiled
[     3.983] (**) intel(0): "Tear free" disabled
[     3.983] (**) intel(0): Forcing per-crtc-pixmaps? no
[     3.983] (EE) intel(0): No outputs and no modes.
[     3.984] (--) intel(1): Integrated Graphics Chipset: Intel(R) HD graphics 5500
[     3.984] (--) intel(1): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     3.984] (II) intel(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
[     3.984] (==) intel(1): Depth 24, (--) framebuffer bpp 32
[     3.984] (==) intel(1): RGB weight 888
[     3.984] (==) intel(1): Default visual is TrueColor
[     3.984] (**) intel(1): Option "AccelMethod" "sna"
[     3.984] (**) intel(1): Option "ZaphodHeads" "DVI2"
[     3.984] (**) intel(1): Framebuffer tiled
[     3.984] (**) intel(1): Pixmaps tiled
[     3.984] (**) intel(1): "Tear free" disabled
[     3.984] (**) intel(1): Forcing per-crtc-pixmaps? no
[     3.984] (EE) intel(1): No outputs and no modes.
[     3.984] (II) UnloadModule: "intel"
[     3.984] (II) UnloadModule: "intel"
[     3.984] (EE) Screen(s) found, but none have a usable configuration.
[     3.984] (EE) 
Fatal server error:
[     3.984] (EE) no screens found(EE) 
[     3.984] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     3.984] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     3.984] (EE) 
[     3.986] (EE) Server terminated with error (1). Closing log file.

```

I have tried booting with the laptop lid closed or without. When I go to a virtual terminal, the 2 external moniters fire up and mirror the laptop's screen. But no X no way, no how. Any ideas? I'm going to pick up some DP cables tomorrow to see if that does the trick. But this exact same setup works in Windows 7, so I'm loathe to throw more hardware at the problem.

---

