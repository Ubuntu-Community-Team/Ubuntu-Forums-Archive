---
title: "ATI/AMD propietary FGLRX graphics driver - Mobility Radeon HD3450"
date: 2012-01-17
forum: Hardware
---

### Post by nero32222 on 2012-01-17
Hi guys!

I have a Dell Studio 1535 notebook, which has a Mobility Radeon HD3450 graphics card in it. The problem is, that immediately after I install the ATI/AMD propietary FGLRX graphics driver, the screen brightness will be set up automatically to 100% after each reboot. (By using the default ubuntu settings, without the installed ATI/AMD propietary FGLRX graphics driver, the issue does not occur.) Within the AMD Catalyst Control Center I wasn't able to find any option to set it correctly up. I searched a lot for the solution on the net, but does not found any...
Anybody help me by this?
 
sudo lshw >
description: VGA compatible controller
product: Mobility Radeon HD 3400 Series
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:49 memory:e0000000-efffffff ioport:ee00(size=256)

Thank you for your help in advance! :-)

---

### Post by MoreOrLess on 2012-01-17
See this for example commands. Once you figure out what command/setting you want, put the command in /etc/rc.local so it runs at every start. [http://k3mist.com/linux/contrast-brightness-gamma-linux/](http://k3mist.com/linux/contrast-brightness-gamma-linux/)

---

### Post by nero32222 on 2012-01-18
Hi! 
Thank you for your post!
The link does not really solved the issue, unfortunately. :-( 
I think, it's not about the brightness, saturation, hue or contrast, coz they are all set correctly and are changeable even in Catalyst Control Center or in terminal. It must be about the 'fglrx (2:8.881-0ubuntu4.1)' pkg., coz as soon as I install it the backlighting of the LCD(LED) display will be turned up to max. value, so that I need to turn it down manually by press. the Fn+Scrolldown keys.
Today I downloaded the 'ati-driver-installer-11-12-x86.x86_64' driver from AMD and installed it without any problems (even the 'aticonfig --initial gave me the right answer > [sudo] password for x: ;Found fglrx primary device section; Using /etc/X11/xorg.conf ;Saving back-up to /etc/X11/xorg.conf.fglrx-10'), but then after a restart, the resolution of the screen was able to be set up to a max. value of only 1152x864 instead of 1440x900. This time, the backlighting function behave well and did not turned up to a max. value, but according to synaptic pkg. manager no 'fgrlx' or similar graphics driver pkg. was installed, which seemed to me as there were no proper driver installed.

some info, furhertmore:
- I'm using 64bit Xubuntu (3.0.0-14-generic)
- installed 64bit driver
- have 'xrandr 1.3.5' installed
- xorg.conf:
Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

---

### Post by MoreOrLess on 2012-01-18
Unless you built packages from the installer, it just dumps stuff into your filesystem (not ideal on Debian/Ubuntu). As for the resolution issue, post/pastebin your /var/log/Xorg.0.log

---

### Post by nero32222 on 2012-01-18
Currently I have 'fglrx' installed, hope this hasn't a big influence on the output file:


[    22.354] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.354] X Protocol Version 11, Revision 0
[    22.354] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    22.354] Current Operating System: Linux x 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    22.354] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=61652583-69b8-4d41-8493-f6e9ff96e0e5 ro quiet splash vt.handoff=7
[    22.354] Build Date: 19 October 2011  05:21:26AM
[    22.354] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.354] Current version of pixman: 0.22.2
[    22.354] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.354] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.354] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 18 17:18:00 2012
[    22.354] (==) Using config file: "/etc/X11/xorg.conf"
[    22.354] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.355] (==) ServerLayout "aticonfig Layout"
[    22.355] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    22.355] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    22.355] (**) |   |-->Device "aticonfig-Device[0]-0"
[    22.355] (==) Automatically adding devices
[    22.355] (==) Automatically enabling devices
[    22.355] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.355] 	Entry deleted from font path.
[    22.355] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.355] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.355] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.355] (II) Loader magic: 0x7e0220
[    22.355] (II) Module ABI versions:
[    22.355] 	X.Org ANSI C Emulation: 0.4
[    22.355] 	X.Org Video Driver: 10.0
[    22.355] 	X.Org XInput driver : 12.3
[    22.355] 	X.Org Server Extension : 5.0
[    22.357] (--) PCI:*(0:1:0:0) 1002:95c4:1028:0254 rev 0, Mem @ 0xe0000000/268435456, 0xf6df0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    22.357] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.357] (II) "extmod" will be loaded by default.
[    22.357] (II) "dbe" will be loaded by default.
[    22.357] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    22.357] (II) "record" will be loaded by default.
[    22.357] (II) "dri" will be loaded by default.
[    22.357] (II) "dri2" will be loaded by default.
[    22.357] (II) LoadModule: "glx"
[    22.375] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    22.375] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    22.375] 	compiled for 6.9.0, module version = 1.0.0
[    22.375] (II) Loading extension GLX
[    22.375] (II) LoadModule: "extmod"
[    22.375] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.375] (II) Module extmod: vendor="X.Org Foundation"
[    22.375] 	compiled for 1.10.4, module version = 1.0.0
[    22.375] 	Module class: X.Org Server Extension
[    22.375] 	ABI class: X.Org Server Extension, version 5.0
[    22.375] (II) Loading extension MIT-SCREEN-SAVER
[    22.375] (II) Loading extension XFree86-VidModeExtension
[    22.375] (II) Loading extension XFree86-DGA
[    22.376] (II) Loading extension DPMS
[    22.376] (II) Loading extension XVideo
[    22.376] (II) Loading extension XVideo-MotionCompensation
[    22.376] (II) Loading extension X-Resource
[    22.376] (II) LoadModule: "dbe"
[    22.376] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.376] (II) Module dbe: vendor="X.Org Foundation"
[    22.376] 	compiled for 1.10.4, module version = 1.0.0
[    22.376] 	Module class: X.Org Server Extension
[    22.376] 	ABI class: X.Org Server Extension, version 5.0
[    22.376] (II) Loading extension DOUBLE-BUFFER
[    22.376] (II) LoadModule: "record"
[    22.376] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.376] (II) Module record: vendor="X.Org Foundation"
[    22.376] 	compiled for 1.10.4, module version = 1.13.0
[    22.376] 	Module class: X.Org Server Extension
[    22.376] 	ABI class: X.Org Server Extension, version 5.0
[    22.376] (II) Loading extension RECORD
[    22.376] (II) LoadModule: "dri"
[    22.377] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.377] (II) Module dri: vendor="X.Org Foundation"
[    22.377] 	compiled for 1.10.4, module version = 1.0.0
[    22.377] 	ABI class: X.Org Server Extension, version 5.0
[    22.377] (II) Loading extension XFree86-DRI
[    22.377] (II) LoadModule: "dri2"
[    22.377] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.377] (II) Module dri2: vendor="X.Org Foundation"
[    22.377] 	compiled for 1.10.4, module version = 1.2.0
[    22.377] 	ABI class: X.Org Server Extension, version 5.0
[    22.377] (II) Loading extension DRI2
[    22.377] (II) LoadModule: "fglrx"
[    22.377] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    22.397] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    22.397] 	compiled for 1.4.99.906, module version = 8.88.7
[    22.397] 	Module class: X.Org Video Driver
[    22.397] (II) Loading sub module "fglrxdrm"
[    22.397] (II) LoadModule: "fglrxdrm"
[    22.397] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    22.398] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    22.398] 	compiled for 1.4.99.906, module version = 8.88.7
[    22.398] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[    22.398] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[    22.398] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:04:01
[    22.398] (++) using VT number 7

