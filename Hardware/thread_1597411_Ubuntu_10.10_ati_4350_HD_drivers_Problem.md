---
title: "Ubuntu 10.10 ati 4350 HD drivers Problem"
date: 2010-10-15
forum: Hardware
---

### Post by Syl4r on 2010-10-15
Hi!
I'm new to this forum, and i'm quite new also to Ubuntu :P
So, here's my problem: I just installed Ubuntu 10.10, and, as always, it told me that there were proprietary drivers for my ati 4350 HD, so i installed them, but at next reboot, it stays in command line, for a few minutes. After this 2 or 3 minutes, it starts normally. During this minutes, if i try to launch (from command line) some program (like gedit), it gives me a gtk error saying something like "unable to show display". If i uninstall the drivers, everything is again ok...
In the last few days (before installing ubuntu 10.10), i started having the same problem with Lucid Lynx...
Hope somebody can help me... i really need video drivers...
Thanks in advance :)
(Sorry for my English, i'm Italian :P)

---

### Post by Claus7 on 2010-10-15
Bona Sera!

Hello and welcome to the forums!

First of: since you can work your ubu box without any problems why do you want to install the drivers in the first place?

There are many things you could try, yet if you were more specific on the problem you are facing then you would give us more info in order to help you out. I had also problems with a similar card and I had to tamper with a file named xorg.conf under /etc/X11 using the drivers you are mentioning. 

The first thing you could try is to type:
```
sudo aticonfig --initial 
```

in a terminal (open from Applications -> Accessories) and reboot. Hope this will fix your problem.

I have to admit that I have not heard a booting process that emits errors, delays and then continues normally.

Hope I gave some hints,
Regards!

---

### Post by Syl4r on 2010-10-15
Hi, and thanks for the answer!
I need the drivers for a few reasons...for setting the resolution to something higher, for playing some games, and for using some applications such as blender and other graphics stuff... 
Anyways, if i type
```
sudo aticonfig --initial
```i get this:
```

Found fglrx primary device section
 Unable to find any supported Screen sections

```Here's the content of the file /etc/X11/Xorg.conf, if it helps...

```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

```Thanks again for your reply!

---

### Post by Claus7 on 2010-10-15
Hello,

so you have a xorg.conf file and you know about this. Ok, since you have then let's do some tweaking.

Take mine here:
[http://ubuntuforums.org/showpost.php?p=9940327&postcount=15](http://ubuntuforums.org/showpost.php?p=9940327&postcount=15)

and as a type of card use the output of the command (after the : mark):
```
lspci | grep VGA
```

for resolution refresh rates and actual resolution you have to use your own from your manufacturer. First fix everything else and last leave these things. Hope you will be able to understand what you have to change so as to make your xorg file similar to mine. 

You are welcome,
Regards!

---

### Post by Syl4r on 2010-10-15
Thanks for your time!
So, here's what i understood...
I did a backup copy of my xorg.conf file, then i replaced mines with yours, i opened it and everywhere i found 
```

"ATI Technologies Inc Redwood [Radeon HD 5670]"

```i replaced it with
```

"ATI Technologies Inc RV710 [Radeon HD 4350]"

```(that its the output of the command you gave me in the previous post) ...but it doesn't change anything...

---

### Post by Claus7 on 2010-10-15
Hello,

now try to type sudo aticonfig --initial 

Also when you say nothing what do mean? It did not produce any errors?

With the command above, if you have a descent xorg file it smoothes some things. Do not worry about backing things up for now as it is done automatically. Sorry for not mentioning before, yet the file you had was pretty basic. 

Also under the modes section use a resolution that is supported by your monitor.

Regards!

---

### Post by Syl4r on 2010-10-15
Sorry for the late reply.
I tried giving "sudo aticonfig --initial" and i keep getting 
```

Found fglrx primary device section
 Unable to find any supported Screen sections

```

if i give the command
```

sudo aticonfig --initial --input=/etc/X11/xorg.conf

```
i get the following
```

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

```
but on reboot it keeps giving me the same problem...it stays in command line...
i forgot to mention that on reboot, when i get to the point where it stays in command line, i can do my login, and use my ubuntu, but all in command line (for a few minutes)...i dont know if this information can be any helpful...
sorry if i'm not very clear, but im not able to express myself in english...
Thanks.

---

### Post by Claus7 on 2010-10-15
Hello,

two things:

1) could you upload your latest xorg file?

2) on reboot (because every time you tamper with xorg is the best way to see what you have done) if you type:
```
startx
```

could you tell us what errors do you get?

Seems is a matter of trial and error here...

Regards!

---

