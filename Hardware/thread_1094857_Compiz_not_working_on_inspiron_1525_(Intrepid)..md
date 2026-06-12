---
title: "Compiz not working on inspiron 1525 (Intrepid)."
date: 2009-03-13
forum: Hardware
---

### Post by codyxx on 2009-03-13
Okay, so essentially, Compiz is not working. I uninstalled it and reinstalled it, and still I get the same message when attempted to execute it:

```
cody@cody-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by michael37 on 2009-03-13
The problem is probably not in compiz.

Post the output of commands:
```

glxinfo

```

and your /var/log/Xorg.0.log and /etc/X11/xorg.conf files.

---

### Post by codyxx on 2009-03-13
Below are my current xorg.conf configurations:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Following are the results to the glxinfo command.

```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
 
```

Godspeed,
Cody

---

### Post by codyxx on 2009-03-13
bump

---

### Post by michael37 on 2009-03-14
your 3d acceleration is not working at all -- that's why compiz refuses to work.  it's a video driver config issue.

still need your /var/log/Xorg.0.log file to troubleshoot.

---

### Post by codyxx on 2009-03-14
Okay, no problem.

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux cody-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 07 March 2009  02:18:57AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.127934] (--) probed, [    0.127962] (**) from config file, [    0.127981] (==) default setting,
	[    0.127999] (++) from command line, [    0.128018] (!!) notice, [    0.128036] (II) informational,
	[    0.128055] (WW) warning, [    0.128073] (EE) error, [    0.128091] (NI) not implemented, [    0.128110] (??) unknown.
[    0.128248] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 14 13:10:42 2009
[    0.135801] (==) Using config file: "/etc/X11/xorg.conf"
[    0.135979] (==) No Layout section.  Using the first Screen section.
[    0.136951] (**) |-->Screen "Default Screen" (0)
[    0.136985] (**) |   |-->Monitor "Configured Monitor"
[    0.137428] (**) |   |-->Device "Configured Video Device"
[    0.137480] (==) Automatically adding devices
[    0.137496] (==) Automatically enabling devices
[    0.219755] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.496189] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.496234] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.496251] (II) Cannot locate a core pointer device.
[    0.496265] (II) Cannot locate a core keyboard device.
[    0.496278] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.496310] (II) Loader magic: 0x3bc0
[    0.496325] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.496377] (II) Loader running on linux
[    0.496399] (++) using VT number 7

[    0.625700] (--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[    0.625835] (--) PCI: (0@0:2:1) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfeb00000/1048576
[    0.626031] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.626085] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.626353] (II) LoadModule: "extmod"
[    0.639263] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.639580] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.639643] (II) Loading extension MIT-SCREEN-SAVER
[    0.639658] (II) Loading extension XFree86-VidModeExtension
[    0.639672] (II) Loading extension XFree86-DGA
[    0.639690] (II) Loading extension DPMS
[    0.639704] (II) Loading extension XVideo
[    0.639721] (II) Loading extension XVideo-MotionCompensation
[    0.639735] (II) Loading extension X-Resource
[    0.639750] (II) LoadModule: "dbe"
[    0.640343] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.640528] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.640590] (II) Loading extension DOUBLE-BUFFER
[    0.640606] (II) LoadModule: "glx"
[    0.641160] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
[    0.641468] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.641491] (II) UnloadModule: "glx"
[    0.641505] (EE) Failed to load module "glx" (loader failed, 7)
[    0.641528] (II) LoadModule: "record"
[    0.642114] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.642278] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.642339] (II) Loading extension RECORD
[    0.642355] (II) LoadModule: "dri"
[    0.642917] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.677580] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
[    0.677648] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.677672] (II) UnloadModule: "dri"
[    0.677686] (II) Unloading /usr/lib/xorg/modules/extensions//libdri.so
[    0.677705] (EE) Failed to load module "dri" (module requirement mismatch, 0)
[    0.677730] (II) LoadModule: "dri2"
[    0.678329] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.686724] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.686789] (II) Loading extension DRI2
[    0.686848] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.701565] (II) Matched intel from file name intel.ids
[    0.701632] (==) Matched intel for the autoconfigured driver
[    0.701650] (==) Assigned the driver to the xf86ConfigLayout
[    0.701666] (II) LoadModule: "intel"
[    0.702009] (II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
[    0.741525] (II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 2.6.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.741631] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile IntelÂ® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
[    0.743686] (II) Primary Device is: PCI 00@00:02:0
[    0.785239] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.786048] (II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
[    0.817982] (II) Loading sub module "vgahw"
[    0.818010] (II) LoadModule: "vgahw"
[    0.818103] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.818237] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.818296] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.818308] (==) intel(0): Depth 24, [    0.818316] (--) framebuffer bpp 32
[    0.818325] (==) intel(0): RGB weight 888
[    0.818336] (==) intel(0): Default visual is TrueColor
[    0.818371] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    0.818401] (--) intel(0): Chipset: "965GM"
[    0.818410] (--) intel(0): Linear framebuffer at 0xE0000000
[    0.818418] (--) intel(0): IO registers at addr 0xFEA00000
[    0.818429] (WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
[    0.819102] (==) intel(0): Using EXA for acceleration
[    0.819203] (II) intel(0): 2 display pipes available.
[    0.819215] (II) Loading sub module "ddc"
[    0.819223] (II) LoadModule: "ddc"
[    0.819241] (II) Module "ddc" already built-in
[    0.819248] (II) Loading sub module "i2c"
[    0.819255] (II) LoadModule: "i2c"
[    0.819268] (II) Module "i2c" already built-in
[    0.875015] (II) intel(0): Output VGA using monitor section Configured Monitor
[    0.875054] (II) intel(0): Output LVDS has no monitor section
[    0.893845] (II) intel(0): I2C bus "LVDSDDC_C" initialized.
[    0.893860] (II) intel(0): Attempting to determine panel fixed mode.
[    0.893881] (II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
[    0.893892] (II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
[    0.952488] (II) intel(0): EDID vendor "CPT", prod id 5151
[    0.952606] (II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
[    0.957530] (II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
[    0.957573] (II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
[    1.114893] (II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
[    1.165629] (II) intel(0): Output TMDS-1 has no monitor section
[    1.186609] (II) intel(0): SDVOB: device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz
[    1.186659] (II) intel(0): SDVOB: 1 input channel
[    1.186669] (II) intel(0): SDVOB: TMDS0 output reported
[    1.186687] (II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
[    1.186696] (II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
[    1.187454] (II) intel(0): No SDVO device found on SDVOC
[    1.187474] (II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
[    1.187484] (II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
[    1.187511] (II) intel(0): Output TV has no monitor section
[    1.203290] (II) intel(0): Current clock rate multiplier: 1
[    1.399489] (II) intel(0): EDID for output VGA
[    1.452685] (II) intel(0): EDID for output LVDS
[    1.452713] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[    1.452723] (II) intel(0): Year: 2008  Week: 41
[    1.452731] (II) intel(0): EDID Version: 1.3
[    1.452738] (II) intel(0): Digital Display Input
[    1.452746] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    1.452763] (II) intel(0): Gamma: 2.20
[    1.452775] (II) intel(0): No DPMS capabilities specified
[    1.452787] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    1.452795] (II) intel(0): First detailed timing is preferred mode
[    1.452803] (II) intel(0): GTF timings supported
[    1.452811] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[    1.452827] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[    1.452841] (II) intel(0): Manufacturer's mask: 0
[    1.452849] (II) intel(0): Supported additional Video Mode:
[    1.452857] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    1.452872] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[    1.452885] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[    1.452898] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[    1.452911] (II) intel(0):  C285J€154WB8
[    1.452919] (II) intel(0):  '6AGd‚«ÿ
[    1.452926] (II) intel(0): EDID (in hex):
[    1.452938] (II) intel(0): 	00ffffffffffff000e141f1400000000
[    1.452949] (II) intel(0): 	29120103802115780a092d9d564f9027
[    1.452960] (II) intel(0): 	21505400000001010101010101010101
[    1.452971] (II) intel(0): 	010101010101bc1b00aa502010303020
[    1.452982] (II) intel(0): 	36004bcf100000190000000f00000000
[    1.453014] (II) intel(0): 	0000000000206e050f00000000fe0043
[    1.453026] (II) intel(0): 	3238354a8031353457423820000000fe
[    1.453036] (II) intel(0): 	00273641476482abff01012020200081
[    1.453045] (II) intel(0): EDID vendor "CPT", prod id 5151
[    1.453137] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453148] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    1.453156] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    1.453165] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    1.453173] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    1.453181] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    1.453189] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    1.453197] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    1.453204] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    1.453212] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    1.453220] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    1.453228] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    1.453236] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    1.453244] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    1.453252] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    1.453260] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    1.453268] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    1.453276] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453284] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453325] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453334] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453342] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453350] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    1.453358] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    1.453367] (II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
[    1.453375] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    1.453383] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    1.453391] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    1.453399] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    1.453407] (II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
[    1.453415] (II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
[    1.453423] (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    1.453431] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    1.453439] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    1.453447] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    1.453454] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    1.453462] (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    1.453470] (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
[    1.453478] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    1.453486] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    1.453494] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    1.453515] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    1.453526] (II) intel(0): Printing probed modes for output LVDS
[    1.453538] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[    1.453555] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    1.453570] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    1.453584] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    1.453598] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    1.453611] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    1.453625] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    1.453638] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    1.453652] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    1.453665] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    1.453678] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    1.453692] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    1.453705] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    1.453718] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    1.453731] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    1.453745] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    1.453758] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    1.453771] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    1.462423] (II) intel(0): EDID for output TMDS-1
[    4.252832] (II) intel(0): EDID for output TV
[    4.252892] (II) intel(0): Output VGA disconnected
[    4.252910] (II) intel(0): Output LVDS connected
[    4.252926] (II) intel(0): Output TMDS-1 disconnected
[    4.252940] (II) intel(0): Output TV disconnected
[    4.253013] (II) intel(0): Using exact sizes for initial modes
[    4.253028] (II) intel(0): Output LVDS using initial mode 1280x800
[    5.194573] (II) intel(0): detected 512 kB GTT.
[    5.194603] (II) intel(0): detected 7676 kB stolen memory.
[    5.194615] (==) intel(0): video overlay key set to 0x101fe
[    5.194626] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    5.194643] (==) intel(0): DPI set to (96, 96)
[    5.194651] (II) Loading sub module "fb"
[    5.194659] (II) LoadModule: "fb"
[    5.194762] (II) Loading /usr/lib/xorg/modules//libfb.so
[    5.194922] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    5.194952] (II) Loading sub module "exa"
[    5.194960] (II) LoadModule: "exa"
[    5.195039] (II) Loading /usr/lib/xorg/modules//libexa.so
[    5.221893] (II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
[    5.221932] (II) Loading sub module "ramdac"
[    5.221940] (II) LoadModule: "ramdac"
[    5.221958] (II) Module "ramdac" already built-in
[    5.221971] (II) intel(0): Comparing regs from server start up to After PreInit
[    5.221990] (WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
[    5.222006] (WW) intel(0): PP_STATUS before: on, ready, sequencing idle
[    5.222033] (WW) intel(0): PP_STATUS after: on, ready, sequencing on
[    5.222045] (WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000203 to 0x00000207
[    5.222063] (WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
[    5.222071] (WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
[    5.222088] (WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x100000c0 to 0x000c00c0
[    5.222097] (WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
[    5.222106] (WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
[    5.222115] (WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
[    5.222123] (WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
[    5.222132] (WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
[    5.222141] (WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
[    5.222150] (WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00404000
[    5.222158] (WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
[    5.222167] (WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
[    5.222176] (WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
[    5.222184] (WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
[    5.222193] (WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
[    5.222201] (WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
[    5.222210] (WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
[    5.222219] (WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
[    5.222227] (WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
[    5.222236] (WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
[    5.222244] (WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
[    5.222253] (WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710087
[    5.222261] (WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x6b405140
[    5.222270] (WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
[    5.222279] (WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
[    5.222287] (WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
[    5.222296] (WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
[    5.222305] (WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
[    5.222314] (WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
[    5.222322] (WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
[    5.222331] (WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
[    5.222340] (WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
[    5.244128] (==) Depth 24 pixmap format is 32 bpp
[    5.244147] (II) do I need RAC?  No, I don't.
[    5.244158] (II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[    5.244507] (II) intel(0): Kernel reported 746496 total, 1 used
[    5.244522] (II) intel(0): I830CheckAvailableMemory: 2985980 kB available
[    5.244533] (WW) intel(0): DRI2 requires UXA
[    5.244574] (EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
[    5.244597] (**) intel(0): Framebuffer compression disabled
[    5.244605] (**) intel(0): Tiling enabled
[    5.244659] (==) intel(0): VideoRam: 262144 KB
[    5.244670] (II) intel(0): Attempting memory allocation with tiled buffers.
[    5.303199] (II) intel(0): Tiled allocation successful.
[    5.304264] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    5.305056] (II) EXA(0): Offscreen pixmap area of 19660800 bytes
[    5.305080] (II) EXA(0): Driver registered support for the following operations:
[    5.305091] (II)         Solid
[    5.305098] (II)         Copy
[    5.305105] (II)         Composite (RENDER acceleration)
[    5.305117] (==) intel(0): Backing store disabled
[    5.305128] (==) intel(0): Silken mouse enabled
[    5.305771] (II) intel(0): Initializing HW Cursor
[    5.313900] (II) intel(0): Current clock rate multiplier: 1
[    5.483411] (II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
[    5.483721] (II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00840000 (pgoffset 2112)
[    5.484175] (II) intel(0): Fixed memory allocation layout:
[    5.484207] (II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
[    5.484217] (II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
[    5.484226] (II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
[    5.484235] (II) intel(0): 0x00032000-0x00131fff: fake bufmgr (1024 kB)
[    5.484244] (II) intel(0): 0x00132000-0x00140fff: exa G965 state buffer (60 kB)
[    5.484253] (II) intel(0): 0x00141000-0x00141fff: overlay registers (4 kB)
[    5.484262] (II) intel(0): 0x00142000-0x00142fff: power context (4 kB)
[    5.484271] (II) intel(0): 0x00200000-0x0083ffff: front buffer (6400 kB) X tiled
[    5.484280] (II) intel(0): 0x0077f000:            end of stolen memory
[    5.484289] (II) intel(0): 0x00840000-0x01afffff: exa offscreen (19200 kB)
[    5.484298] (II) intel(0): 0x10000000:            end of aperture
[    6.026433] (II) intel(0): using SSC reference clock of 100 MHz
[    6.027013] (II) intel(0): Selecting standard 18 bit TMDS pixel format.
[    6.599959] (II) intel(0): Output configuration:
[    6.600211] (II) intel(0):   Pipe A is off
[    6.600234] (II) intel(0):   Display plane A is now disabled and connected to pipe A.
[    6.600248] (II) intel(0):   Pipe B is on
[    6.600260] (II) intel(0):   Display plane B is now enabled and connected to pipe B.
[    6.600272] (II) intel(0):   Output VGA is connected to pipe none
[    6.600283] (II) intel(0):   Output LVDS is connected to pipe B
[    6.600295] (II) intel(0):   Output TMDS-1 is connected to pipe none
[    6.600306] (II) intel(0):   Output TV is connected to pipe none
[    6.600325] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    6.616681] (II) intel(0): DPMS enabled
[    6.616707] (==) intel(0): Intel XvMC decoder disabled
[    6.616748] (II) intel(0): Set up textured video
[    6.616789] (II) intel(0): Set up overlay video
[    6.616853] (II) intel(0): direct rendering: Failed
[    6.616872] (--) RandR disabled
[    6.647482] (II) Initializing built-in extension Generic Event Extension
[    6.647506] (II) Initializing built-in extension SHAPE
[    6.647517] (II) Initializing built-in extension MIT-SHM
[    6.647528] (II) Initializing built-in extension XInputExtension
[    6.647538] (II) Initializing built-in extension XTEST
[    6.647548] (II) Initializing built-in extension BIG-REQUESTS
[    6.647559] (II) Initializing built-in extension SYNC
[    6.647569] (II) Initializing built-in extension XKEYBOARD
[    6.647579] (II) Initializing built-in extension XC-MISC
[    6.647589] (II) Initializing built-in extension SECURITY
[    6.647599] (II) Initializing built-in extension XINERAMA
[    6.647609] (II) Initializing built-in extension XFIXES
[    6.647646] (II) Initializing built-in extension RENDER
[    6.647658] (II) Initializing built-in extension RANDR
[    6.647668] (II) Initializing built-in extension COMPOSITE
[    6.647678] (II) Initializing built-in extension DAMAGE
[    6.663901] (II) intel(0): Setting screen physical size to 331 x 207
[    7.243462] (II) config/hal: Adding input device AT Translated Set 2 keyboard
[    7.243511] (II) LoadModule: "evdev"
[    7.243676] (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[    7.269893] (II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
[    7.269963] (**) AT Translated Set 2 keyboard: always reports core events
[    7.269977] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    7.270048] (II) AT Translated Set 2 keyboard: Found keys
[    7.270058] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    7.270085] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    7.270106] (**) Option "xkb_rules" "evdev"
[    7.270122] (**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
[    7.270131] (**) Option "xkb_model" "pc105"
[    7.270146] (**) AT Translated Set 2 keyboard: xkb_model: "pc105"
[    7.270154] (**) Option "xkb_layout" "us"
[    7.270169] (**) AT Translated Set 2 keyboard: xkb_layout: "us"
[    7.372332] (II) config/hal: Adding input device Video Bus
[    7.372432] (**) Video Bus: always reports core events
[    7.372446] (**) Video Bus: Device: "/dev/input/event6"
[    7.375512] (II) Video Bus: Found keys
[    7.375523] (II) Video Bus: Configuring as keyboard
[    7.375546] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    7.375563] (**) Option "xkb_rules" "evdev"
[    7.375580] (**) Video Bus: xkb_rules: "evdev"
[    7.375587] (**) Option "xkb_model" "pc105"
[    7.375602] (**) Video Bus: xkb_model: "pc105"
[    7.375610] (**) Option "xkb_layout" "us"
[    7.375626] (**) Video Bus: xkb_layout: "us"
[    7.439669] (II) config/hal: Adding input device Video Bus
[    7.439735] (**) Video Bus: always reports core events
[    7.439748] (**) Video Bus: Device: "/dev/input/event7"
[    7.443496] (II) Video Bus: Found keys
[    7.443508] (II) Video Bus: Configuring as keyboard
[    7.443531] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    7.443547] (**) Option "xkb_rules" "evdev"
[    7.443563] (**) Video Bus: xkb_rules: "evdev"
[    7.443572] (**) Option "xkb_model" "pc105"
[    7.443586] (**) Video Bus: xkb_model: "pc105"
[    7.443594] (**) Option "xkb_layout" "us"
[    7.443609] (**) Video Bus: xkb_layout: "us"
[    7.506212] (II) config/hal: Adding input device Macintosh mouse button emulation
[    7.506275] (**) Macintosh mouse button emulation: always reports core events
[    7.506288] (**) Macintosh mouse button emulation: Device: "/dev/input/event0"
[    7.508514] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[    7.508527] (II) Macintosh mouse button emulation: Found x and y relative axes
[    7.508535] (II) Macintosh mouse button emulation: Configuring as mouse
[    7.508556] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    7.508566] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    7.508587] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    7.508624] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    7.508634] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[    7.508647] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[    7.508663] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[    7.510892] (II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
[    7.510929] (II) LoadModule: "synaptics"
[    7.511108] (II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
[    7.533079] (II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
[    7.533141] (II) Synaptics touchpad driver version 0.99.3
[    7.533165] (**) Option "Device" "/dev/input/event9"
[    7.533241] (II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    7.533253] (II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    7.533262] (II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    7.533271] (II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
[    7.533281] (II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    7.533296] (II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
[    7.533333] (--) AlpsPS/2 ALPS GlidePoint touchpad found
[    7.533346] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    7.533418] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    7.533456] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    7.533467] (**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
[    7.533480] (**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
[    7.533495] (**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
[    7.533688] (--) AlpsPS/2 ALPS GlidePoint touchpad found
[    7.535351] (II) config/hal: Adding input device PS/2 Mouse
[    7.535402] (**) PS/2 Mouse: always reports core events
[    7.535415] (**) PS/2 Mouse: Device: "/dev/input/event8"
[    7.536496] (II) PS/2 Mouse: Found 3 mouse buttons
[    7.536513] (II) PS/2 Mouse: Found x and y relative axes
[    7.536524] (II) PS/2 Mouse: Configuring as mouse
[    7.536545] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    7.536560] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    7.536584] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    7.536624] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    7.536638] (**) PS/2 Mouse: (accel) filter chain progression: 2.00
[    7.536654] (**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
[    7.536676] (**) PS/2 Mouse: (accel) set acceleration profile 0
[    8.214413] (II) intel(0): EDID for output VGA
[    8.269256] (II) intel(0): EDID for output LVDS
[    8.269284] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[    8.269304] (II) intel(0): Year: 2008  Week: 41
[    8.269319] (II) intel(0): EDID Version: 1.3
[    8.269333] (II) intel(0): Digital Display Input
[    8.269347] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    8.269378] (II) intel(0): Gamma: 2.20
[    8.269398] (II) intel(0): No DPMS capabilities specified
[    8.269420] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    8.269436] (II) intel(0): First detailed timing is preferred mode
[    8.269451] (II) intel(0): GTF timings supported
[    8.269464] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[    8.269494] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[    8.269523] (II) intel(0): Manufacturer's mask: 0
[    8.269538] (II) intel(0): Supported additional Video Mode:
[    8.269552] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    8.269580] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[    8.269605] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[    8.269630] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[    8.269654] (II) intel(0):  C285J€154WB8
[    8.269668] (II) intel(0):  '6AGd‚«ÿ
[    8.269682] (II) intel(0): EDID (in hex):
[    8.269704] (II) intel(0): 	00ffffffffffff000e141f1400000000
[    8.269725] (II) intel(0): 	29120103802115780a092d9d564f9027
[    8.269746] (II) intel(0): 	21505400000001010101010101010101
[    8.269766] (II) intel(0): 	010101010101bc1b00aa502010303020
[    8.269787] (II) intel(0): 	36004bcf100000190000000f00000000
[    8.269808] (II) intel(0): 	0000000000206e050f00000000fe0043
[    8.269858] (II) intel(0): 	3238354a8031353457423820000000fe
[    8.269879] (II) intel(0): 	00273641476482abff01012020200081
[    8.269899] (II) intel(0): EDID vendor "CPT", prod id 5151
[    8.269921] (II) intel(0): Using EDID range info for horizontal sync
[    8.269937] (II) intel(0): Using EDID range info for vertical refresh
[    8.269951] (II) intel(0): Printing DDC gathered Modelines:
[    8.269968] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[    8.270009] (II) intel(0): EDID vendor "CPT", prod id 5151
[    8.270180] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270199] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    8.270214] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    8.270229] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    8.270244] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    8.270259] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    8.270274] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    8.270289] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    8.270303] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    8.270318] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    8.270333] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    8.270347] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[    8.270362] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[    8.270377] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[    8.270392] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[    8.270407] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[    8.270421] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[    8.270436] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270451] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270466] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270481] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270496] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270510] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    8.270525] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    8.270540] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    8.270555] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    8.270569] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    8.270584] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    8.270599] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    8.270614] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[    8.270628] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[    8.270643] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    8.270657] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    8.270672] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    8.270687] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    8.270702] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    8.270738] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[    8.270753] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[    8.270768] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[    8.270782] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[    8.270797] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[    8.270811] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[    8.270833] (II) intel(0): Printing probed modes for output LVDS
[    8.270853] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[    8.270883] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    8.270910] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    8.270937] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    8.270963] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    8.270989] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    8.271014] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    8.271040] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    8.271065] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    8.271090] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    8.271115] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    8.271140] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    8.271166] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    8.271191] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    8.271216] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    8.271241] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    8.271266] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    8.271292] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    8.280047] (II) intel(0): EDID for output TMDS-1
[    8.304033] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[    8.588705] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[    8.599378] (II) intel(0): EDID for output TV
[  130.468862] (II) intel(0): EDID for output VGA
[  130.523972] (II) intel(0): EDID for output LVDS
[  130.524001] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  130.524019] (II) intel(0): Year: 2008  Week: 41
[  130.524034] (II) intel(0): EDID Version: 1.3
[  130.524049] (II) intel(0): Digital Display Input
[  130.524063] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  130.524093] (II) intel(0): Gamma: 2.20
[  130.524114] (II) intel(0): No DPMS capabilities specified
[  130.524136] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  130.524151] (II) intel(0): First detailed timing is preferred mode
[  130.524166] (II) intel(0): GTF timings supported
[  130.524179] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  130.524210] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  130.524238] (II) intel(0): Manufacturer's mask: 0
[  130.524291] (II) intel(0): Supported additional Video Mode:
[  130.524306] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  130.524334] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  130.524359] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  130.524384] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  130.524408] (II) intel(0):  C285J€154WB8
[  130.524421] (II) intel(0):  '6AGd‚«ÿ
[  130.524451] (II) intel(0): EDID (in hex):
[  130.524473] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  130.524497] (II) intel(0): 	29120103802115780a092d9d564f9027
[  130.524518] (II) intel(0): 	21505400000001010101010101010101
[  130.524539] (II) intel(0): 	010101010101bc1b00aa502010303020
[  130.524567] (II) intel(0): 	36004bcf100000190000000f00000000
[  130.524588] (II) intel(0): 	0000000000206e050f00000000fe0043
[  130.524608] (II) intel(0): 	3238354a8031353457423820000000fe
[  130.524629] (II) intel(0): 	00273641476482abff01012020200081
[  130.524645] (II) intel(0): EDID vendor "CPT", prod id 5151
[  130.524667] (II) intel(0): Using hsync ranges from config file
[  130.524682] (II) intel(0): Using vrefresh ranges from config file
[  130.524696] (II) intel(0): Printing DDC gathered Modelines:
[  130.524714] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  130.524753] (II) intel(0): EDID vendor "CPT", prod id 5151
[  130.524910] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.524928] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  130.524943] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  130.524958] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.524973] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.524988] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.525003] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.525018] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.525032] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.525047] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.525062] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.525076] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  130.525091] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  130.525106] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  130.525120] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  130.525135] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.525150] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.525164] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525179] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525194] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525209] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525223] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525238] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.525252] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  130.525267] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  130.525282] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.525297] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.525347] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.525364] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.525378] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  130.525393] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  130.525407] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.525422] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.525436] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.525451] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.525465] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.525480] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  130.525494] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  130.525508] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.525523] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.525538] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.525552] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.525571] (II) intel(0): Printing probed modes for output LVDS
[  130.525589] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  130.525619] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  130.525646] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  130.525673] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  130.525699] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  130.525724] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  130.525750] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  130.525775] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  130.525800] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  130.525825] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  130.525850] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  130.525875] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  130.525900] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  130.525925] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  130.525949] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  130.525974] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  130.525999] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  130.526024] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  130.534830] (II) intel(0): EDID for output TMDS-1
[  130.558752] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  130.710296] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  130.721615] (II) intel(0): EDID for output TV
[  130.746493] (II) intel(0): EDID for output VGA
[  130.802189] (II) intel(0): EDID for output LVDS
[  130.802221] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  130.802239] (II) intel(0): Year: 2008  Week: 41
[  130.802254] (II) intel(0): EDID Version: 1.3
[  130.802268] (II) intel(0): Digital Display Input
[  130.802283] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  130.802314] (II) intel(0): Gamma: 2.20
[  130.802335] (II) intel(0): No DPMS capabilities specified
[  130.802357] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  130.802372] (II) intel(0): First detailed timing is preferred mode
[  130.802386] (II) intel(0): GTF timings supported
[  130.802400] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  130.802431] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  130.802459] (II) intel(0): Manufacturer's mask: 0
[  130.802474] (II) intel(0): Supported additional Video Mode:
[  130.802488] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  130.802516] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  130.802542] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  130.802566] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  130.802590] (II) intel(0):  C285J€154WB8
[  130.802604] (II) intel(0):  '6AGd‚«ÿ
[  130.802618] (II) intel(0): EDID (in hex):
[  130.802641] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  130.802662] (II) intel(0): 	29120103802115780a092d9d564f9027
[  130.802682] (II) intel(0): 	21505400000001010101010101010101
[  130.802703] (II) intel(0): 	010101010101bc1b00aa502010303020
[  130.802731] (II) intel(0): 	36004bcf100000190000000f00000000
[  130.802752] (II) intel(0): 	0000000000206e050f00000000fe0043
[  130.802772] (II) intel(0): 	3238354a8031353457423820000000fe
[  130.802792] (II) intel(0): 	00273641476482abff01012020200081
[  130.802808] (II) intel(0): EDID vendor "CPT", prod id 5151
[  130.802830] (II) intel(0): Using hsync ranges from config file
[  130.802845] (II) intel(0): Using vrefresh ranges from config file
[  130.802859] (II) intel(0): Printing DDC gathered Modelines:
[  130.802877] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  130.802916] (II) intel(0): EDID vendor "CPT", prod id 5151
[  130.803071] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803090] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  130.803105] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  130.803120] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.803134] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.803149] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  130.803164] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.803179] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.803194] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.803209] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.803224] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  130.803238] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  130.803253] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  130.803268] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  130.803283] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  130.803297] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.803312] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.803327] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803374] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803390] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803404] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803419] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803451] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  130.803466] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  130.803480] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  130.803495] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.803509] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.803524] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.803538] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  130.803553] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  130.803567] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  130.803582] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.803597] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.803611] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.803625] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.803640] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  130.803654] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  130.803669] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  130.803683] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  130.803698] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.803712] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.803727] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  130.803746] (II) intel(0): Printing probed modes for output LVDS
[  130.803764] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  130.803795] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  130.803822] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  130.803848] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  130.803874] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  130.803899] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  130.803925] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  130.803950] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  130.803975] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  130.804000] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  130.804025] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  130.804049] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  130.804074] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  130.804099] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  130.804146] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  130.804172] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  130.804197] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  130.804222] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  130.812817] (II) intel(0): EDID for output TMDS-1
[  130.825851] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  131.020773] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  131.031720] (II) intel(0): EDID for output TV
[  131.040128] (II) intel(0): EDID for output VGA
[  131.097400] (II) intel(0): EDID for output LVDS
[  131.097444] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  131.097462] (II) intel(0): Year: 2008  Week: 41
[  131.097478] (II) intel(0): EDID Version: 1.3
[  131.097493] (II) intel(0): Digital Display Input
[  131.097507] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  131.097538] (II) intel(0): Gamma: 2.20
[  131.097559] (II) intel(0): No DPMS capabilities specified
[  131.097581] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  131.097596] (II) intel(0): First detailed timing is preferred mode
[  131.097610] (II) intel(0): GTF timings supported
[  131.097624] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  131.097654] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  131.097682] (II) intel(0): Manufacturer's mask: 0
[  131.097697] (II) intel(0): Supported additional Video Mode:
[  131.097711] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  131.097739] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  131.097763] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  131.097788] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  131.097812] (II) intel(0):  C285J€154WB8
[  131.097826] (II) intel(0):  '6AGd‚«ÿ
[  131.097840] (II) intel(0): EDID (in hex):
[  131.097862] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  131.097883] (II) intel(0): 	29120103802115780a092d9d564f9027
[  131.097904] (II) intel(0): 	21505400000001010101010101010101
[  131.097925] (II) intel(0): 	010101010101bc1b00aa502010303020
[  131.097945] (II) intel(0): 	36004bcf100000190000000f00000000
[  131.097966] (II) intel(0): 	0000000000206e050f00000000fe0043
[  131.097986] (II) intel(0): 	3238354a8031353457423820000000fe
[  131.098006] (II) intel(0): 	00273641476482abff01012020200081
[  131.098023] (II) intel(0): EDID vendor "CPT", prod id 5151
[  131.098045] (II) intel(0): Using hsync ranges from config file
[  131.098060] (II) intel(0): Using vrefresh ranges from config file
[  131.098074] (II) intel(0): Printing DDC gathered Modelines:
[  131.098092] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  131.098132] (II) intel(0): EDID vendor "CPT", prod id 5151
[  131.098290] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098308] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  131.098323] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  131.098338] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  131.098353] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  131.098367] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  131.098382] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  131.098397] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  131.098411] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  131.098462] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  131.098478] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  131.098492] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  131.098507] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  131.098522] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  131.098536] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  131.098550] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  131.098565] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  131.098580] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098594] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098609] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098624] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098638] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098652] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  131.098667] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  131.098681] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  131.098696] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  131.098710] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  131.098725] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  131.098739] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  131.098754] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  131.098768] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  131.098783] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  131.098797] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  131.098812] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  131.098826] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  131.098841] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  131.098855] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  131.098870] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  131.098884] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  131.098899] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  131.098913] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  131.098928] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  131.098947] (II) intel(0): Printing probed modes for output LVDS
[  131.098964] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  131.098994] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  131.099021] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  131.099047] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  131.099073] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  131.099099] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  131.099147] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  131.099173] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  131.099198] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  131.099223] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  131.099247] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  131.099272] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  131.099297] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  131.099323] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  131.099347] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  131.099373] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  131.099398] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  131.099422] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  131.110400] (II) intel(0): EDID for output TMDS-1
[  131.127514] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  131.327923] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  131.338818] (II) intel(0): EDID for output TV
[  138.119482] (II) intel(0): EDID for output VGA
[  138.174327] (II) intel(0): EDID for output LVDS
[  138.174352] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  138.174362] (II) intel(0): Year: 2008  Week: 41
[  138.174371] (II) intel(0): EDID Version: 1.3
[  138.174378] (II) intel(0): Digital Display Input
[  138.174387] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  138.174403] (II) intel(0): Gamma: 2.20
[  138.174417] (II) intel(0): No DPMS capabilities specified
[  138.174428] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  138.174437] (II) intel(0): First detailed timing is preferred mode
[  138.174446] (II) intel(0): GTF timings supported
[  138.174453] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  138.174469] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  138.174484] (II) intel(0): Manufacturer's mask: 0
[  138.174493] (II) intel(0): Supported additional Video Mode:
[  138.174501] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  138.174515] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  138.174529] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  138.174542] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  138.174555] (II) intel(0):  C285J€154WB8
[  138.174563] (II) intel(0):  '6AGd‚«ÿ
[  138.174571] (II) intel(0): EDID (in hex):
[  138.174582] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  138.174593] (II) intel(0): 	29120103802115780a092d9d564f9027
[  138.174605] (II) intel(0): 	21505400000001010101010101010101
[  138.174615] (II) intel(0): 	010101010101bc1b00aa502010303020
[  138.174626] (II) intel(0): 	36004bcf100000190000000f00000000
[  138.174637] (II) intel(0): 	0000000000206e050f00000000fe0043
[  138.174648] (II) intel(0): 	3238354a8031353457423820000000fe
[  138.174659] (II) intel(0): 	00273641476482abff01012020200081
[  138.174667] (II) intel(0): EDID vendor "CPT", prod id 5151
[  138.174679] (II) intel(0): Using hsync ranges from config file
[  138.174687] (II) intel(0): Using vrefresh ranges from config file
[  138.174696] (II) intel(0): Printing DDC gathered Modelines:
[  138.174705] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  138.174754] (II) intel(0): EDID vendor "CPT", prod id 5151
[  138.174837] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.174847] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  138.174856] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  138.174864] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.174872] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.174880] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.174888] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.174897] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.174905] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.174913] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.174921] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.174929] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  138.174937] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  138.174945] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  138.174953] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  138.174961] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.174969] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.174977] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.174985] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.174993] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.175001] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.175010] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.175018] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.175026] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  138.175034] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  138.175042] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.175050] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.175058] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.175066] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.175074] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  138.175082] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  138.175090] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.175098] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.175106] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.175114] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.175122] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.175130] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  138.175138] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  138.175146] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.175154] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.175162] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.175183] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.175194] (II) intel(0): Printing probed modes for output LVDS
[  138.175207] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  138.175223] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  138.175237] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  138.175251] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  138.175265] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  138.175278] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  138.175292] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  138.175306] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  138.175319] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  138.175332] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  138.175345] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  138.175358] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  138.175372] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  138.175385] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  138.175398] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  138.175411] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  138.175424] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  138.175438] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  138.183817] (II) intel(0): EDID for output TMDS-1
[  138.200222] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  138.473740] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  138.483472] (II) intel(0): EDID for output TV
[  138.535777] (II) intel(0): EDID for output VGA
[  138.599669] (II) intel(0): EDID for output LVDS
[  138.599699] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  138.599710] (II) intel(0): Year: 2008  Week: 41
[  138.599718] (II) intel(0): EDID Version: 1.3
[  138.599726] (II) intel(0): Digital Display Input
[  138.599734] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  138.599750] (II) intel(0): Gamma: 2.20
[  138.599763] (II) intel(0): No DPMS capabilities specified
[  138.599775] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  138.599783] (II) intel(0): First detailed timing is preferred mode
[  138.599791] (II) intel(0): GTF timings supported
[  138.599799] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  138.599814] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  138.599829] (II) intel(0): Manufacturer's mask: 0
[  138.599837] (II) intel(0): Supported additional Video Mode:
[  138.599845] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  138.599859] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  138.599873] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  138.599886] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  138.599899] (II) intel(0):  C285J€154WB8
[  138.599907] (II) intel(0):  '6AGd‚«ÿ
[  138.599914] (II) intel(0): EDID (in hex):
[  138.599945] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  138.599957] (II) intel(0): 	29120103802115780a092d9d564f9027
[  138.599968] (II) intel(0): 	21505400000001010101010101010101
[  138.599978] (II) intel(0): 	010101010101bc1b00aa502010303020
[  138.599989] (II) intel(0): 	36004bcf100000190000000f00000000
[  138.600000] (II) intel(0): 	0000000000206e050f00000000fe0043
[  138.600010] (II) intel(0): 	3238354a8031353457423820000000fe
[  138.600021] (II) intel(0): 	00273641476482abff01012020200081
[  138.600030] (II) intel(0): EDID vendor "CPT", prod id 5151
[  138.600041] (II) intel(0): Using hsync ranges from config file
[  138.600049] (II) intel(0): Using vrefresh ranges from config file
[  138.600057] (II) intel(0): Printing DDC gathered Modelines:
[  138.600067] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  138.600091] (II) intel(0): EDID vendor "CPT", prod id 5151
[  138.600178] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600188] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  138.600196] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  138.600204] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.600213] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.600221] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  138.600229] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.600237] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.600245] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.600253] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.600261] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  138.600269] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  138.600277] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  138.600285] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  138.600293] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  138.600301] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.600309] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.600317] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600325] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600333] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600342] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600350] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600358] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  138.600365] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  138.600373] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  138.600381] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.600389] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.600397] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.600405] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  138.600413] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  138.600421] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  138.600442] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.600450] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.600469] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.600478] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.600485] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  138.600493] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  138.600501] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  138.600509] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  138.600517] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.600525] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.600533] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  138.600544] (II) intel(0): Printing probed modes for output LVDS
[  138.600555] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  138.600571] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  138.600585] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  138.600599] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  138.600613] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  138.600626] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  138.600640] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  138.600653] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  138.600667] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  138.600680] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  138.600693] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  138.600706] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  138.600720] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  138.600733] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  138.600746] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  138.600760] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  138.600773] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  138.600786] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  138.609142] (II) intel(0): EDID for output TMDS-1
[  138.621460] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  138.906764] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  138.913084] (II) intel(0): EDID for output TV
[  139.319303] (II) intel(0): EDID for output VGA
[  139.380106] (II) intel(0): EDID for output LVDS
[  139.380136] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  139.380147] (II) intel(0): Year: 2008  Week: 41
[  139.380155] (II) intel(0): EDID Version: 1.3
[  139.380163] (II) intel(0): Digital Display Input
[  139.380171] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  139.380187] (II) intel(0): Gamma: 2.20
[  139.380200] (II) intel(0): No DPMS capabilities specified
[  139.380211] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  139.380239] (II) intel(0): First detailed timing is preferred mode
[  139.380247] (II) intel(0): GTF timings supported
[  139.380255] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  139.380271] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  139.380285] (II) intel(0): Manufacturer's mask: 0
[  139.380294] (II) intel(0): Supported additional Video Mode:
[  139.380301] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  139.380316] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  139.380330] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  139.380343] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  139.380356] (II) intel(0):  C285J€154WB8
[  139.380364] (II) intel(0):  '6AGd‚«ÿ
[  139.380371] (II) intel(0): EDID (in hex):
[  139.380383] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  139.380394] (II) intel(0): 	29120103802115780a092d9d564f9027
[  139.380405] (II) intel(0): 	21505400000001010101010101010101
[  139.380416] (II) intel(0): 	010101010101bc1b00aa502010303020
[  139.380427] (II) intel(0): 	36004bcf100000190000000f00000000
[  139.380442] (II) intel(0): 	0000000000206e050f00000000fe0043
[  139.380453] (II) intel(0): 	3238354a8031353457423820000000fe
[  139.380463] (II) intel(0): 	00273641476482abff01012020200081
[  139.380472] (II) intel(0): EDID vendor "CPT", prod id 5151
[  139.380484] (II) intel(0): Using hsync ranges from config file
[  139.380492] (II) intel(0): Using vrefresh ranges from config file
[  139.380500] (II) intel(0): Printing DDC gathered Modelines:
[  139.380511] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  139.380534] (II) intel(0): EDID vendor "CPT", prod id 5151
[  139.380611] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380621] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  139.380629] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  139.380637] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.380645] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.380653] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.380662] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.380670] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.380678] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.380686] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.380694] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.380702] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  139.380710] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  139.380718] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  139.380726] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  139.380734] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.380742] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.380750] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380758] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380766] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380774] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380782] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380790] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.380798] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  139.380818] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  139.380826] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.380834] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.380842] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.380850] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.380858] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  139.380865] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  139.380873] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.380881] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.380889] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.380897] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.380905] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.380913] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  139.380921] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  139.380929] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.380937] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.380945] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.380952] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.380963] (II) intel(0): Printing probed modes for output LVDS
[  139.380973] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  139.380989] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  139.381003] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  139.381017] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  139.381030] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  139.381044] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  139.381057] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  139.381071] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  139.381084] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  139.381097] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  139.381110] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  139.381123] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  139.381136] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  139.381150] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  139.381163] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  139.381176] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  139.381189] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  139.381202] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  139.389630] (II) intel(0): EDID for output TMDS-1
[  139.406677] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  139.693626] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  139.704595] (II) intel(0): EDID for output TV
[  139.809958] (II) intel(0): EDID for output VGA
[  139.901669] (II) intel(0): EDID for output LVDS
[  139.901713] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  139.901732] (II) intel(0): Year: 2008  Week: 41
[  139.901747] (II) intel(0): EDID Version: 1.3
[  139.901761] (II) intel(0): Digital Display Input
[  139.901775] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  139.901804] (II) intel(0): Gamma: 2.20
[  139.901825] (II) intel(0): No DPMS capabilities specified
[  139.901846] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  139.901862] (II) intel(0): First detailed timing is preferred mode
[  139.901876] (II) intel(0): GTF timings supported
[  139.901889] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  139.901919] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  139.901947] (II) intel(0): Manufacturer's mask: 0
[  139.901962] (II) intel(0): Supported additional Video Mode:
[  139.901975] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  139.902003] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  139.902028] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  139.902053] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  139.902077] (II) intel(0):  C285J€154WB8
[  139.902091] (II) intel(0):  '6AGd‚«ÿ
[  139.902105] (II) intel(0): EDID (in hex):
[  139.902127] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  139.902147] (II) intel(0): 	29120103802115780a092d9d564f9027
[  139.902168] (II) intel(0): 	21505400000001010101010101010101
[  139.902189] (II) intel(0): 	010101010101bc1b00aa502010303020
[  139.902209] (II) intel(0): 	36004bcf100000190000000f00000000
[  139.902230] (II) intel(0): 	0000000000206e050f00000000fe0043
[  139.902250] (II) intel(0): 	3238354a8031353457423820000000fe
[  139.902270] (II) intel(0): 	00273641476482abff01012020200081
[  139.902285] (II) intel(0): EDID vendor "CPT", prod id 5151
[  139.902307] (II) intel(0): Using hsync ranges from config file
[  139.902322] (II) intel(0): Using vrefresh ranges from config file
[  139.902336] (II) intel(0): Printing DDC gathered Modelines:
[  139.902353] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  139.902395] (II) intel(0): EDID vendor "CPT", prod id 5151
[  139.902548] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902566] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  139.902581] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  139.902596] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.902610] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.902625] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  139.902639] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.902654] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.902668] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.902682] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.902696] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  139.902710] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  139.902725] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  139.902739] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  139.902787] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  139.902802] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.902816] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.902831] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902845] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902859] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902873] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902888] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902902] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  139.902916] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  139.902930] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  139.902945] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.902959] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.902973] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.902988] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  139.903002] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  139.903016] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  139.903030] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.903044] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.903059] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.903073] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.903087] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  139.903101] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  139.903115] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  139.903130] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  139.903144] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.903158] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.903173] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  139.903192] (II) intel(0): Printing probed modes for output LVDS
[  139.903211] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  139.903240] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  139.903267] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  139.903293] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  139.903319] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  139.903344] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  139.903370] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  139.903396] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  139.903421] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  139.903465] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  139.903492] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  139.903567] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  139.903595] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  139.903620] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  139.903644] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  139.903669] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  139.903694] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  139.903719] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  139.912444] (II) intel(0): EDID for output TMDS-1
[  139.927165] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  140.204223] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  140.216248] (II) intel(0): EDID for output TV
[  140.256352] (II) intel(0): EDID for output VGA
[  140.311999] (II) intel(0): EDID for output LVDS
[  140.312041] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  140.312061] (II) intel(0): Year: 2008  Week: 41
[  140.312076] (II) intel(0): EDID Version: 1.3
[  140.312090] (II) intel(0): Digital Display Input
[  140.312105] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  140.312135] (II) intel(0): Gamma: 2.20
[  140.312156] (II) intel(0): No DPMS capabilities specified
[  140.312178] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  140.312194] (II) intel(0): First detailed timing is preferred mode
[  140.312208] (II) intel(0): GTF timings supported
[  140.312222] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  140.312251] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  140.312279] (II) intel(0): Manufacturer's mask: 0
[  140.312294] (II) intel(0): Supported additional Video Mode:
[  140.312308] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  140.312336] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  140.312361] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  140.312386] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  140.312410] (II) intel(0):  C285J€154WB8
[  140.312424] (II) intel(0):  '6AGd‚«ÿ
[  140.312437] (II) intel(0): EDID (in hex):
[  140.312459] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  140.312480] (II) intel(0): 	29120103802115780a092d9d564f9027
[  140.312501] (II) intel(0): 	21505400000001010101010101010101
[  140.312522] (II) intel(0): 	010101010101bc1b00aa502010303020
[  140.312542] (II) intel(0): 	36004bcf100000190000000f00000000
[  140.312562] (II) intel(0): 	0000000000206e050f00000000fe0043
[  140.312582] (II) intel(0): 	3238354a8031353457423820000000fe
[  140.312601] (II) intel(0): 	00273641476482abff01012020200081
[  140.312617] (II) intel(0): EDID vendor "CPT", prod id 5151
[  140.312638] (II) intel(0): Using hsync ranges from config file
[  140.312653] (II) intel(0): Using vrefresh ranges from config file
[  140.312668] (II) intel(0): Printing DDC gathered Modelines:
[  140.312685] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  140.312725] (II) intel(0): EDID vendor "CPT", prod id 5151
[  140.312880] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.312900] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  140.312914] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  140.312929] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.312943] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.312997] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.313014] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.313029] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.313043] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.313058] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.313072] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.313086] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  140.313100] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  140.313115] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  140.313129] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  140.313143] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.313158] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.313172] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313186] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313201] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313215] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313230] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313244] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.313259] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  140.313273] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  140.313288] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.313302] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.313316] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.313331] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.313345] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  140.313359] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  140.313374] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.313388] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.313402] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.313417] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.313431] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.313445] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  140.313460] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  140.313474] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.313488] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.313502] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.313517] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.313543] (II) intel(0): Printing probed modes for output LVDS
[  140.313563] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  140.313596] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  140.313623] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  140.314899] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  140.314940] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  140.314967] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  140.314993] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  140.315019] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  140.315045] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  140.315070] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  140.315095] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  140.315120] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  140.315145] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  140.315171] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  140.315196] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  140.315221] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  140.315246] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  140.315271] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  140.324027] (II) intel(0): EDID for output TMDS-1
[  140.342461] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  140.650429] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  140.658470] (II) intel(0): EDID for output TV
[  140.714949] (II) intel(0): EDID for output VGA
[  140.769503] (II) intel(0): EDID for output LVDS
[  140.769532] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  140.769542] (II) intel(0): Year: 2008  Week: 41
[  140.769550] (II) intel(0): EDID Version: 1.3
[  140.769558] (II) intel(0): Digital Display Input
[  140.769566] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  140.769583] (II) intel(0): Gamma: 2.20
[  140.769595] (II) intel(0): No DPMS capabilities specified
[  140.769607] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  140.769615] (II) intel(0): First detailed timing is preferred mode
[  140.769623] (II) intel(0): GTF timings supported
[  140.769631] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  140.769647] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  140.769662] (II) intel(0): Manufacturer's mask: 0
[  140.769670] (II) intel(0): Supported additional Video Mode:
[  140.769678] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  140.769693] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  140.769706] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  140.769719] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  140.769732] (II) intel(0):  C285J€154WB8
[  140.769740] (II) intel(0):  '6AGd‚«ÿ
[  140.769747] (II) intel(0): EDID (in hex):
[  140.769759] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  140.769770] (II) intel(0): 	29120103802115780a092d9d564f9027
[  140.769781] (II) intel(0): 	21505400000001010101010101010101
[  140.769792] (II) intel(0): 	010101010101bc1b00aa502010303020
[  140.769803] (II) intel(0): 	36004bcf100000190000000f00000000
[  140.769814] (II) intel(0): 	0000000000206e050f00000000fe0043
[  140.769825] (II) intel(0): 	3238354a8031353457423820000000fe
[  140.769835] (II) intel(0): 	00273641476482abff01012020200081
[  140.769865] (II) intel(0): EDID vendor "CPT", prod id 5151
[  140.769878] (II) intel(0): Using hsync ranges from config file
[  140.769886] (II) intel(0): Using vrefresh ranges from config file
[  140.769895] (II) intel(0): Printing DDC gathered Modelines:
[  140.769905] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  140.769928] (II) intel(0): EDID vendor "CPT", prod id 5151
[  140.770010] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770020] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  140.770028] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  140.770036] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.770044] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.770052] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  140.770060] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.770068] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.770076] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.770084] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.770092] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  140.770100] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  140.770108] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  140.770116] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  140.770124] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  140.770132] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.770140] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.770148] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770156] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770164] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770172] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770180] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770188] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  140.770196] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  140.770204] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  140.770212] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.770220] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.770228] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.770236] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  140.770244] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  140.770252] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  140.770260] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.770267] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.770275] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.770283] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.770291] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  140.770299] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  140.770307] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  140.770327] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  140.770336] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.770344] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.770352] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  140.770365] (II) intel(0): Printing probed modes for output LVDS
[  140.770375] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  140.770390] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  140.770405] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  140.770419] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  140.770432] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  140.770446] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  140.770459] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  140.770473] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  140.770486] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  140.770499] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  140.770512] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  140.770525] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  140.770538] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  140.770552] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  140.770565] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  140.770578] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  140.770591] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  140.770604] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  140.779071] (II) intel(0): EDID for output TMDS-1
[  140.795508] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  141.069235] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  141.080957] (II) intel(0): EDID for output TV
[  141.102735] (II) intel(0): EDID for output VGA
[  141.159444] (II) intel(0): EDID for output LVDS
[  141.159495] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  141.159513] (II) intel(0): Year: 2008  Week: 41
[  141.159529] (II) intel(0): EDID Version: 1.3
[  141.159543] (II) intel(0): Digital Display Input
[  141.159557] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  141.159588] (II) intel(0): Gamma: 2.20
[  141.159610] (II) intel(0): No DPMS capabilities specified
[  141.159632] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  141.159648] (II) intel(0): First detailed timing is preferred mode
[  141.159663] (II) intel(0): GTF timings supported
[  141.159676] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  141.159706] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  141.159735] (II) intel(0): Manufacturer's mask: 0
[  141.159750] (II) intel(0): Supported additional Video Mode:
[  141.159764] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  141.159793] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  141.159870] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  141.159896] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[  141.159920] (II) intel(0):  C285J€154WB8
[  141.159934] (II) intel(0):  '6AGd‚«ÿ
[  141.159948] (II) intel(0): EDID (in hex):
[  141.159970] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  141.159991] (II) intel(0): 	29120103802115780a092d9d564f9027
[  141.160011] (II) intel(0): 	21505400000001010101010101010101
[  141.160032] (II) intel(0): 	010101010101bc1b00aa502010303020
[  141.160052] (II) intel(0): 	36004bcf100000190000000f00000000
[  141.160073] (II) intel(0): 	0000000000206e050f00000000fe0043
[  141.160093] (II) intel(0): 	3238354a8031353457423820000000fe
[  141.160113] (II) intel(0): 	00273641476482abff01012020200081
[  141.160130] (II) intel(0): EDID vendor "CPT", prod id 5151
[  141.160153] (II) intel(0): Using hsync ranges from config file
[  141.160168] (II) intel(0): Using vrefresh ranges from config file
[  141.160183] (II) intel(0): Printing DDC gathered Modelines:
[  141.160201] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  141.160243] (II) intel(0): EDID vendor "CPT", prod id 5151
[  141.160417] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160438] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  141.160454] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[  141.160469] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  141.160485] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  141.160500] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[  141.160515] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  141.160530] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  141.160545] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  141.160560] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  141.160575] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  141.160589] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  141.160604] (II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
[  141.160619] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  141.160634] (II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
[  141.160649] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  141.160664] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  141.160678] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160693] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160708] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160722] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160737] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160752] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[  141.160767] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  141.160781] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  141.160796] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  141.160811] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  141.160826] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  141.160840] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  141.160881] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  141.160897] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  141.160911] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  141.160926] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  141.160941] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  141.160955] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  141.160970] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  141.160984] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  141.160999] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  141.161013] (II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
[  141.161028] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  141.161043] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  141.161057] (II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
[  141.161077] (II) intel(0): Printing probed modes for output LVDS
[  141.161097] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  141.161128] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  141.161155] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  141.161182] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  141.161209] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  141.161235] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  141.161261] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  141.161287] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  141.161313] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  141.161339] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  141.161365] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  141.161391] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  141.161417] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  141.161443] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  141.161469] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  141.161495] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[  141.161520] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[  141.161547] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[  141.181372] (II) intel(0): EDID for output TMDS-1
[  141.194129] (II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01b00000 (pgoffset 6912)
[  141.476916] (II) intel(0): xf86UnbindGARTMemory: unbind key 2
[  141.484526] (II) intel(0): EDID for output TV
```