[    22.398] (WW) Falling back to old probe method for fglrx
[    22.420] (II) Loading PCS database from /etc/ati/amdpcsdb
[    22.421] (--) Chipset Supported AMD Graphics Processor (0x95C4) found
[    22.421] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    22.421] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    22.421] (II) AMD Video driver is signed
[    22.421] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    22.421] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    22.421] (II) fglrx(0): pEnt->device->identifier=0x1902630
[    22.421] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    22.421] (II) Loading sub module "vgahw"
[    22.421] (II) LoadModule: "vgahw"
[    22.422] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    22.422] (II) Module vgahw: vendor="X.Org Foundation"
[    22.422] 	compiled for 1.10.4, module version = 0.1.0
[    22.422] 	ABI class: X.Org Video Driver, version 10.0
[    22.422] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    22.422] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.422] (==) fglrx(0): Default visual is TrueColor
[    22.422] (**) fglrx(0): Option "DPMS" "true"
[    22.422] (==) fglrx(0): RGB weight 888
[    22.422] (II) fglrx(0): Using 8 bits per RGB 
[    22.422] (==) fglrx(0): Buffer Tiling is ON
[    22.422] (II) Loading sub module "fglrxdrm"
[    22.422] (II) LoadModule: "fglrxdrm"
[    22.422] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    22.422] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    22.422] 	compiled for 1.4.99.906, module version = 8.88.7
[    22.424] ukiDynamicMajor: found major device number 249
[    22.424] ukiDynamicMajor: found major device number 249
[    22.424] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    22.424] ukiOpenDevice: node name is /dev/ati/card0
[    22.424] ukiOpenDevice: open result is 14, (OK)
[    22.424] ukiOpenByBusid: ukiOpenMinor returns 14
[    22.424] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    22.424] (==) fglrx(0): NoAccel = NO
[    22.425] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    22.425] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3400 Series" (Chipset = 0x95c4)
[    22.425] (--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x0254)
[    22.425] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    22.425] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    22.425] (--) fglrx(0): MMIO registers at 0xf6df0000
[    22.425] (--) fglrx(0): I/O port at 0x0000ee00
[    22.425] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    22.425] (II) fglrx(0): AC Adapter is used
[    22.429] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    22.430] (II) Loading sub module "vbe"
[    22.430] (II) LoadModule: "vbe"
[    22.445] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    22.445] (II) Module vbe: vendor="X.Org Foundation"
[    22.445] 	compiled for 1.10.4, module version = 1.1.0
[    22.445] 	ABI class: X.Org Video Driver, version 10.0
[    22.446] (II) fglrx(0): VESA BIOS detected
[    22.446] (II) fglrx(0): VESA VBE Version 3.0
[    22.446] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    22.446] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    22.446] (II) fglrx(0): VESA VBE OEM Software Rev: 10.86
[    22.446] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    22.446] (II) fglrx(0): VESA VBE OEM Product: M82
[    22.446] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    22.479] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    22.479] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
[    22.479] (II) fglrx(0): PCIE card detected
[    22.479] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    22.479] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    22.482] (II) fglrx(0): Using adapter: 1:0.0.
[    22.512] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
[    22.532] (II) fglrx(0): Interrupt handler installed at IRQ 49.
[    22.532] (II) fglrx(0): RandR 1.2 support is enabled!
[    22.532] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    22.532] (==) fglrx(0): Center Mode is disabled 
[    22.532] (II) Loading sub module "fb"
[    22.532] (II) LoadModule: "fb"
[    22.532] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.532] (II) Module fb: vendor="X.Org Foundation"
[    22.532] 	compiled for 1.10.4, module version = 1.0.0
[    22.532] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.532] (II) Loading sub module "ddc"
[    22.532] (II) LoadModule: "ddc"
[    22.532] (II) Module "ddc" already built-in
[    23.012] (II) fglrx(0): Finished Initialize PPLIB!
[    23.015] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    23.015] (II) fglrx(0): Output DFP1 has no monitor section
[    23.015] (II) fglrx(0): Output CRT1 has no monitor section
[    23.015] (II) Loading sub module "ddc"
[    23.015] (II) LoadModule: "ddc"
[    23.015] (II) Module "ddc" already built-in
[    23.015] (II) fglrx(0): Connected Display0: LVDS
[    23.015] (II) fglrx(0): Display0 EDID data ---------------------------
[    23.015] (II) fglrx(0): Manufacturer: LPL  Model: b80a  Serial#: 0
[    23.015] (II) fglrx(0): Year: 2008  Week: 0
[    23.015] (II) fglrx(0): EDID Version: 1.3
[    23.015] (II) fglrx(0): Digital Display Input
[    23.015] (II) fglrx(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    23.015] (II) fglrx(0): Gamma: 2.20
[    23.015] (II) fglrx(0): No DPMS capabilities specified
[    23.015] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.015] (II) fglrx(0): First detailed timing is preferred mode
[    23.015] (II) fglrx(0): redX: 0.587 redY: 0.344   greenX: 0.337 greenY: 0.561
[    23.015] (II) fglrx(0): blueX: 0.153 blueY: 0.122   whiteX: 0.313 whiteY: 0.329
[    23.015] (II) fglrx(0): Manufacturer's mask: 0
[    23.015] (II) fglrx(0): Supported detailed timing:
[    23.015] (II) fglrx(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[    23.015] (II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[    23.015] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    23.015] (II) fglrx(0): Supported detailed timing:
[    23.015] (II) fglrx(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[    23.015] (II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[    23.015] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    23.015] (II) fglrx(0):  FM041&#8364;154WP2
[    23.015] (II) fglrx(0): Unknown vendor-specific block 0
[    23.015] (II) fglrx(0): EDID (in hex):
[    23.015] (II) fglrx(0): 	00ffffffffffff00320c0ab800000000
[    23.015] (II) fglrx(0): 	00120103902115780a46559658568f27
[    23.015] (II) fglrx(0): 	1f505400000001010101010101010101
[    23.015] (II) fglrx(0): 	010101010101a325a02651841a303020
[    23.015] (II) fglrx(0): 	36004bcf1000001ba325a02651841a30
[    23.015] (II) fglrx(0): 	302036004bcf1000001b000000fe0046
[    23.015] (II) fglrx(0): 	4d303431803135345750320a00000000
[    23.015] (II) fglrx(0): 	003c587490acc8e4ff02010a202000f1
[    23.015] (II) fglrx(0): End of Display0 EDID data --------------------
[    23.048] (II) fglrx(0): EDID for output LVDS
[    23.048] (II) fglrx(0): Manufacturer: LPL  Model: b80a  Serial#: 0
[    23.048] (II) fglrx(0): Year: 2008  Week: 0
[    23.048] (II) fglrx(0): EDID Version: 1.3
[    23.048] (II) fglrx(0): Digital Display Input
[    23.048] (II) fglrx(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    23.048] (II) fglrx(0): Gamma: 2.20
[    23.048] (II) fglrx(0): No DPMS capabilities specified
[    23.048] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.048] (II) fglrx(0): First detailed timing is preferred mode
[    23.048] (II) fglrx(0): redX: 0.587 redY: 0.344   greenX: 0.337 greenY: 0.561
[    23.048] (II) fglrx(0): blueX: 0.153 blueY: 0.122   whiteX: 0.313 whiteY: 0.329
[    23.048] (II) fglrx(0): Manufacturer's mask: 0
[    23.048] (II) fglrx(0): Supported detailed timing:
[    23.048] (II) fglrx(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[    23.048] (II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[    23.048] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    23.048] (II) fglrx(0): Supported detailed timing:
[    23.048] (II) fglrx(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[    23.048] (II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[    23.048] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    23.048] (II) fglrx(0):  FM041&#8364;154WP2
[    23.048] (II) fglrx(0): Unknown vendor-specific block 0
[    23.048] (II) fglrx(0): EDID (in hex):
[    23.048] (II) fglrx(0): 	00ffffffffffff00320c0ab800000000
[    23.048] (II) fglrx(0): 	00120103902115780a46559658568f27
[    23.048] (II) fglrx(0): 	1f505400000001010101010101010101
[    23.048] (II) fglrx(0): 	010101010101a325a02651841a303020
[    23.048] (II) fglrx(0): 	36004bcf1000001ba325a02651841a30
[    23.048] (II) fglrx(0): 	302036004bcf1000001b000000fe0046
[    23.048] (II) fglrx(0): 	4d303431803135345750320a00000000
[    23.048] (II) fglrx(0): 	003c587490acc8e4ff02010a202000f1
[    23.048] (II) fglrx(0): EDID vendor "LPL", prod id 47114
[    23.049] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.049] (II) fglrx(0): Modeline "1440x900"x0.0   96.35  1440 1488 1520 1734  900 903 909 926 +hsync -vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Printing probed modes for output LVDS
[    23.049] (II) fglrx(0): Modeline "1440x900"x60.0   96.35  1440 1488 1520 1734  900 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1280x800"x60.0   96.35  1280 1488 1520 1734  800 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1152x864"x60.0   96.35  1152 1488 1520 1734  864 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1280x768"x60.0   96.35  1280 1488 1520 1734  768 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1280x720"x60.0   96.35  1280 1488 1520 1734  720 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1024x768"x60.0   96.35  1024 1488 1520 1734  768 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "1024x600"x60.0   96.35  1024 1488 1520 1734  600 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "800x600"x60.0   96.35  800 1488 1520 1734  600 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "800x480"x60.0   96.35  800 1488 1520 1734  480 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "720x480"x60.0   96.35  720 1488 1520 1734  480 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): Modeline "640x480"x60.0   96.35  640 1488 1520 1734  480 903 909 926 -hsync +vsync (55.6 kHz)
[    23.049] (II) fglrx(0): EDID for output DFP1
[    23.049] (II) fglrx(0): EDID for output CRT1
[    23.049] (II) fglrx(0): Output LVDS connected
[    23.049] (II) fglrx(0): Output DFP1 disconnected
[    23.049] (II) fglrx(0): Output CRT1 disconnected
[    23.049] (II) fglrx(0): Using exact sizes for initial modes
[    23.049] (II) fglrx(0): Output LVDS using initial mode 1440x900
[    23.049] (II) fglrx(0): Display dimensions: (330, 210) mm
[    23.049] (II) fglrx(0): DPI set to (110, 108)
[    23.049] (II) fglrx(0): Adapter ATI Mobility Radeon HD 3400 Series has 2 configurable heads and 1 displays connected.
[    23.049] (==) fglrx(0):  PseudoColor visuals disabled
[    23.049] (II) Loading sub module "ramdac"
[    23.049] (II) LoadModule: "ramdac"
[    23.049] (II) Module "ramdac" already built-in
[    23.049] (==) fglrx(0): NoDRI = NO
[    23.049] (==) fglrx(0): Capabilities: 0x00000000
[    23.049] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    23.049] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    23.049] (==) fglrx(0): UseFastTLS=0
[    23.049] (==) fglrx(0): BlockSignalsOnLock=1
[    23.049] (--) Depth 24 pixmap format is 32 bpp
[    23.050] (II) Loading extension ATIFGLRXDRI
[    23.050] (II) fglrx(0): doing swlDriScreenInit
[    23.050] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    23.050] ukiDynamicMajor: found major device number 249
[    23.050] ukiDynamicMajor: found major device number 249
[    23.050] ukiDynamicMajor: found major device number 249
[    23.050] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.050] ukiOpenDevice: node name is /dev/ati/card0
[    23.050] ukiOpenDevice: open result is 19, (OK)
[    23.050] ukiOpenByBusid: ukiOpenMinor returns 19
[    23.050] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.050] (II) fglrx(0): [uki] DRM interface version 1.0
[    23.050] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    23.051] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    23.051] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fbf9465f000
[    23.051] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    23.051] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    23.051] (II) fglrx(0): swlDriScreenInit done
[    23.051] (II) fglrx(0): Kernel Module Version Information:
[    23.051] (II) fglrx(0):     Name: fglrx
[    23.051] (II) fglrx(0):     Version: 8.88.7
[    23.051] (II) fglrx(0):     Date: Jul 28 2011
[    23.051] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    23.051] (II) fglrx(0): Kernel Module version matches driver.
[    23.051] (II) fglrx(0): Kernel Module Build Time Information:
[    23.051] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.0.0-14-generic
[    23.051] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    23.051] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    23.051] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    23.051] (II) fglrx(0): [uki] register handle = 0x00004000
[    23.087] (II) fglrx(0): DRI initialization successfull
[    23.087] (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01004000
[    23.087] (==) fglrx(0): Backing store disabled
[    23.087] (II) Loading extension FGLRXEXTENSION
[    23.087] (**) fglrx(0): DPMS enabled
[    23.088] (II) fglrx(0): Initialized in-driver Xinerama extension
[    23.088] (**) fglrx(0): Textured Video is enabled.
[    23.088] (II) LoadModule: "glesx"
[    23.088] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    23.089] (II) Module glesx: vendor="X.Org Foundation"
[    23.089] 	compiled for 1.4.99.906, module version = 1.0.0
[    23.089] (II) Loading extension GLESX
[    23.089] (II) fglrx(0): GLESX enableFlags = 528
[    23.089] (II) fglrx(0): GLESX is enabled
[    23.089] (II) LoadModule: "amdxmm"
[    23.089] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    23.090] (II) Module amdxmm: vendor="X.Org Foundation"
[    23.090] 	compiled for 1.4.99.906, module version = 2.0.0
[    23.090] (II) Loading extension AMDXVOPL
[    23.090] (II) Loading extension AMDXVBA
[    23.090] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[    23.099] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    23.102] (II) fglrx(0): Enable composite support successfully
[    23.102] (WW) fglrx(0): Option "VendorName" is not used
[    23.102] (WW) fglrx(0): Option "ModelName" is not used
[    23.102] (II) fglrx(0): X context handle = 0x1
[    23.102] (II) fglrx(0): [DRI] installation complete
[    23.102] (==) fglrx(0): Silken mouse enabled
[    23.102] (==) fglrx(0): Using HW cursor of display infrastructure!
[    23.102] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    23.102] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    23.102] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    23.698] (--) RandR disabled
[    23.698] (II) Initializing built-in extension Generic Event Extension
[    23.698] (II) Initializing built-in extension SHAPE
[    23.698] (II) Initializing built-in extension MIT-SHM
[    23.698] (II) Initializing built-in extension XInputExtension
[    23.699] (II) Initializing built-in extension XTEST
[    23.699] (II) Initializing built-in extension BIG-REQUESTS
[    23.699] (II) Initializing built-in extension SYNC
[    23.699] (II) Initializing built-in extension XKEYBOARD
[    23.699] (II) Initializing built-in extension XC-MISC
[    23.699] (II) Initializing built-in extension SECURITY
[    23.699] (II) Initializing built-in extension XINERAMA
[    23.699] (II) Initializing built-in extension XFIXES
[    23.699] (II) Initializing built-in extension RENDER
[    23.699] (II) Initializing built-in extension RANDR
[    23.699] (II) Initializing built-in extension COMPOSITE
[    23.699] (II) Initializing built-in extension DAMAGE
[    23.699] (II) Initializing built-in extension GESTURE
[    23.802] ukiDynamicMajor: found major device number 249
[    23.802] ukiDynamicMajor: found major device number 249
[    23.802] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.802] ukiOpenDevice: node name is /dev/ati/card0
[    23.802] ukiOpenDevice: open result is 21, (OK)
[    23.802] ukiOpenByBusid: ukiOpenMinor returns 21
[    23.802] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    25.399] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    25.399] (II) fglrx(0): Enable the clock gating!
[    25.399] (II) fglrx(0): Setting screen physical size to 381 x 238
[    25.750] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.772] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    25.772] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.772] (II) LoadModule: "evdev"
[    25.773] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.773] (II) Module evdev: vendor="X.Org Foundation"
[    25.773] 	compiled for 1.10.2, module version = 2.6.0
[    25.773] 	Module class: X.Org XInput Driver
[    25.773] 	ABI class: X.Org XInput driver, version 12.3
[    25.773] (II) Using input driver 'evdev' for 'Video Bus'
[    25.773] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.773] (**) Video Bus: always reports core events
[    25.773] (**) Video Bus: Device: "/dev/input/event5"
[    25.773] (--) Video Bus: Found keys
[    25.773] (II) Video Bus: Configuring as keyboard
[    25.773] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input5/event5"
[    25.773] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.774] (**) Option "xkb_rules" "evdev"
[    25.774] (**) Option "xkb_model" "pc105"
[    25.774] (**) Option "xkb_layout" "hu"
[    25.775] (II) XKB: reuse xkmfile /var/lib/xkb/server-544CA222969D37ADB2821D0E82B6A6D6FDEF206B.xkm
[    25.781] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.781] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.781] (II) Using input driver 'evdev' for 'Power Button'
[    25.781] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.781] (**) Power Button: always reports core events
[    25.781] (**) Power Button: Device: "/dev/input/event1"
[    25.781] (--) Power Button: Found keys
[    25.781] (II) Power Button: Configuring as keyboard
[    25.781] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.781] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.781] (**) Option "xkb_rules" "evdev"
[    25.781] (**) Option "xkb_model" "pc105"
[    25.781] (**) Option "xkb_layout" "hu"
[    25.781] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.781] (II) No input driver/identifier specified (ignoring)
[    25.782] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.782] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.782] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.782] (**) Sleep Button: always reports core events
[    25.782] (**) Sleep Button: Device: "/dev/input/event2"
[    25.782] (--) Sleep Button: Found keys
[    25.782] (II) Sleep Button: Configuring as keyboard
[    25.782] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.782] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.782] (**) Option "xkb_rules" "evdev"
[    25.782] (**) Option "xkb_model" "pc105"
[    25.782] (**) Option "xkb_layout" "hu"
[    25.783] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[    25.783] (II) No input driver/identifier specified (ignoring)
[    25.784] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event7)
[    25.784] (II) No input driver/identifier specified (ignoring)
[    25.785] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event8)
[    25.785] (II) No input driver/identifier specified (ignoring)
[    25.785] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event9)
[    25.785] (II) No input driver/identifier specified (ignoring)
[    25.787] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event4)
[    25.787] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    25.787] (II) Using input driver 'evdev' for 'PIXART USB OPTICAL MOUSE'
[    25.787] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.787] (**) PIXART USB OPTICAL MOUSE: always reports core events
[    25.787] (**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event4"
[    25.787] (--) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[    25.787] (--) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[    25.787] (--) PIXART USB OPTICAL MOUSE: Found relative axes
[    25.787] (--) PIXART USB OPTICAL MOUSE: Found x and y relative axes
[    25.787] (II) PIXART USB OPTICAL MOUSE: Configuring as mouse
[    25.787] (II) PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[    25.787] (**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    25.787] (**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.787] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input4/event4"
[    25.787] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
[    25.787] (II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
[    25.787] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    25.787] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[    25.787] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    25.787] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    25.787] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse0)
[    25.787] (II) No input driver/identifier specified (ignoring)
[    25.789] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event12)
[    25.789] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[    25.789] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_2M'
[    25.789] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.789] (**) Laptop_Integrated_Webcam_2M: always reports core events
[    25.789] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event12"
[    25.789] (--) Laptop_Integrated_Webcam_2M: Found keys
[    25.789] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[    25.789] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input12/event12"
[    25.789] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[    25.789] (**) Option "xkb_rules" "evdev"
[    25.789] (**) Option "xkb_model" "pc105"
[    25.789] (**) Option "xkb_layout" "hu"
[    25.792] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.792] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.793] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.793] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.793] (**) AT Translated Set 2 keyboard: always reports core events
[    25.793] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.793] (--) AT Translated Set 2 keyboard: Found keys
[    25.793] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.793] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.793] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.793] (**) Option "xkb_rules" "evdev"
[    25.793] (**) Option "xkb_model" "pc105"
[    25.793] (**) Option "xkb_layout" "hu"
[    25.793] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event13)
[    25.793] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    25.793] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    25.793] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.793] (**) PS/2 Mouse: always reports core events
[    25.793] (**) PS/2 Mouse: Device: "/dev/input/event13"
[    25.793] (--) PS/2 Mouse: Found 3 mouse buttons
[    25.793] (--) PS/2 Mouse: Found relative axes
[    25.793] (--) PS/2 Mouse: Found x and y relative axes
[    25.793] (II) PS/2 Mouse: Configuring as mouse
[    25.793] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    25.793] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.793] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event13"
[    25.793] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    25.793] (II) PS/2 Mouse: initialized for relative axes.
[    25.793] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    25.793] (**) PS/2 Mouse: (accel) acceleration profile 0
[    25.793] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    25.794] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    25.794] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    25.794] (II) No input driver/identifier specified (ignoring)
[    25.794] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event14)
[    25.794] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    25.794] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    25.794] (II) LoadModule: "synaptics"
[    25.794] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.795] (II) Module synaptics: vendor="X.Org Foundation"
[    25.795] 	compiled for 1.10.4, module version = 1.4.1
[    25.795] 	Module class: X.Org XInput Driver
[    25.795] 	ABI class: X.Org XInput driver, version 12.3
[    25.795] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    25.795] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.795] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    25.795] (**) Option "Device" "/dev/input/event14"
[    25.795] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    25.795] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    25.795] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    25.795] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    25.795] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    25.796] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    25.796] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    25.800] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event14"
[    25.800] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    25.800] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    25.800] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    25.800] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    25.800] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    25.800] (II) No input driver/identifier specified (ignoring)
[    25.805] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    25.805] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.806] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    25.806] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.806] (**) Dell WMI hotkeys: always reports core events
[    25.806] (**) Dell WMI hotkeys: Device: "/dev/input/event10"
[    25.806] (--) Dell WMI hotkeys: Found keys
[    25.806] (II) Dell WMI hotkeys: Configuring as keyboard
[    25.806] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    25.806] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    25.806] (**) Option "xkb_rules" "evdev"
[    25.806] (**) Option "xkb_model" "pc105"
[    25.806] (**) Option "xkb_layout" "hu"
[    25.807] (II) config/udev: Adding input device ITE8708 CIR transceiver (/dev/input/event6)
[    25.807] (**) ITE8708 CIR transceiver: Applying InputClass "evdev keyboard catchall"
[    25.807] (II) Using input driver 'evdev' for 'ITE8708 CIR transceiver'
[    25.807] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.807] (**) ITE8708 CIR transceiver: always reports core events
[    25.808] (**) ITE8708 CIR transceiver: Device: "/dev/input/event6"
[    25.808] (--) ITE8708 CIR transceiver: Found keys
[    25.808] (II) ITE8708 CIR transceiver: Configuring as keyboard
[    25.808] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input6/event6"
[    25.808] (II) XINPUT: Adding extended input device "ITE8708 CIR transceiver" (type: KEYBOARD)
[    25.808] (**) Option "xkb_rules" "evdev"
[    25.808] (**) Option "xkb_model" "pc105"
[    25.808] (**) Option "xkb_layout" "hu"
[    25.851] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    32.359] (II) fglrx(0): EDID vendor "LPL", prod id 47114
[    32.359] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.359] (II) fglrx(0): Modeline "1440x900"x0.0   96.35  1440 1488 1520 1734  900 903 909 926 +hsync -vsync (55.6 kHz)
[    32.971] (II) fglrx(0): EDID vendor "LPL", prod id 47114
[    32.971] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.971] (II) fglrx(0): Modeline "1440x900"x0.0   96.35  1440 1488 1520 1734  900 903 909 926 +hsync -vsync (55.6 kHz)