### Post by Syl4r on 2010-10-15
here's my latest xorg.conf file:
```

Section "ServerLayout"
	Identifier     "ATI Technologies Inc RV710 [Radeon HD 4350]"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "fglrx"
	Option	    "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV710 [Radeon HD 4350]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "ATI Technologies Inc RV710 [Radeon HD 4350]"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1152x864"
	EndSubSection
EndSection

```

i think we're close to a solution: if i give the command
```

startx

```
(on reboot), i start correctly my ubuntu gui without waiting this 2 or 3 minutes, but after 2 or 3 minutes my gui is started, it turns off my monitor for a second (like if it is restarting my gui) and then i listen again my ubuntu login sound...

---

### Post by Claus7 on 2010-10-15
Hello,

a quick one:

in section server layout you have forgotten the " in the end of the second line Identifier.

Check this out.

Also go to System -> Preferences -> Monitor and see if you get the right resolutions and refresh rates and try to make permanent an option that fits your needs.

Regards!

---

### Post by Syl4r on 2010-10-15
...i keep getting the same problem ](*,)

---

### Post by Claus7 on 2010-10-15
Hello,

since startx is working let's see what we can do:

Go to System->Administration->Log file Viewer and post the Xorg.0.log file to see what is written there.

Also, while you are typing startx, or while you are booting, have you come across any errors (please post exactly what you get, while booting).

Yet the above file would suffice for the moment.

Regards!

---