---

### Post by michael37 on 2009-03-14
Your computer has a problem with 3D driver for Intel video card installed.  

Here is the gist of the error:

```

[    0.642355] (II) LoadModule: "dri"
[    0.642917] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.677580] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
[    0.677648] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.677672] (II) UnloadModule: "dri"
[    0.677686] (II) Unloading /usr/lib/xorg/modules/extensions//libdri.so

```

I am not expert in Intel cards, but try this command
```

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

```

Then edit your xorg.conf```
sudo nano /etc/X11/xorg.conf
```, and change your device section to read: 
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"DRI"     "true"
EndSection

Section "DRI"
    Mode 0666
EndSection

```

Reboot.

Test 3D by running glxinfo.  It should not report any BADREQUESTS.

If you feel adventerous, try settings from this very helpful page:
[http://wiki.opencompositing.org/Intel%20with%20AiGLX](http://wiki.opencompositing.org/Intel%20with%20AiGLX)

Another suggestion from [thread=743740]forums[/thread]:
```

Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"

```
and
> I've also added this:
INTEL_BATCH="1"
in /etc/environment


If still unsure, please repost glxinfo.

***AFTER*** you fix DRI issue, you may still have one more issue remaining.  See here 

[https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel](https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel)

---

### Post by codyxx on 2009-03-14
Did not work. My glxinfo has this prompt 

after I was forced to go back to my default xorg.conf settings, because when I restarted my computer, I got an error (something to the extent of a low-graphics mode.)

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault (core dumped)

```