Thanks a lot for your efforts!

---

### Post by nero32222 on 2012-01-18
I also have also an 'Xorg.1.log' file:


[ 15704.364] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[ 15704.364] X Protocol Version 11, Revision 0
[ 15704.364] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[ 15704.364] Current Operating System: Linux x 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[ 15704.364] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=61652583-69b8-4d41-8493-f6e9ff96e0e5 ro quiet splash vt.handoff=7
[ 15704.364] Build Date: 19 October 2011  05:21:26AM
[ 15704.364] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 15704.364] Current version of pixman: 0.22.2
[ 15704.364] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[ 15704.364] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 15704.364] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Nov 14 14:57:37 2011
[ 15704.364] (==) Using config file: "/etc/X11/xorg.conf"
[ 15704.364] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 15704.379] (==) No Layout section.  Using the first Screen section.
[ 15704.379] (**) |-->Screen "Default Screen" (0)
[ 15704.379] (**) |   |-->Monitor "<default monitor>"
[ 15704.379] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[ 15704.379] (==) Automatically adding devices
[ 15704.379] (==) Automatically enabling devices
[ 15704.379] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 15704.379] 	Entry deleted from font path.
[ 15704.379] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 15704.379] 	Entry deleted from font path.
[ 15704.379] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 15704.379] 	Entry deleted from font path.
[ 15704.379] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 15704.379] 	Entry deleted from font path.
[ 15704.379] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 15704.379] 	Entry deleted from font path.
[ 15704.379] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 15704.379] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 15704.379] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 15704.379] (II) Loader magic: 0x7e0220
[ 15704.379] (II) Module ABI versions:
[ 15704.379] 	X.Org ANSI C Emulation: 0.4
[ 15704.379] 	X.Org Video Driver: 10.0
[ 15704.379] 	X.Org XInput driver : 12.3
[ 15704.379] 	X.Org Server Extension : 5.0
[ 15704.380] (--) PCI:*(0:1:0:0) 1002:95c4:1028:0254 rev 0, Mem @ 0xe0000000/268435456, 0xf6df0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[ 15704.381] (II) Open ACPI successful (/var/run/acpid.socket)
[ 15704.381] (II) "extmod" will be loaded by default.
[ 15704.381] (II) "dbe" will be loaded by default.
[ 15704.381] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[ 15704.381] (II) "record" will be loaded by default.
[ 15704.381] (II) "dri" will be loaded by default.
[ 15704.381] (II) "dri2" will be loaded by default.
[ 15704.381] (II) LoadModule: "glx"
[ 15704.381] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 15704.390] (II) Module glx: vendor="X.Org Foundation"
[ 15704.390] 	compiled for 1.10.4, module version = 1.0.0
[ 15704.390] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.390] (==) AIGLX enabled
[ 15704.390] (II) Loading extension GLX
[ 15704.390] (II) LoadModule: "extmod"
[ 15704.390] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 15704.390] (II) Module extmod: vendor="X.Org Foundation"
[ 15704.390] 	compiled for 1.10.4, module version = 1.0.0
[ 15704.390] 	Module class: X.Org Server Extension
[ 15704.390] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.390] (II) Loading extension MIT-SCREEN-SAVER
[ 15704.390] (II) Loading extension XFree86-VidModeExtension
[ 15704.390] (II) Loading extension XFree86-DGA
[ 15704.390] (II) Loading extension DPMS
[ 15704.390] (II) Loading extension XVideo
[ 15704.390] (II) Loading extension XVideo-MotionCompensation
[ 15704.390] (II) Loading extension X-Resource
[ 15704.390] (II) LoadModule: "dbe"
[ 15704.391] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 15704.391] (II) Module dbe: vendor="X.Org Foundation"
[ 15704.391] 	compiled for 1.10.4, module version = 1.0.0
[ 15704.391] 	Module class: X.Org Server Extension
[ 15704.391] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.391] (II) Loading extension DOUBLE-BUFFER
[ 15704.391] (II) LoadModule: "record"
[ 15704.391] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 15704.391] (II) Module record: vendor="X.Org Foundation"
[ 15704.391] 	compiled for 1.10.4, module version = 1.13.0
[ 15704.391] 	Module class: X.Org Server Extension
[ 15704.391] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.391] (II) Loading extension RECORD
[ 15704.391] (II) LoadModule: "dri"
[ 15704.391] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 15704.391] (II) Module dri: vendor="X.Org Foundation"
[ 15704.391] 	compiled for 1.10.4, module version = 1.0.0
[ 15704.391] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.391] (II) Loading extension XFree86-DRI
[ 15704.391] (II) LoadModule: "dri2"
[ 15704.391] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 15704.391] (II) Module dri2: vendor="X.Org Foundation"
[ 15704.391] 	compiled for 1.10.4, module version = 1.2.0
[ 15704.391] 	ABI class: X.Org Server Extension, version 5.0
[ 15704.391] (II) Loading extension DRI2
[ 15704.391] (==) Matched fglrx as autoconfigured driver 0
[ 15704.391] (==) Matched ati as autoconfigured driver 1
[ 15704.391] (==) Matched vesa as autoconfigured driver 2
[ 15704.391] (==) Matched fbdev as autoconfigured driver 3
[ 15704.392] (==) Assigned the driver to the xf86ConfigLayout
[ 15704.392] (II) LoadModule: "fglrx"
[ 15704.392] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[ 15704.392] (EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so: /usr/lib/xorg/modules/drivers/fglrx_drv.so: cannot open shared object file: No such file or directory
[ 15704.392] (EE) LoadModule: Module fglrx does not have a fglrxModuleData data object.
[ 15704.392] (II) UnloadModule: "fglrx"
[ 15704.392] (II) Unloading fglrx
[ 15704.392] (EE) Failed to load module "fglrx" (invalid module, 0)
[ 15704.392] (II) LoadModule: "ati"
[ 15704.392] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 15704.392] (II) Module ati: vendor="X.Org Foundation"
[ 15704.392] 	compiled for 1.10.2.902, module version = 6.14.99
[ 15704.392] 	Module class: X.Org Video Driver
[ 15704.392] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.392] (II) LoadModule: "radeon"
[ 15704.392] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 15704.393] (II) Module radeon: vendor="X.Org Foundation"
[ 15704.393] 	compiled for 1.10.2.902, module version = 6.14.99
[ 15704.393] 	Module class: X.Org Video Driver
[ 15704.393] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.393] (II) LoadModule: "vesa"
[ 15704.393] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 15704.393] (II) Module vesa: vendor="X.Org Foundation"
[ 15704.393] 	compiled for 1.10.2, module version = 2.3.0
[ 15704.393] 	Module class: X.Org Video Driver
[ 15704.393] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.393] (II) LoadModule: "fbdev"
[ 15704.393] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 15704.393] (II) Module fbdev: vendor="X.Org Foundation"
[ 15704.393] 	compiled for 1.10.0, module version = 0.4.2
[ 15704.393] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.393] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[ 15704.397] (II) VESA: driver for VESA chipsets: vesa
[ 15704.397] (II) FBDEV: driver for framebuffer: fbdev
[ 15704.397] (++) using VT number 8