### Post by Syl4r on 2010-10-15
so...here's the xorg.0.log file:
```

[   133.434] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   133.435] X Protocol Version 11, Revision 0
[   133.435] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   133.435] Current Operating System: Linux COMPUTER 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686
[   133.435] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a22bfd01-3acc-4978-9283-bc4ea1167a6e ro quiet splash
[   133.435] Build Date: 16 September 2010  05:39:22PM
[   133.435] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   133.452] Current version of pixman: 0.18.4
[   133.452] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   133.452] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   133.452] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 15 19:09:46 2010
[   133.476] (==) Using config file: "/etc/X11/xorg.conf"
[   133.476] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   133.528] (==) ServerLayout "ATI Technologies Inc RV710 [Radeon HD 4350]"
[   133.529] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[   133.529] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[   133.529] (**) |   |-->Device "ATI Technologies Inc RV710 [Radeon HD 4350]"
[   133.529] (==) Automatically adding devices
[   133.529] (==) Automatically enabling devices
[   133.579] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   133.579] 	Entry deleted from font path.
[   133.614] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   133.614] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   133.614] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   133.614] (II) Loader magic: 0x81f8e00
[   133.614] (II) Module ABI versions:
[   133.614] 	X.Org ANSI C Emulation: 0.4
[   133.614] 	X.Org Video Driver: 8.0
[   133.614] 	X.Org XInput driver : 11.0
[   133.614] 	X.Org Server Extension : 4.0
[   133.617] (--) PCI:*(0:1:0:0) 1002:954f:1043:02a8 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[   133.617] (II) Open ACPI successful (/var/run/acpid.socket)
[   133.617] (II) "extmod" will be loaded by default.
[   133.618] (II) "dbe" will be loaded by default.
[   133.618] (II) "glx" will be loaded by default.
[   133.618] (II) "record" will be loaded by default.
[   133.618] (II) "dri" will be loaded by default.
[   133.618] (II) "dri2" will be loaded by default.
[   133.618] (II) LoadModule: "extmod"
[   133.657] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   133.669] (II) Module extmod: vendor="X.Org Foundation"
[   133.669] 	compiled for 1.9.0, module version = 1.0.0
[   133.669] 	Module class: X.Org Server Extension
[   133.669] 	ABI class: X.Org Server Extension, version 4.0
[   133.670] (II) Loading extension MIT-SCREEN-SAVER
[   133.670] (II) Loading extension XFree86-VidModeExtension
[   133.670] (II) Loading extension XFree86-DGA
[   133.670] (II) Loading extension DPMS
[   133.670] (II) Loading extension XVideo
[   133.670] (II) Loading extension XVideo-MotionCompensation
[   133.670] (II) Loading extension X-Resource
[   133.670] (II) LoadModule: "dbe"
[   133.670] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   133.676] (II) Module dbe: vendor="X.Org Foundation"
[   133.676] 	compiled for 1.9.0, module version = 1.0.0
[   133.676] 	Module class: X.Org Server Extension
[   133.676] 	ABI class: X.Org Server Extension, version 4.0
[   133.676] (II) Loading extension DOUBLE-BUFFER
[   133.676] (II) LoadModule: "glx"
[   133.676] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   133.715] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   133.716] 	compiled for 7.6.0, module version = 1.0.0
[   133.716] (II) Loading extension GLX
[   133.716] (II) LoadModule: "record"
[   133.717] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   133.728] (II) Module record: vendor="X.Org Foundation"
[   133.728] 	compiled for 1.9.0, module version = 1.13.0
[   133.728] 	Module class: X.Org Server Extension
[   133.728] 	ABI class: X.Org Server Extension, version 4.0
[   133.728] (II) Loading extension RECORD
[   133.728] (II) LoadModule: "dri"
[   133.728] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   133.744] (II) Module dri: vendor="X.Org Foundation"
[   133.744] 	compiled for 1.9.0, module version = 1.0.0
[   133.744] 	ABI class: X.Org Server Extension, version 4.0
[   133.744] (II) Loading extension XFree86-DRI
[   133.744] (II) LoadModule: "dri2"
[   133.745] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   133.759] (II) Module dri2: vendor="X.Org Foundation"
[   133.759] 	compiled for 1.9.0, module version = 1.2.0
[   133.759] 	ABI class: X.Org Server Extension, version 4.0
[   133.759] (II) Loading extension DRI2
[   133.759] (II) LoadModule: "fglrx"
[   133.759] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   133.998] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   134.011] 	compiled for 1.4.99.906, module version = 8.78.30
[   134.011] 	Module class: X.Org Video Driver
[   134.029] (II) Loading sub module "fglrxdrm"
[   134.029] (II) LoadModule: "fglrxdrm"
[   134.030] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   134.059] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   134.059] 	compiled for 1.8.99.905, module version = 8.78.30
[   134.059] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[   134.059] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[   134.059] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[   134.059] (++) using VT number 7

[   134.068] (WW) Falling back to old probe method for fglrx
[   134.179] (II) Loading PCS database from /etc/ati/amdpcsdb
[   134.180] (--) Chipset Supported AMD Graphics Processor (0x954F) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[   134.181] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[   134.182] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   134.182] (II) AMD Video driver is signed
[   134.183] (II) fglrx(0): pEnt->device->identifier=0x9b0b690
[   134.183] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[   134.184] (II) Loading sub module "vgahw"
[   134.184] (II) LoadModule: "vgahw"
[   134.185] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   134.209] (II) Module vgahw: vendor="X.Org Foundation"
[   134.210] 	compiled for 1.9.0, module version = 0.1.0
[   134.210] 	ABI class: X.Org Video Driver, version 8.0
[   134.210] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   134.210] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   134.210] (==) fglrx(0): Default visual is TrueColor
[   134.210] (**) fglrx(0): Option "DPMS" "true"
[   134.210] (==) fglrx(0): RGB weight 888
[   134.210] (II) fglrx(0): Using 8 bits per RGB 
[   134.210] (==) fglrx(0): Buffer Tiling is ON
[   134.228] (II) Loading sub module "fglrxdrm"
[   134.228] (II) LoadModule: "fglrxdrm"
[   134.228] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   134.233] ukiDynamicMajor: found major device number 250
[   134.233] ukiDynamicMajor: found major device number 250
[   134.233] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   134.233] ukiOpenDevice: node name is /dev/ati/card0
[   134.233] ukiOpenDevice: open result is 11, (OK)
[   134.233] ukiOpenByBusid: ukiOpenMinor returns 11
[   134.233] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   134.233] (==) fglrx(0): NoAccel = NO
[   134.234] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[   134.234] (--) fglrx(0): Chipset: "ATI Radeon HD 4300/4500 Series" (Chipset = 0x954f)
[   134.234] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x02a8)
[   134.234] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[   134.234] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[   134.234] (--) fglrx(0): MMIO registers at 0xfeaf0000
[   134.234] (--) fglrx(0): I/O port at 0x0000d000
[   134.234] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   134.262] (II) fglrx(0): AC Adapter is used
[   134.321] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   134.444] (II) Loading sub module "vbe"
[   134.444] (II) LoadModule: "vbe"
[   134.465] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   134.475] (II) Module vbe: vendor="X.Org Foundation"
[   134.475] 	compiled for 1.9.0, module version = 1.1.0
[   134.475] 	ABI class: X.Org Video Driver, version 8.0
[   134.476] (II) fglrx(0): VESA BIOS detected
[   134.476] (II) fglrx(0): VESA VBE Version 3.0
[   134.476] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   134.476] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[   134.476] (II) fglrx(0): VESA VBE OEM Software Rev: 11.20
[   134.476] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   134.476] (II) fglrx(0): VESA VBE OEM Product: RV710
[   134.476] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   134.512] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[   134.513] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[   134.513] (II) fglrx(0): PCIE card detected
[   134.513] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   134.513] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   134.518] (II) fglrx(0): Using adapter: 1:0.0.
[   134.541] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[   134.622] (II) fglrx(0): Interrupt handler installed at IRQ 44.
[   134.623] (II) fglrx(0): RandR 1.2 support is enabled!
[   134.623] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   134.623] (==) fglrx(0): Center Mode is disabled 
[   134.623] (II) Loading sub module "fb"
[   134.623] (II) LoadModule: "fb"
[   134.624] (II) Loading /usr/lib/xorg/modules/libfb.so
[   134.636] (II) Module fb: vendor="X.Org Foundation"
[   134.636] 	compiled for 1.9.0, module version = 1.0.0
[   134.636] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   134.636] (==) fglrx(0): Active stereo disabled
[   134.636] (II) Loading sub module "ddc"
[   134.636] (II) LoadModule: "ddc"
[   134.636] (II) Module "ddc" already built-in
[   135.582] (II) fglrx(0): Finished Initialize PPLIB!
[   135.604] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[   135.604] (II) fglrx(0): Output DFP2 has no monitor section
[   135.605] (II) fglrx(0): Output CRT1 has no monitor section
[   135.605] (II) fglrx(0): Output CRT2 has no monitor section
[   135.623] (II) Loading sub module "ddc"
[   135.623] (II) LoadModule: "ddc"
[   135.623] (II) Module "ddc" already built-in
[   135.623] (II) fglrx(0): Connected Display0: CRT1
[   135.623] (II) fglrx(0): Display0 EDID data ---------------------------
[   135.623] (II) fglrx(0): Manufacturer: CPQ  Model: 1399  Serial#: 6275684
[   135.623] (II) fglrx(0): Year: 2001  Week: 39
[   135.623] (II) fglrx(0): EDID Version: 1.3
[   135.623] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[   135.623] (II) fglrx(0): Sync:  Separate
[   135.623] (II) fglrx(0): Max Image Size [cm]: horiz.: 32  vert.: 24
[   135.623] (II) fglrx(0): Gamma: 1.99
[   135.623] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   135.623] (II) fglrx(0): First detailed timing not preferred mode in violation of standard!
[   135.623] (II) fglrx(0): redX: 0.650 redY: 0.317   greenX: 0.273 greenY: 0.613
[   135.624] (II) fglrx(0): blueX: 0.142 blueY: 0.058   whiteX: 0.283 whiteY: 0.298
[   135.624] (II) fglrx(0): Supported established timings:
[   135.624] (II) fglrx(0): 720x400@70Hz
[   135.624] (II) fglrx(0): 640x480@60Hz
[   135.624] (II) fglrx(0): 640x480@72Hz
[   135.624] (II) fglrx(0): 640x480@75Hz
[   135.624] (II) fglrx(0): 800x600@60Hz
[   135.624] (II) fglrx(0): 800x600@72Hz
[   135.624] (II) fglrx(0): 800x600@75Hz
[   135.624] (II) fglrx(0): 832x624@75Hz
[   135.624] (II) fglrx(0): 1024x768@60Hz
[   135.624] (II) fglrx(0): 1024x768@70Hz
[   135.624] (II) fglrx(0): 1024x768@75Hz
[   135.624] (II) fglrx(0): Manufacturer's mask: 0
[   135.624] (II) fglrx(0): Supported standard timings:
[   135.624] (II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[   135.624] (II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[   135.624] (II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[   135.624] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   135.624] (II) fglrx(0): Supported detailed timing:
[   135.624] (II) fglrx(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
[   135.624] (II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
[   135.624] (II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
[   135.624] (II) fglrx(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 115 MHz
[   135.624] (II) fglrx(0): Monitor name: COMPAQ S720
[   135.624] (II) fglrx(0): Unknown vendor-specific block d
[   135.624] (II) fglrx(0): EDID (in hex):
[   135.624] (II) fglrx(0): 	00ffffffffffff000e11991364c25f00
[   135.624] (II) fglrx(0): 	270b010368201863e89079a651469d24
[   135.624] (II) fglrx(0): 	0e484cadee0031594559615981800101
[   135.624] (II) fglrx(0): 	010101010101ea240060410028303060
[   135.624] (II) fglrx(0): 	130038ea1000001e000000fd0032a01e
[   135.624] (II) fglrx(0): 	460b000a202020202020000000fc0043
[   135.624] (II) fglrx(0): 	4f4d50415120533732300a200000000d
[   135.624] (II) fglrx(0): 	0002027f04e80730152600c302d800e6
[   135.624] (II) fglrx(0): End of Display0 EDID data --------------------
[   135.807] (II) fglrx(0): Output DFP1 disconnected
[   135.807] (II) fglrx(0): Output DFP2 disconnected
[   135.807] (II) fglrx(0): Output CRT1 connected
[   135.807] (II) fglrx(0): Output CRT2 disconnected
[   135.807] (II) fglrx(0): Using user preference for initial modes
[   135.807] (II) fglrx(0): Output CRT1 using initial mode 1152x864
[   135.807] (II) fglrx(0): DPI set to (96, 96)
[   135.807] (II) fglrx(0): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 1 displays connected.
[   135.807] (==) fglrx(0):  PseudoColor visuals disabled
[   135.807] (II) Loading sub module "ramdac"
[   135.807] (II) LoadModule: "ramdac"
[   135.807] (II) Module "ramdac" already built-in
[   135.807] (==) fglrx(0): NoDRI = NO
[   135.807] (==) fglrx(0): Capabilities: 0x00000000
[   135.807] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   135.807] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   135.807] (==) fglrx(0): UseFastTLS=0
[   135.807] (==) fglrx(0): BlockSignalsOnLock=1
[   135.807] (--) Depth 24 pixmap format is 32 bpp
[   135.807] (II) Loading extension ATIFGLRXDRI
[   135.808] (II) fglrx(0): doing swlDriScreenInit
[   135.808] (II) fglrx(0): swlDriScreenInit for fglrx driver
[   135.808] ukiDynamicMajor: found major device number 250
[   135.808] ukiDynamicMajor: found major device number 250
[   135.808] ukiDynamicMajor: found major device number 250
[   135.808] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   135.808] ukiOpenDevice: node name is /dev/ati/card0
[   135.808] ukiOpenDevice: open result is 17, (OK)
[   135.808] ukiOpenByBusid: ukiOpenMinor returns 17
[   135.808] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   135.808] (II) fglrx(0): [uki] DRM interface version 1.0
[   135.808] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[   135.808] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[   135.808] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb779b000
[   135.808] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[   135.808] (II) fglrx(0): [uki] added 1 reserved context for kernel
[   135.808] (II) fglrx(0): swlDriScreenInit done
[   135.808] (II) fglrx(0): Kernel Module Version Information:
[   135.808] (II) fglrx(0):     Name: fglrx
[   135.808] (II) fglrx(0):     Version: 8.78.30
[   135.808] (II) fglrx(0):     Date: Sep 20 2010
[   135.808] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[   135.808] (II) fglrx(0): Kernel Module version matches driver.
[   135.808] (II) fglrx(0): Kernel Module Build Time Information:
[   135.808] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-22-generic
[   135.808] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[   135.808] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[   135.808] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[   135.808] (II) fglrx(0): [uki] register handle = 0x00004000
[   135.841] (II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
[   135.841] (II) fglrx(0): DRI initialization successfull
[   135.841] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010a8000
[   135.887] (II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
[   135.887] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
[   135.887] (II) fglrx(0): Largest offscreen area available: 1664 x 960
[   135.889] (==) fglrx(0): Backing store disabled
[   135.889] (II) Loading extension FGLRXEXTENSION
[   135.889] (**) fglrx(0): DPMS enabled
[   135.889] (II) fglrx(0): Initialized in-driver Xinerama extension
[   135.889] (**) fglrx(0): Textured Video is enabled.
[   135.889] (II) LoadModule: "glesx"
[   135.890] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[   136.046] (II) Module glesx: vendor="X.Org Foundation"
[   136.046] 	compiled for 1.8.99.905, module version = 1.0.0
[   136.046] (II) Loading extension GLESX
[   136.046] (II) fglrx(0): GLESX enableFlags = 528
[   136.047] (II) fglrx(0): GLESX is enabled
[   136.047] (II) fglrx(0): Acceleration enabled
[   136.047] (II) LoadModule: "amdxmm"
[   136.047] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[   136.059] (II) Module amdxmm: vendor="X.Org Foundation"
[   136.059] 	compiled for 1.8.99.905, module version = 1.0.0
[   136.060] (II) Loading extension AMDXVOPL
[   136.085] (II) fglrx(0): UVD2 feature is available
[   136.090] (II) fglrx(0): Enable composite support successfully
[   136.090] (WW) fglrx(0): Option "fglrx" is not used
[   136.090] (WW) fglrx(0): Option "Generic Autodetecting Monitor" is not used
[   136.090] (II) fglrx(0): X context handle = 0x1
[   136.090] (II) fglrx(0): [DRI] installation complete
[   136.090] (==) fglrx(0): Silken mouse enabled
[   136.115] (==) fglrx(0): Using HW cursor of display infrastructure!
[   136.115] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[   136.208] (--) RandR disabled
[   136.208] (II) Initializing built-in extension Generic Event Extension
[   136.208] (II) Initializing built-in extension SHAPE
[   136.208] (II) Initializing built-in extension MIT-SHM
[   136.208] (II) Initializing built-in extension XInputExtension
[   136.208] (II) Initializing built-in extension XTEST
[   136.208] (II) Initializing built-in extension BIG-REQUESTS
[   136.208] (II) Initializing built-in extension SYNC
[   136.209] (II) Initializing built-in extension XKEYBOARD
[   136.209] (II) Initializing built-in extension XC-MISC
[   136.209] (II) Initializing built-in extension SECURITY
[   136.209] (II) Initializing built-in extension XINERAMA
[   136.209] (II) Initializing built-in extension XFIXES
[   136.209] (II) Initializing built-in extension RENDER
[   136.209] (II) Initializing built-in extension RANDR
[   136.209] (II) Initializing built-in extension COMPOSITE
[   136.209] (II) Initializing built-in extension DAMAGE
[   136.209] (II) Initializing built-in extension GESTURE
[   136.217] ukiDynamicMajor: found major device number 250
[   136.217] ukiDynamicMajor: found major device number 250
[   136.218] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   136.218] ukiOpenDevice: node name is /dev/ati/card0
[   136.218] ukiOpenDevice: open result is 18, (OK)
[   136.218] ukiOpenByBusid: ukiOpenMinor returns 18
[   136.218] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   137.161] (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
[   137.165] (II) GLX: Initialized DRI GL provider for screen 0
[   137.414] (II) fglrx(0): Enable the clock gating!
[   137.414] (II) fglrx(0): Setting screen physical size to 304 x 228
[   137.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   137.666] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   137.666] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   137.666] (II) LoadModule: "evdev"
[   137.667] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   137.703] (II) Module evdev: vendor="X.Org Foundation"
[   137.703] 	compiled for 1.9.0, module version = 2.3.2
[   137.703] 	Module class: X.Org XInput Driver
[   137.703] 	ABI class: X.Org XInput driver, version 11.0
[   137.704] (**) Power Button: always reports core events
[   137.704] (**) Power Button: Device: "/dev/input/event1"
[   137.704] (II) Power Button: Found keys
[   137.704] (II) Power Button: Configuring as keyboard
[   137.704] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   137.704] (**) Option "xkb_rules" "evdev"
[   137.704] (**) Option "xkb_model" "evdev"
[   137.704] (**) Option "xkb_layout" "it"
[   137.710] (II) XKB: reuse xkmfile /var/lib/xkb/server-35DF0DEC488035CD7337E5EF69F018BFAFADCAC5.xkm
[   137.728] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   137.728] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   137.728] (**) Power Button: always reports core events
[   137.728] (**) Power Button: Device: "/dev/input/event0"
[   137.728] (II) Power Button: Found keys
[   137.728] (II) Power Button: Configuring as keyboard
[   137.728] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   137.728] (**) Option "xkb_rules" "evdev"
[   137.729] (**) Option "xkb_model" "evdev"
[   137.729] (**) Option "xkb_layout" "it"
[   137.734] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/event2)
[   137.735] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: Applying InputClass "evdev pointer catchall"
[   137.735] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: always reports core events
[   137.735] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: Device: "/dev/input/event2"
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found 9 mouse buttons
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found scroll wheel(s)
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found relative axes
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found x and y relative axes
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Configuring as mouse
[   137.735] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: YAxisMapping: buttons 4 and 5
[   137.735] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   137.735] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse® 1.00" (type: MOUSE)
[   137.735] (II) Microsoft Microsoft Wireless Optical Mouse® 1.00: initialized for relative axes.
[   137.736] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/mouse0)
[   137.736] (II) No input driver/identifier specified (ignoring)
[   137.738] (II) config/udev: Adding input device CHICONY USB NetVista Full Width Keyboard (/dev/input/event3)
[   137.738] (**) CHICONY USB NetVista Full Width Keyboard: Applying InputClass "evdev keyboard catchall"
[   137.738] (**) CHICONY USB NetVista Full Width Keyboard: always reports core events
[   137.738] (**) CHICONY USB NetVista Full Width Keyboard: Device: "/dev/input/event3"
[   137.738] (II) CHICONY USB NetVista Full Width Keyboard: Found keys
[   137.738] (II) CHICONY USB NetVista Full Width Keyboard: Configuring as keyboard
[   137.738] (II) XINPUT: Adding extended input device "CHICONY USB NetVista Full Width Keyboard" (type: KEYBOARD)
[   137.738] (**) Option "xkb_rules" "evdev"
[   137.738] (**) Option "xkb_model" "evdev"
[   137.738] (**) Option "xkb_layout" "it"
[   137.836] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[   142.073] (II) fglrx(0): EDID vendor "CPQ", prod id 5017
[   142.074] (II) fglrx(0): Using EDID range info for horizontal sync
[   142.074] (II) fglrx(0): Using EDID range info for vertical refresh
[   142.074] (II) fglrx(0): Printing DDC gathered Modelines:
[   142.074] (II) fglrx(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   142.074] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   142.074] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   142.074] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   142.074] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   142.074] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   142.074] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   142.074] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   142.074] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   142.074] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   142.074] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   142.074] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   142.074] (II) fglrx(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   142.074] (II) fglrx(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   142.074] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   142.532] (II) fglrx(0): EDID vendor "CPQ", prod id 5017
[   142.532] (II) fglrx(0): Using hsync ranges from config file
[   142.532] (II) fglrx(0): Using vrefresh ranges from config file
[   142.532] (II) fglrx(0): Printing DDC gathered Modelines:
[   142.532] (II) fglrx(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   142.532] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   142.532] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   142.532] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   142.532] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   142.532] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   142.532] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   142.532] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   142.532] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   142.532] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   142.532] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   142.532] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   142.532] (II) fglrx(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   142.532] (II) fglrx(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   142.532] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   143.122] (II) fglrx(0): EDID vendor "CPQ", prod id 5017
[   143.122] (II) fglrx(0): Using hsync ranges from config file
[   143.122] (II) fglrx(0): Using vrefresh ranges from config file
[   143.122] (II) fglrx(0): Printing DDC gathered Modelines:
[   143.122] (II) fglrx(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   143.122] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   143.122] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   143.122] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   143.122] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   143.122] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   143.122] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   143.122] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   143.122] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   143.122] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   143.122] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   143.122] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   143.122] (II) fglrx(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   143.122] (II) fglrx(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   143.122] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   149.164] (II) fglrx(0): EDID vendor "CPQ", prod id 5017
[   149.164] (II) fglrx(0): Using hsync ranges from config file
[   149.164] (II) fglrx(0): Using vrefresh ranges from config file
[   149.164] (II) fglrx(0): Printing DDC gathered Modelines:
[   149.164] (II) fglrx(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   149.164] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   149.164] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   149.164] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   149.164] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   149.164] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   149.164] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   149.164] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   149.164] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   149.164] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   149.164] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   149.164] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   149.164] (II) fglrx(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   149.164] (II) fglrx(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   149.164] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   152.628] (II) fglrx(0): EDID vendor "CPQ", prod id 5017
[   152.628] (II) fglrx(0): Using hsync ranges from config file
[   152.628] (II) fglrx(0): Using vrefresh ranges from config file
[   152.628] (II) fglrx(0): Printing DDC gathered Modelines:
[   152.628] (II) fglrx(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   152.628] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   152.628] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   152.628] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   152.628] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   152.628] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   152.628] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   152.629] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   152.629] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   152.629] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   152.629] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   152.629] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   152.629] (II) fglrx(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   152.629] (II) fglrx(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   152.629] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)


```
and during the boot (just before my problem happens) i get this errors:
```

[10.092022] tmp_tis 00:0b: tmp_transmit: tmp_send: error 4294967234
[12.092025] tmp_tis 00:0b: tmp_transmit: tmp_send: error 4294967234

```
and another one in wich it changes just the first number (i can't read that one, it's too fast)