---

### Post by michael37 on 2009-03-14
> **codyxx said:**
> Did not work. My glxinfo has this prompt 

after I was forced to go back to my default xorg.conf settings, because when I restarted my computer, I got an error (something to the extent of a low-graphics mode.)


Error about low graphics mode means that you damaged your xorg.conf.  Your computer was not able to use it and it essentially discarded it (not literally, it just used the failsafe version which does not do 3D).  Our intent is to fix xorg.conf, and then to use it.

---

### Post by codyxx on 2009-03-14
Okay, now I am in even more of a predicament. I edited my xorg.conf to the settings shown in the thread you provided, and now, I can only log-in through failsafe terminal. I tried to edit the file in there through nano, but I don't have root permissions to do that.

---

### Post by michael37 on 2009-03-15
> **codyxx said:**
> Okay, now I am in even more of a predicament. I edited my xorg.conf to the settings shown in the thread you provided, and now, I can only log-in through failsafe terminal. I tried to edit the file in there through nano, but I don't have root permissions to do that.

Well, the easy solution is to run the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in the failsafe terminal.  That will reset xorg.conf to the working default.

About editing xorg.conf: always use sudo, e.g. sudo nano /etc/X11/xorg.conf.

There are very many websites on how to get a working xorg.conf.  Try reading them first.