[ 15704.457] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 15704.457] (II) [KMS] Kernel modesetting enabled.
[ 15704.457] (WW) Falling back to old probe method for vesa
[ 15704.457] (WW) Falling back to old probe method for fbdev
[ 15704.457] (II) Loading sub module "fbdevhw"
[ 15704.457] (II) LoadModule: "fbdevhw"
[ 15704.457] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 15704.457] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 15704.457] 	compiled for 1.10.4, module version = 0.0.2
[ 15704.457] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.457] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[ 15704.457] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[ 15704.457] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 15704.457] (==) RADEON(0): Default visual is TrueColor
[ 15704.457] (==) RADEON(0): RGB weight 888
[ 15704.457] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[ 15704.457] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 3400 Series" (ChipID = 0x95c4)
[ 15704.457] (II) RADEON(0): PCIE card detected
[ 15704.457] drmOpenDevice: node name is /dev/dri/card0
[ 15704.457] drmOpenDevice: open result is 12, (OK)
[ 15704.457] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[ 15704.457] drmOpenDevice: node name is /dev/dri/card0
[ 15704.458] drmOpenDevice: open result is 12, (OK)
[ 15704.458] drmOpenByBusid: drmOpenMinor returns 12
[ 15704.458] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[ 15704.458] (II) Loading sub module "exa"
[ 15704.458] (II) LoadModule: "exa"
[ 15704.458] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 15704.484] (II) Module exa: vendor="X.Org Foundation"
[ 15704.484] 	compiled for 1.10.4, module version = 2.5.0
[ 15704.484] 	ABI class: X.Org Video Driver, version 10.0
[ 15704.484] (II) RADEON(0): KMS Color Tiling: enabled
[ 15704.484] (II) RADEON(0): KMS Pageflipping: enabled
[ 15704.484] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[ 15704.508] (II) RADEON(0): Output VGA-0 has no monitor section
[ 15704.508] (II) RADEON(0): Output LVDS has no monitor section
[ 15704.512] (II) RADEON(0): Output HDMI-0 has no monitor section
[ 15704.536] (II) RADEON(0): EDID for output VGA-0
[ 15704.536] (II) RADEON(0): EDID for output LVDS
[ 15704.536] (II) RADEON(0): Manufacturer: LPL  Model: b80a  Serial#: 0
[ 15704.536] (II) RADEON(0): Year: 2008  Week: 0
[ 15704.536] (II) RADEON(0): EDID Version: 1.3
[ 15704.536] (II) RADEON(0): Digital Display Input
[ 15704.536] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[ 15704.536] (II) RADEON(0): Gamma: 2.20
[ 15704.536] (II) RADEON(0): No DPMS capabilities specified
[ 15704.536] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 15704.536] (II) RADEON(0): First detailed timing is preferred mode
[ 15704.536] (II) RADEON(0): redX: 0.587 redY: 0.344   greenX: 0.337 greenY: 0.561
[ 15704.536] (II) RADEON(0): blueX: 0.153 blueY: 0.122   whiteX: 0.313 whiteY: 0.329
[ 15704.536] (II) RADEON(0): Manufacturer's mask: 0
[ 15704.536] (II) RADEON(0): Supported detailed timing:
[ 15704.537] (II) RADEON(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[ 15704.537] (II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[ 15704.537] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[ 15704.537] (II) RADEON(0): Supported detailed timing:
[ 15704.537] (II) RADEON(0): clock: 96.3 MHz   Image Size:  331 x 207 mm
[ 15704.537] (II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1734 h_border: 0
[ 15704.537] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[ 15704.537] (II) RADEON(0):  FM041&#8364;154WP2
[ 15704.537] (II) RADEON(0): Unknown vendor-specific block 0
[ 15704.537] (II) RADEON(0): EDID (in hex):
[ 15704.537] (II) RADEON(0): 	00ffffffffffff00320c0ab800000000
[ 15704.537] (II) RADEON(0): 	00120103902115780a46559658568f27
[ 15704.537] (II) RADEON(0): 	1f505400000001010101010101010101
[ 15704.537] (II) RADEON(0): 	010101010101a325a02651841a303020
[ 15704.537] (II) RADEON(0): 	36004bcf1000001ba325a02651841a30
[ 15704.537] (II) RADEON(0): 	302036004bcf1000001b000000fe0046
[ 15704.537] (II) RADEON(0): 	4d303431803135345750320a00000000
[ 15704.537] (II) RADEON(0): 	003c587490acc8e4ff02010a202000f1
[ 15704.537] (II) RADEON(0): Printing probed modes for output LVDS
[ 15704.537] (II) RADEON(0): Modeline "1440x900"x60.0   96.35  1440 1488 1520 1734  900 903 909 926 +hsync -vsync (55.6 kHz)
[ 15704.537] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[ 15704.537] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[ 15704.537] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[ 15704.537] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[ 15704.537] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[ 15704.537] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[ 15704.537] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[ 15704.537] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[ 15704.537] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[ 15704.541] (II) RADEON(0): EDID for output HDMI-0
[ 15704.541] (II) RADEON(0): Output VGA-0 disconnected
[ 15704.541] (II) RADEON(0): Output LVDS connected
[ 15704.541] (II) RADEON(0): Output HDMI-0 disconnected
[ 15704.541] (II) RADEON(0): Using exact sizes for initial modes
[ 15704.541] (II) RADEON(0): Output LVDS using initial mode 1440x900
[ 15704.541] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 15704.541] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:faac000
[ 15704.541] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[ 15704.542] (==) RADEON(0): DPI set to (96, 96)
[ 15704.542] (II) Loading sub module "fb"
[ 15704.542] (II) LoadModule: "fb"
[ 15704.542] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 15704.542] (II) Module fb: vendor="X.Org Foundation"
[ 15704.542] 	compiled for 1.10.4, module version = 1.0.0
[ 15704.543] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 15704.543] (II) Loading sub module "ramdac"
[ 15704.543] (II) LoadModule: "ramdac"
[ 15704.543] (II) Module "ramdac" already built-in
[ 15704.543] (II) UnloadModule: "vesa"
[ 15704.543] (II) Unloading vesa
[ 15704.543] (II) UnloadModule: "fbdev"
[ 15704.543] (II) Unloading fbdev
[ 15704.543] (II) UnloadModule: "fbdevhw"
[ 15704.543] (II) Unloading fbdevhw
[ 15704.543] (--) Depth 24 pixmap format is 32 bpp
[ 15704.543] (II) RADEON(0): [DRI2] Setup complete
[ 15704.543] (II) RADEON(0): [DRI2]   DRI driver: r600
[ 15704.543] (II) RADEON(0): Front buffer size: 5200K
[ 15704.543] (II) RADEON(0): VRAM usage limit set to 226339K
[ 15704.543] (==) RADEON(0): Backing store disabled
[ 15704.543] (II) RADEON(0): Direct rendering enabled
[ 15704.543] (II) RADEON(0): Setting EXA maxPitchBytes
[ 15704.543] (II) EXA(0): Driver allocated offscreen pixmaps
[ 15704.543] (II) EXA(0): Driver registered support for the following operations:
[ 15704.543] (II)         Solid
[ 15704.543] (II)         Copy
[ 15704.543] (II)         Composite (RENDER acceleration)
[ 15704.543] (II)         UploadToScreen
[ 15704.543] (II)         DownloadFromScreen
[ 15704.543] (II) RADEON(0): Acceleration enabled
[ 15704.543] (==) RADEON(0): DPMS enabled
[ 15704.543] (==) RADEON(0): Silken mouse enabled
[ 15704.543] (II) RADEON(0): Set up textured video
[ 15704.543] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[ 15704.543] (II) RADEON(0): [XvMC] Extension initialized.
[ 15704.543] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 15704.543] (--) RandR disabled
[ 15704.543] (II) Initializing built-in extension Generic Event Extension
[ 15704.543] (II) Initializing built-in extension SHAPE
[ 15704.543] (II) Initializing built-in extension MIT-SHM
[ 15704.543] (II) Initializing built-in extension XInputExtension
[ 15704.543] (II) Initializing built-in extension XTEST
[ 15704.543] (II) Initializing built-in extension BIG-REQUESTS
[ 15704.543] (II) Initializing built-in extension SYNC
[ 15704.543] (II) Initializing built-in extension XKEYBOARD
[ 15704.543] (II) Initializing built-in extension XC-MISC
[ 15704.543] (II) Initializing built-in extension SECURITY
[ 15704.543] (II) Initializing built-in extension XINERAMA
[ 15704.543] (II) Initializing built-in extension XFIXES
[ 15704.543] (II) Initializing built-in extension RENDER
[ 15704.543] (II) Initializing built-in extension RANDR
[ 15704.544] (II) Initializing built-in extension COMPOSITE
[ 15704.544] (II) Initializing built-in extension DAMAGE
[ 15704.544] (II) Initializing built-in extension GESTURE
[ 15704.549] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
[ 15704.637] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 15704.637] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 15704.637] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 15704.637] (II) AIGLX: enabled GLX_SGI_make_current_read
[ 15704.637] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 15704.637] (II) AIGLX: Loaded and initialized r600
[ 15704.637] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 15704.637] (II) RADEON(0): Setting screen physical size to 381 x 238
[ 15704.675] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15704.701] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[ 15704.701] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 15704.701] (II) LoadModule: "evdev"
[ 15704.701] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.702] (II) Module evdev: vendor="X.Org Foundation"
[ 15704.702] 	compiled for 1.10.2, module version = 2.6.0
[ 15704.702] 	Module class: X.Org XInput Driver
[ 15704.702] 	ABI class: X.Org XInput driver, version 12.3
[ 15704.702] (II) Using input driver 'evdev' for 'Video Bus'
[ 15704.702] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.702] (**) Video Bus: always reports core events
[ 15704.702] (**) Video Bus: Device: "/dev/input/event4"
[ 15704.702] (--) Video Bus: Found keys
[ 15704.702] (II) Video Bus: Configuring as keyboard
[ 15704.702] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input4/event4"
[ 15704.702] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 15704.702] (**) Option "xkb_rules" "evdev"
[ 15704.702] (**) Option "xkb_model" "pc105"
[ 15704.702] (**) Option "xkb_layout" "hu"
[ 15704.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-544CA222969D37ADB2821D0E82B6A6D6FDEF206B.xkm
[ 15704.710] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 15704.710] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 15704.710] (II) Using input driver 'evdev' for 'Power Button'
[ 15704.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.710] (**) Power Button: always reports core events
[ 15704.710] (**) Power Button: Device: "/dev/input/event1"
[ 15704.710] (--) Power Button: Found keys
[ 15704.710] (II) Power Button: Configuring as keyboard
[ 15704.710] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[ 15704.710] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 15704.710] (**) Option "xkb_rules" "evdev"
[ 15704.710] (**) Option "xkb_model" "pc105"
[ 15704.710] (**) Option "xkb_layout" "hu"
[ 15704.711] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 15704.711] (II) No input driver/identifier specified (ignoring)
[ 15704.711] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 15704.711] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 15704.711] (II) Using input driver 'evdev' for 'Sleep Button'
[ 15704.711] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.711] (**) Sleep Button: always reports core events
[ 15704.711] (**) Sleep Button: Device: "/dev/input/event2"
[ 15704.711] (--) Sleep Button: Found keys
[ 15704.711] (II) Sleep Button: Configuring as keyboard
[ 15704.711] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[ 15704.711] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 15704.711] (**) Option "xkb_rules" "evdev"
[ 15704.711] (**) Option "xkb_model" "pc105"
[ 15704.711] (**) Option "xkb_layout" "hu"
[ 15704.713] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[ 15704.713] (II) No input driver/identifier specified (ignoring)
[ 15704.714] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event6)
[ 15704.714] (II) No input driver/identifier specified (ignoring)
[ 15704.714] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event7)
[ 15704.714] (II) No input driver/identifier specified (ignoring)
[ 15704.714] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event8)
[ 15704.715] (II) No input driver/identifier specified (ignoring)
[ 15704.716] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event14)
[ 15704.716] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[ 15704.716] (II) Using input driver 'evdev' for 'PIXART USB OPTICAL MOUSE'
[ 15704.716] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.716] (**) PIXART USB OPTICAL MOUSE: always reports core events
[ 15704.716] (**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event14"
[ 15704.716] (--) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[ 15704.716] (--) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[ 15704.716] (--) PIXART USB OPTICAL MOUSE: Found relative axes
[ 15704.716] (--) PIXART USB OPTICAL MOUSE: Found x and y relative axes
[ 15704.716] (II) PIXART USB OPTICAL MOUSE: Configuring as mouse
[ 15704.716] (II) PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[ 15704.716] (**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[ 15704.716] (**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 15704.716] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input15/event14"
[ 15704.716] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
[ 15704.716] (II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
[ 15704.717] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[ 15704.717] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[ 15704.717] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[ 15704.717] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[ 15704.717] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse2)
[ 15704.717] (II) No input driver/identifier specified (ignoring)
[ 15704.718] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event12)
[ 15704.718] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[ 15704.718] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_2M'
[ 15704.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.718] (**) Laptop_Integrated_Webcam_2M: always reports core events
[ 15704.718] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event12"
[ 15704.718] (--) Laptop_Integrated_Webcam_2M: Found keys
[ 15704.718] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[ 15704.718] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input12/event12"
[ 15704.718] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[ 15704.718] (**) Option "xkb_rules" "evdev"
[ 15704.718] (**) Option "xkb_model" "pc105"
[ 15704.718] (**) Option "xkb_layout" "hu"
[ 15704.722] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 15704.722] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 15704.722] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 15704.722] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.722] (**) AT Translated Set 2 keyboard: always reports core events
[ 15704.722] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 15704.722] (--) AT Translated Set 2 keyboard: Found keys
[ 15704.722] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 15704.722] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 15704.722] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 15704.722] (**) Option "xkb_rules" "evdev"
[ 15704.722] (**) Option "xkb_model" "pc105"
[ 15704.722] (**) Option "xkb_layout" "hu"
[ 15704.723] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event10)
[ 15704.723] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[ 15704.723] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[ 15704.723] (II) LoadModule: "synaptics"
[ 15704.723] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 15704.723] (II) Module synaptics: vendor="X.Org Foundation"
[ 15704.723] 	compiled for 1.10.4, module version = 1.4.1
[ 15704.723] 	Module class: X.Org XInput Driver
[ 15704.723] 	ABI class: X.Org XInput driver, version 12.3
[ 15704.723] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[ 15704.723] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 15704.723] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[ 15704.723] (**) Option "Device" "/dev/input/event10"
[ 15704.726] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[ 15704.726] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[ 15704.726] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[ 15704.726] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[ 15704.726] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[ 15704.728] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[ 15704.728] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[ 15704.732] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[ 15704.732] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[ 15704.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[ 15704.733] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[ 15704.733] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[ 15704.733] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[ 15704.733] (II) No input driver/identifier specified (ignoring)
[ 15704.733] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event9)
[ 15704.734] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[ 15704.734] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[ 15704.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.734] (**) PS/2 Mouse: always reports core events
[ 15704.734] (**) PS/2 Mouse: Device: "/dev/input/event9"
[ 15704.734] (--) PS/2 Mouse: Found 3 mouse buttons
[ 15704.734] (--) PS/2 Mouse: Found relative axes
[ 15704.734] (--) PS/2 Mouse: Found x and y relative axes
[ 15704.734] (II) PS/2 Mouse: Configuring as mouse
[ 15704.734] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[ 15704.734] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 15704.734] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[ 15704.734] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[ 15704.734] (II) PS/2 Mouse: initialized for relative axes.
[ 15704.734] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[ 15704.734] (**) PS/2 Mouse: (accel) acceleration profile 0
[ 15704.734] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[ 15704.734] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[ 15704.735] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[ 15704.735] (II) No input driver/identifier specified (ignoring)
[ 15704.744] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
[ 15704.744] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 15704.744] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 15704.744] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.744] (**) Dell WMI hotkeys: always reports core events
[ 15704.744] (**) Dell WMI hotkeys: Device: "/dev/input/event11"
[ 15704.744] (--) Dell WMI hotkeys: Found keys
[ 15704.744] (II) Dell WMI hotkeys: Configuring as keyboard
[ 15704.744] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event11"
[ 15704.744] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[ 15704.744] (**) Option "xkb_rules" "evdev"
[ 15704.744] (**) Option "xkb_model" "pc105"
[ 15704.744] (**) Option "xkb_layout" "hu"
[ 15704.746] (II) config/udev: Adding input device ITE8708 CIR transceiver (/dev/input/event5)
[ 15704.746] (**) ITE8708 CIR transceiver: Applying InputClass "evdev keyboard catchall"
[ 15704.746] (II) Using input driver 'evdev' for 'ITE8708 CIR transceiver'
[ 15704.746] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15704.746] (**) ITE8708 CIR transceiver: always reports core events
[ 15704.746] (**) ITE8708 CIR transceiver: Device: "/dev/input/event5"
[ 15704.746] (--) ITE8708 CIR transceiver: Found keys
[ 15704.746] (II) ITE8708 CIR transceiver: Configuring as keyboard
[ 15704.746] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input5/event5"
[ 15704.746] (II) XINPUT: Adding extended input device "ITE8708 CIR transceiver" (type: KEYBOARD)
[ 15704.746] (**) Option "xkb_rules" "evdev"
[ 15704.746] (**) Option "xkb_model" "pc105"
[ 15704.746] (**) Option "xkb_layout" "hu"
[ 15738.528] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 15738.546] (II) ITE8708 CIR transceiver: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) Dell WMI hotkeys: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) PS/2 Mouse: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) UnloadModule: "synaptics"
[ 15738.546] (II) Unloading synaptics
[ 15738.546] (II) AT Translated Set 2 keyboard: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) Laptop_Integrated_Webcam_2M: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) PIXART USB OPTICAL MOUSE: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) Sleep Button: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) Power Button: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.546] (II) Video Bus: Close
[ 15738.546] (II) UnloadModule: "evdev"
[ 15738.546] (II) Unloading evdev
[ 15738.561]  ddxSigGiveUp: Closing log