---

### Post by Claus7 on 2010-10-15
Hello,

please give the entire output of the command:
lspci | grep VGA

I would like to see the bus id of your card, which is there that you get the most warnings.

Regards!

---

### Post by Syl4r on 2010-10-15
Here's what i get when i give that command ("lspci | grep VGA"):
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]

```

---

### Post by Claus7 on 2010-10-15
Hello,

the id seems to be correct, yet since I do not have one in my xorg file try to remove it and see what you will get. Up to now this is all I can think of.

Regards!

edit: just add in the end of your xorg.conf file this:

> Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

---

### Post by Syl4r on 2010-10-16
hi,
thanks again, but neither this has worked for me...

---

### Post by Claus7 on 2010-10-16
Hello,

there are two more things I can think of:

1) why do you use in your xorg.conf file a resolution like "1152x864"? According to the xorg.0.log this is nowhere to be found so try something else.

2) the other has to do with conflicts with other open source drivers installed in your system. Maybe removing these would be a nice idea. 

Yet I would insist on the first one. This is very important so as to have a good resolution.

Hope I'm driving you to the right direction
and that you will solve your problem soon,
Regards!

---

### Post by Syl4r on 2010-10-18
Hi, i'll try to change resolution when i get home (i'm at school now), anyways, i use 1152x864 because i have an old monitor and i tried to use 1280x1024 and it is to big.
For the second point...how should i uninstall the open source drivers??
Thanks again for your help!

---

### Post by Claus7 on 2010-10-19
Hello,

did it work, the resolution thing...

In case you face some conflicts with the other drivers you could open synaptic and remove from there the packages that are called like:
xserver-....(vesa, nouveau, nv, ati, radeon, nvidia)

that way you will use only the fglrx one. In case you want them back, you remove the fglrx driver (that you don't want though) and reinstall the ati, radeon and vesa ones, because the other are not needed anyway.

You are very welcome,
Regards!

---

### Post by Syl4r on 2010-10-21
Hi,
i changed the resolution, but it didn't change anything...i also tried removing the packages you mentioned, but there are a lot more called "xserver"

[IMG]http://img836.imageshack.us/img836/5076/synaptic.png[/IMG]

should i remove all of those packages??

---

### Post by Claus7 on 2010-10-22
Hello,

just the ones that have in their name the word I described you before, mainly the ati and radeon ones, because in a guide about fglrx and ubuntu it was mentioned that these might conflict with the fglrx driver. In my new installation these are installed though and I do not get some problems that's why I mentioned this to you as a last resort.

I have to admit that I cannot think of anything else... Maybe someone else would point you to the right direction. I'll keep an eye on this, yet I do not know anything else to propose.

Maybe a new installation from a new cd might solve the problem...

Good luck,
Regards!

---

### Post by Syl4r on 2010-10-24
Thanks for all your help! i hope in some ati drivers update that resolves my problem...but, at least now i have the "startx" command to start my system without waiting!
Thanks again for your help!
Regards!

---

### Post by Claus7 on 2010-10-24
Hello,

> **Syl4r said:**
> Thanks for all your help! i hope in some ati drivers update that resolves my problem...but, at least now i have the "startx" command to start my system without waiting!
Thanks again for your help!
Regards!

When I had to type startx in order to get my screen on, I had to tamper with the monitor lines of my xorg.conf. These were the ones that were causing this problem.

Since your monitor is an old one, I do not think that you will find a solution with just an update. You are very close on setting this once and for all. At least this is what I can get...

Once again you might have to tamper the monitor section. I do not know for sure, yet here:
[http://www.gentoo.org/doc/en/xorg-config.xml](http://www.gentoo.org/doc/en/xorg-config.xml)

you will be able to find some info on vga and dvi one's. Since I cannot tamper with it, I cannot give you more info on that. It is just a thought.

Glad that your system is working a little bit better than before. Hope you will be able to fix it with a permanent solution.

Molto piacere! 
Regards!

---

### Post by coffeecat on 2010-10-24
@Syl4r, I must admit I haven't ploughed through the whole of this thread, so this may have been covered, but unless you are a gamer your first mistake was to install the proprietary driver. I'm posting from a system with the same ATI Radeon HD 4350 graphics chipset as you. I am running 10.10/Maverick and I am using the open-source default driver. I have no problems with video - in fact I have no problems. And I get sufficient 3d acceleration for compiz. There is no configuration to do, no xorg.conf to edit. I don't even have to set the monitor resolution - the system does that for me.

I don't know whether you've thought of reverting to the open source driver or how easy this will be with what you've had to do with your system, but I'll leave this thought with you.

---

### Post by dieselfan on 2010-10-27
I have an ACER TravelMate with an ATI 2400. I get the EXACT same error as the original poster, 

- NO FANCY resolution or screen just a plain laptop
- X starts after around 120 seconds byitself OR I can login and type startx

Just prior to X starting by itself ie after 120 secs it says
"tpm_transmit:tpm_send error -62" then starts by itself after another 60 seconds.

Once I'm in Gnome, after around 5 mins the screen flickers a few times and then is fine.

PS Neither hibernate nor suspend work on my laptop.

Any suggestions?

---

### Post by lif44 on 2010-11-05
I had a similar problem and the following helped:


[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

----------

f you previously used the proprietary "fglrx" driver it is highly recommended to
 totally get rid of the fglrx package:

--> sudo apt-get remove --purge xorg-driver-fglrx

--> and reboot the computer.

The libGL.so in /usr/lib might also still be the version installed by xorg-driver-fglrx. You can check that very easily, just run:

glxinfo |grep vendor

If you see: client glx vendor string: ATI, then the libGL.so is still from ATI.

Make sure libgl1-mesa-glx and libgl1-mesa-dri are properly installed:

--> sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

Make sure "fglrx" is not listed in /etc/modules file.

Of course, make sure your xorg.conf does not contain any "fglrx" entry

----------

I followed these steps, especially the reinstall of libgl1-mesa-glx and libgl1-mesa-dri was very useful, then it worked (althoug it was a radeon 9600, this is probably also useful here)

regards
lif44

---