---

### Post by codyxx on 2009-03-15
This is still occuring after my xorg.conf was set to default. I can show you my xsessions error file prompt I get when I try to log in:

```
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 26 id: not found 
etc/gdm/Xsession: Executing /usr/bin/gnome-session failed
exec: 20 x-terminal-emulator: not found
```

---

### Post by michael37 on 2009-03-15
At this point, I am afraid your system is too broken.  I do not know why -- I would think that you probably made too many changes at once.

Reinstall, get a clean one, and then work on your xorg.conf problem.

---

### Post by codyxx on 2009-03-15
For the moment, I wrote down all of the graphical settings I had before regarding my theme and such as well as the programs I had installed at the time. I am first booting off of a live CD as to recover my music files and such to transfer those to my friend's external HD. After that, I will then proceed to install Ubuntu once more.

---

### Post by jamaj on 2010-03-22
I upgraded my dell inspiron 1525 to 8.10 LTS (intrepid)
I got the same error.
My compiz was functioning. Now it gives me the same error above.

---

### Post by jamaj on 2010-03-24
I checked out that the problem was due corrupted packages. I then remved all drivers from xserver-xorg except intel one.

Evething now seems ok, even the direct rendering is functioning. But, i realized that GoogleEarth and other OpenGL programs are not working very well.

With metacity instead compiz it works better. So, i think that there is some incompatobility between intel driver and Direct Rendering or with glx. I really dont know.

---