---

### Post by MoreOrLess on 2012-01-18
I don't see anything in the log that looks problematic. What is output of:
```
xrandr -q
```

---

### Post by nero32222 on 2012-01-19
x@x:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1600 x 1600
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1440x900       60.0*+
   1280x800       60.0 +
   1152x864       60.0 +
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)

---

### Post by nero32222 on 2012-01-19
additional - perfomed today:
I'm using dualboot since half a year, have Win7 and Xubuntu on 2 separate partitions of my laptop. But, since 2 weeks ago the bootmgr of Win7 got crashed, I wasn't able to boot Win7, only Xubuntu booted up and so I used Xubuntu until some time, but then I decided to repair the bootmgr of Win7 with the Win7DVD built in repair option, but gave up after several try.
Today I decided to simply reinstall Win7 (coz I wanted both OSs on my laptop), so I have done so. Of course after the installation of Win7, Grub got crashed and I needed to repair it by using 'boot-repair' after booting up the system with the Ubuntu Live DVD. I used the 'Recommended repair' option of 'boot-repair'. After rebooting my system Grub got repaired and I was able to dualboot, so I booted up Xubuntu first. But coz before booting up Xubuntu, Win7 really pissed me off, I decided to format the Win7 partition (with 'gparted') immediately after Xubuntu booted up. (I know this sounds stupid, but this was the time, I decided not tolerating Win anymore on my HDD). But after Xubuntu booted up (before formatting the Win7 partition), I recognized some very strange things happening. The backlight of the LCD was NOT turned up to max! So I immediately checked if the 3D accelerator got somehow deleted or not. To my surprise, 'fglrx' was installed correctly, 'glxinfo' also confirmed that I have 3D acceleration. But I got paralell some errors too: During the boot up section some strange strong pop sound come out of the speaker of my laptop, plus when I pushed the physical power off button on my laptop in Xubuntu, no log-out screen selection window came up (where I can choose to restart, shut down, hibernate etc. the system), but this time the screen gone black and the system got frozen. Only a hard shut-dowm solved this issue. Plus one more side-down appeared: the 'cpufreq' command/app. told me, that the HW does not support to change the CPU's freq. etc. :-X Very strange things happend. So I formatted the Win7 partition and restarted Xubuntu, but the same strange things happend. I then not only formatted the Win7 part, but also deleted and created instead an ext4 partition and after all that I repaired Grub again with 'boot-repair', but this time I selected to restore MBR and then restore Grub too. Then I restarted my system and the old conditions appared, that is, the 'fglrx' is installed, but the backlight of the LCD will be turned up aut. to max. after every restart, no strange pop sound appears and the power off button selection thing also works.  
I really don't know what happend, what caused all these things (a simple Win7 installation or a Grub repair or MBR repair? :-S )but I really wish to know why my LCD backlight worked well while unfortunately other things gone wrong. :-X

---

