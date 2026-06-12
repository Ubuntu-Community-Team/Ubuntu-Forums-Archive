---
title: "Looking to upgrade video card / power supply"
date: 2011-04-15
forum: Hardware
---

### Post by maxw3ll on 2011-04-15
I just recently installed 10.10 on my Acer Aspire T690 and was looking to upgrade my graphics card from an ATI Radeon 4550 to a GeForce GT520 for openGL support and a little more power. I have the new card but when I install it i receive the following error upon startup. 

serial8250 too much work irq19

My current power supply is only 250w and the card calls for 300 at least so i'm sure that is the problem, my question is if i were to buy a cheapo power supply from tigerdirect 

[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=106&sel=Detail;145_435_31319_51102](http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=106&sel=Detail;145_435_31319_51102)

would i have any issue fitting the power supply into my ghetto case?


everything inside of the case is stock aside from the graphics card and 2gb of ram.

---

### Post by wolfen69 on 2011-04-15
I just got an Nvidia update in 11.04 beta that provides support for the GT520 among other newer cards. Not sure if there is going to be an update for 10.10.

But without knowing what your case is like, I can't say if the power supply will fit or not. But it would be a good idea to upgrade it if possible.

---

### Post by K_45 on 2011-04-15
You should never cheap out on the PSU or mobo which are more important than anything else in a build. I'd get an Antec Earthwatts EA500, but you will need to reuse a power cord, as it doesn't come with one.

---

### Post by Yellow Pasque on 2011-04-15
The PSU is probably not causing the issue. See: [https://www.redhat.com/archives/fedora-list/2007-July/msg00657.html](https://www.redhat.com/archives/fedora-list/2007-July/msg00657.html)

If your PSU already worked with a RadeonHD 4550, then it should be fine for a GT520. The load TDP of the RHD is 25W and the GT520 29W.

---

### Post by maxw3ll on 2011-04-15
[http://www.youtube.com/watch?v=cNt1-qmMErw](http://www.youtube.com/watch?v=cNt1-qmMErw)


this video has a good look inside of my case, will the antec power supply fit in there you think? if not do you have any other recommendations?

---

### Post by maxw3ll on 2011-04-15
> **Temüjin said:**
> The PSU is probably not causing the issue. See: [https://www.redhat.com/archives/fedora-list/2007-July/msg00657.html](https://www.redhat.com/archives/fedora-list/2007-July/msg00657.html)

If your PSU already worked with a RadeonHD 4550, then it should be fine for a GT520. The load TDP of the RHD is 25W and the GT520 29W.

OH WOW, i'm going to try taking out the modem card and see what happens.

---

### Post by maxw3ll on 2011-04-15
took out the modem and everything booted up, now im going to upgrade to 11.04 for GT520 support and see what happens

---

### Post by Yellow Pasque on 2011-04-15
Just for reference, your computer uses an ATX standard PSU, so fitting a new one will not be an issue if you ever decide to do that.

---

### Post by maxw3ll on 2011-04-15
I'm running 11.04 now and was wondering where I can find the right driver update to run the geforce gt 520. 


I boot up with the card in there and get a black screen with a checklist 

Stopping cold plug devices
Starting load fallback graphic devices
...
...
...
Stopping load fallback graphic devices
Starting gnome
Starting load userspace bootsplash
Checking battery state


and then it holds there.

---

### Post by Yellow Pasque on 2011-04-15
The nvidia-current package has the latest nvidia driver. Boot to safe mode (hold down shift before GRUB loads) and choose recovery console with net access.
```
sudo apt-get update
sudo apt-get install nvidia-current
```

---

### Post by maxw3ll on 2011-04-15
tried that and went to restart and go the same checklist as before with


"Starting CUPS printing spooler/server" at the end.



Any ideas?

---

### Post by Yellow Pasque on 2011-04-15
> **maxw3ll said:**
> Any ideas?
Look at /var/log/Xorg.0.log to see what's wrong

---

### Post by maxw3ll on 2011-04-15
No idea what i should be looking for, 

```
[    16.011] 
X.Org X Server 1.10.0.902 (1.10.1 RC 2)
Release Date: 2011-04-08
[    16.011] X Protocol Version 11, Revision 0
[    16.011] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.011] Current Operating System: Linux maxwell-Aspire-T690 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    16.011] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=b57193bd-41f7-4c87-b5f8-e01914f56c02 ro quiet splash vt.handoff=7
[    16.011] Build Date: 11 April 2011  07:04:59AM
[    16.011] xorg-server 2:1.10.0.902-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    16.011] Current version of pixman: 0.20.2
[    16.011]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.011] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.012] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 15 21:45:41 2011
[    16.012] (==) Using config file: "/etc/X11/xorg.conf"
[    16.012] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.012] (==) No Layout section.  Using the first Screen section.
[    16.012] (**) |-->Screen "Default Screen" (0)
[    16.012] (**) |   |-->Monitor "<default monitor>"
[    16.013] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    16.013] (**) |   |-->Device "Default Device"
[    16.013] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    16.013] (==) Automatically adding devices
[    16.013] (==) Automatically enabling devices
[    16.013] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.013]     Entry deleted from font path.
[    16.013] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.013] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.013] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.013] (II) Loader magic: 0x81ffde0
[    16.013] (II) Module ABI versions:
[    16.013]     X.Org ANSI C Emulation: 0.4
[    16.013]     X.Org Video Driver: 10.0
[    16.013]     X.Org XInput driver : 12.3
[    16.013]     X.Org Server Extension : 5.0
[    16.014] (--) PCI:*(0:1:0:0) 1002:9540:174b:e106 rev 0, Mem @ 0xd0000000/268435456, 0xfdbe0000/65536, I/O @ 0x0000be00/256, BIOS @ 0x????????/131072
[    16.015] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.015] (II) "extmod" will be loaded by default.
[    16.015] (II) "dbe" will be loaded by default.
[    16.015] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    16.015] (II) "record" will be loaded by default.
[    16.015] (II) "dri" will be loaded by default.
[    16.015] (II) "dri2" will be loaded by default.
[    16.015] (II) LoadModule: "glx"
[    16.015] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    16.016] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    16.016]     compiled for 6.9.0, module version = 1.0.0
[    16.016] (II) Loading extension GLX
[    16.016] (II) LoadModule: "extmod"
[    16.034] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.034] (II) Module extmod: vendor="X.Org Foundation"
[    16.034]     compiled for 1.10.0.902, module version = 1.0.0
[    16.034]     Module class: X.Org Server Extension
[    16.034]     ABI class: X.Org Server Extension, version 5.0
[    16.034] (II) Loading extension MIT-SCREEN-SAVER
[    16.034] (II) Loading extension XFree86-VidModeExtension
[    16.034] (II) Loading extension XFree86-DGA
[    16.034] (II) Loading extension DPMS
[    16.034] (II) Loading extension XVideo
[    16.034] (II) Loading extension XVideo-MotionCompensation
[    16.034] (II) Loading extension X-Resource
[    16.034] (II) LoadModule: "dbe"
[    16.035] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.035] (II) Module dbe: vendor="X.Org Foundation"
[    16.035]     compiled for 1.10.0.902, module version = 1.0.0
[    16.035]     Module class: X.Org Server Extension
[    16.035]     ABI class: X.Org Server Extension, version 5.0
[    16.035] (II) Loading extension DOUBLE-BUFFER
[    16.035] (II) LoadModule: "record"
[    16.035] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.035] (II) Module record: vendor="X.Org Foundation"
[    16.035]     compiled for 1.10.0.902, module version = 1.13.0
[    16.035]     Module class: X.Org Server Extension
[    16.035]     ABI class: X.Org Server Extension, version 5.0
[    16.035] (II) Loading extension RECORD
[    16.035] (II) LoadModule: "dri"
[    16.036] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.036] (II) Module dri: vendor="X.Org Foundation"
[    16.036]     compiled for 1.10.0.902, module version = 1.0.0
[    16.036]     ABI class: X.Org Server Extension, version 5.0
[    16.036] (II) Loading extension XFree86-DRI
[    16.036] (II) LoadModule: "dri2"
[    16.037] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.037] (II) Module dri2: vendor="X.Org Foundation"
[    16.037]     compiled for 1.10.0.902, module version = 1.2.0
[    16.037]     ABI class: X.Org Server Extension, version 5.0
[    16.037] (II) Loading extension DRI2
[    16.037] (II) LoadModule: "fglrx"
[    16.037] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.066] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    16.066]     compiled for 1.4.99.906, module version = 8.84.60
[    16.066]     Module class: X.Org Video Driver
[    16.067] (II) Loading sub module "fglrxdrm"
[    16.067] (II) LoadModule: "fglrxdrm"
[    16.067] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.067] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.067]     compiled for 1.4.99.906, module version = 8.84.60
[    16.067] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    16.067] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    16.067] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    16.067] (++) using VT number 7

[    16.067] (WW) Falling back to old probe method for fglrx
[    16.076] (II) Loading PCS database from /etc/ati/amdpcsdb
[    16.077] (--) Assigning device section with no busID to primary device
[    16.077] (--) Chipset Supported AMD Graphics Processor (0x9540) found
[    16.077] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    16.077] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    16.077] (II) AMD Video driver is signed
[    16.078] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.078] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.078] (II) fglrx(0): pEnt->device->identifier=0x9418738
[    16.078] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    16.078] (II) Loading sub module "vgahw"
[    16.078] (II) LoadModule: "vgahw"
[    16.078] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    16.079] (II) Module vgahw: vendor="X.Org Foundation"
[    16.079]     compiled for 1.10.0.902, module version = 0.1.0
[    16.079]     ABI class: X.Org Video Driver, version 10.0
[    16.079] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    16.079] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    16.079] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.079] (==) fglrx(0): Default visual is TrueColor
[    16.079] (==) fglrx(0): RGB weight 888
[    16.079] (II) fglrx(0): Using 8 bits per RGB 
[    16.079] (==) fglrx(0): Buffer Tiling is ON
[    16.079] (II) Loading sub module "fglrxdrm"
[    16.079] (II) LoadModule: "fglrxdrm"
[    16.079] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.079] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.079]     compiled for 1.4.99.906, module version = 8.84.60
[    16.082] ukiDynamicMajor: found major device number 249
[    16.082] ukiDynamicMajor: found major device number 249
[    16.082] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.082] ukiOpenDevice: node name is /dev/ati/card0
[    16.082] ukiOpenDevice: open result is 11, (OK)
[    16.082] ukiOpenByBusid: ukiOpenMinor returns 11
[    16.082] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.083] (==) fglrx(0): NoAccel = NO
[    16.083] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    16.083] (--) fglrx(0): Chipset: "ATI Radeon HD 4550" (Chipset = 0x9540)
[    16.083] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe106)
[    16.083] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    16.083] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    16.083] (--) fglrx(0): MMIO registers at 0xfdbe0000
[    16.083] (--) fglrx(0): I/O port at 0x0000be00
[    16.083] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    16.084] (II) fglrx(0): AC Adapter is used
[    16.100] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    16.104] (II) Loading sub module "vbe"
[    16.104] (II) LoadModule: "vbe"
[    16.104] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    16.104] (II) Module vbe: vendor="X.Org Foundation"
[    16.104]     compiled for 1.10.0.902, module version = 1.1.0
[    16.104]     ABI class: X.Org Video Driver, version 10.0
[    16.105] (II) fglrx(0): VESA BIOS detected
[    16.105] (II) fglrx(0): VESA VBE Version 3.0
[    16.105] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    16.105] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    16.105] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[    16.105] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    16.105] (II) fglrx(0): VESA VBE OEM Product: Y3
[    16.105] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    16.145] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    16.145] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    16.145] (II) fglrx(0): PCIE card detected
[    16.145] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    16.145] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    16.150] (II) fglrx(0): Using adapter: 1:0.0.
[    16.178] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    16.302] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    16.302] (II) fglrx(0): RandR 1.2 support is enabled!
[    16.302] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    16.303] (==) fglrx(0): Center Mode is disabled 
[    16.303] (II) Loading sub module "fb"
[    16.303] (II) LoadModule: "fb"
[    16.303] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.303] (II) Module fb: vendor="X.Org Foundation"
[    16.303]     compiled for 1.10.0.902, module version = 1.0.0
[    16.303]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.303] (II) Loading sub module "ddc"
[    16.303] (II) LoadModule: "ddc"
[    16.303] (II) Module "ddc" already built-in
[    16.944] (II) fglrx(0): Finished Initialize PPLIB!
[    16.947] (II) fglrx(0): Output DFP1 has no monitor section
[    16.947] (II) fglrx(0): Output DFP2 has no monitor section
[    16.947] (II) fglrx(0): Output CRT1 has no monitor section
[    16.947] (II) fglrx(0): Output CRT2 has no monitor section
[    16.947] (II) Loading sub module "ddc"
[    16.947] (II) LoadModule: "ddc"
[    16.947] (II) Module "ddc" already built-in
[    16.947] (II) fglrx(0): Connected Display0: CRT2
[    16.947] (II) fglrx(0): Display0 EDID data ---------------------------
[    16.947] (II) fglrx(0): Manufacturer: GSM  Model: 5664  Serial#: 403923
[    16.947] (II) fglrx(0): Year: 2007  Week: 9
[    16.947] (II) fglrx(0): EDID Version: 1.3
[    16.948] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    16.948] (II) fglrx(0): Sync:  Separate  SyncOnGreen
[    16.948] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    16.948] (II) fglrx(0): Gamma: 2.20
[    16.948] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    16.948] (II) fglrx(0): First detailed timing is preferred mode
[    16.948] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.605
[    16.948] (II) fglrx(0): blueX: 0.152 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
[    16.948] (II) fglrx(0): Supported established timings:
[    16.948] (II) fglrx(0): 720x400@70Hz
[    16.948] (II) fglrx(0): 640x480@60Hz
[    16.948] (II) fglrx(0): 640x480@75Hz
[    16.948] (II) fglrx(0): 800x600@56Hz
[    16.948] (II) fglrx(0): 800x600@60Hz
[    16.948] (II) fglrx(0): 800x600@75Hz
[    16.948] (II) fglrx(0): 832x624@75Hz
[    16.948] (II) fglrx(0): 1024x768@60Hz
[    16.948] (II) fglrx(0): 1024x768@75Hz
[    16.948] (II) fglrx(0): 1280x1024@75Hz
[    16.948] (II) fglrx(0): 1152x864@75Hz
[    16.948] (II) fglrx(0): Manufacturer's mask: 0
[    16.948] (II) fglrx(0): Supported standard timings:
[    16.948] (II) fglrx(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    16.948] (II) fglrx(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    16.948] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.948] (II) fglrx(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    16.948] (II) fglrx(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.948] (II) fglrx(0): Supported detailed timing:
[    16.948] (II) fglrx(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    16.948] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    16.948] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    16.949] (II) fglrx(0): Supported detailed timing:
[    16.949] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    16.949] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    16.949] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    16.949] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 155 MHz
[    16.949] (II) fglrx(0): Monitor name: L222W
[    16.949] (II) fglrx(0): EDID (in hex):
[    16.949] (II) fglrx(0):     00ffffffffffff001e6d6456d3290600
[    16.949] (II) fglrx(0):     091101036a2f1e78ead425a455499b27
[    16.949] (II) fglrx(0):     135054a76b80950f950081808140714f
[    16.949] (II) fglrx(0):     0101010101017c2e90a0601a1e403020
[    16.949] (II) fglrx(0):     3600da281100001a21399030621a2740
[    16.949] (II) fglrx(0):     68b03600da281100001c000000fd0038
[    16.949] (II) fglrx(0):     4b1c530f000a202020202020000000fc
[    16.949] (II) fglrx(0):     004c32323257000a20202020202000db
[    16.949] (II) fglrx(0): End of Display0 EDID data --------------------
[    17.018] (II) fglrx(0): EDID for output DFP1
[    17.018] (II) fglrx(0): EDID for output DFP2
[    17.018] (II) fglrx(0): EDID for output CRT1
[    17.018] (II) fglrx(0): EDID for output CRT2
[    17.018] (II) fglrx(0): Manufacturer: GSM  Model: 5664  Serial#: 403923
[    17.018] (II) fglrx(0): Year: 2007  Week: 9
[    17.018] (II) fglrx(0): EDID Version: 1.3
[    17.018] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    17.018] (II) fglrx(0): Sync:  Separate  SyncOnGreen
[    17.018] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    17.018] (II) fglrx(0): Gamma: 2.20
[    17.018] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    17.019] (II) fglrx(0): First detailed timing is preferred mode
[    17.019] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.605
[    17.019] (II) fglrx(0): blueX: 0.152 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
[    17.019] (II) fglrx(0): Supported established timings:
[    17.019] (II) fglrx(0): 720x400@70Hz
[    17.019] (II) fglrx(0): 640x480@60Hz
[    17.019] (II) fglrx(0): 640x480@75Hz
[    17.019] (II) fglrx(0): 800x600@56Hz
[    17.019] (II) fglrx(0): 800x600@60Hz
[    17.019] (II) fglrx(0): 800x600@75Hz
[    17.019] (II) fglrx(0): 832x624@75Hz
[    17.019] (II) fglrx(0): 1024x768@60Hz
[    17.019] (II) fglrx(0): 1024x768@75Hz
[    17.019] (II) fglrx(0): 1280x1024@75Hz
[    17.019] (II) fglrx(0): 1152x864@75Hz
[    17.019] (II) fglrx(0): Manufacturer's mask: 0
[    17.019] (II) fglrx(0): Supported standard timings:
[    17.019] (II) fglrx(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    17.019] (II) fglrx(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    17.019] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.019] (II) fglrx(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    17.019] (II) fglrx(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    17.019] (II) fglrx(0): Supported detailed timing:
[    17.019] (II) fglrx(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    17.019] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    17.019] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    17.019] (II) fglrx(0): Supported detailed timing:
[    17.019] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    17.019] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    17.019] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    17.019] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 155 MHz
[    17.019] (II) fglrx(0): Monitor name: L222W
[    17.019] (II) fglrx(0): EDID (in hex):
[    17.019] (II) fglrx(0):     00000000782830293a2053796e633a00
[    17.019] (II) fglrx(0):     6374757265723a202573202029000000
[    17.019] (II) fglrx(0):     00000000782830293a20454449442028
[    17.019] (II) fglrx(0):     696e20686578293a0a00601a1e403020
[    17.019] (II) fglrx(0):     3600da28410000000000000078283029
[    17.019] (II) fglrx(0):     3a2046697273742064657461696c6564
[    17.020] (II) fglrx(0):     2074696d696e67206973207072656665
[    17.020] (II) fglrx(0):     72726564206d6f64650a0020202000db
[    17.020] (II) fglrx(0): Printing probed modes for output CRT2
[    17.020] (II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
[    17.020] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    17.020] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    17.020] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    17.020] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    17.020] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    17.020] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    17.020] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    17.020] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    17.020] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    17.020] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    17.020] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    17.020] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    17.020] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    17.020] (II) fglrx(0): Output DFP1 disconnected
[    17.020] (II) fglrx(0): Output DFP2 disconnected
[    17.020] (II) fglrx(0): Output CRT1 disconnected
[    17.020] (II) fglrx(0): Output CRT2 connected
[    17.020] (II) fglrx(0): Using exact sizes for initial modes
[    17.020] (II) fglrx(0): Output CRT2 using initial mode 1680x1050
[    17.021] (II) fglrx(0): DPI set to (96, 96)
[    17.021] (II) fglrx(0): Adapter ATI Radeon HD 4550 has 2 configurable heads and 1 displays connected.
[    17.021] (==) fglrx(0):  PseudoColor visuals disabled
[    17.021] (II) Loading sub module "ramdac"
[    17.021] (II) LoadModule: "ramdac"
[    17.021] (II) Module "ramdac" already built-in
[    17.021] (==) fglrx(0): NoDRI = NO
[    17.021] (==) fglrx(0): Capabilities: 0x00000000
[    17.021] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    17.021] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    17.021] (==) fglrx(0): UseFastTLS=0
[    17.021] (==) fglrx(0): BlockSignalsOnLock=1
[    17.021] (--) Depth 24 pixmap format is 32 bpp
[    17.021] (II) Loading extension ATIFGLRXDRI
[    17.021] (II) fglrx(0): doing swlDriScreenInit
[    17.021] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    17.021] ukiDynamicMajor: found major device number 249
[    17.022] ukiDynamicMajor: found major device number 249
[    17.022] ukiDynamicMajor: found major device number 249
[    17.022] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.022] ukiOpenDevice: node name is /dev/ati/card0
[    17.022] ukiOpenDevice: open result is 16, (OK)
[    17.022] ukiOpenByBusid: ukiOpenMinor returns 16
[    17.022] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.022] (II) fglrx(0): [uki] DRM interface version 1.0
[    17.022] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    17.022] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    17.022] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7719000
[    17.022] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    17.022] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    17.022] (II) fglrx(0): swlDriScreenInit done
[    17.022] (II) fglrx(0): Kernel Module Version Information:
[    17.022] (II) fglrx(0):     Name: fglrx
[    17.022] (II) fglrx(0):     Version: 8.84.60
[    17.022] (II) fglrx(0):     Date: Mar 24 2011
[    17.022] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    17.022] (II) fglrx(0): Kernel Module version matches driver.
[    17.022] (II) fglrx(0): Kernel Module Build Time Information:
[    17.022] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic
[    17.022] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    17.022] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    17.022] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    17.022] (II) fglrx(0): [uki] register handle = 0x00004000
[    17.046] (II) fglrx(0): DRI initialization successfull
[    17.046] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01008000
[    17.046] (==) fglrx(0): Backing store disabled
[    17.046] (II) Loading extension FGLRXEXTENSION
[    17.046] (==) fglrx(0): DPMS enabled
[    17.047] (II) fglrx(0): Initialized in-driver Xinerama extension
[    17.047] (**) fglrx(0): Textured Video is enabled.
[    17.047] (II) LoadModule: "glesx"
[    17.047] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    17.049] (II) Module glesx: vendor="X.Org Foundation"
[    17.049]     compiled for 1.4.99.906, module version = 1.0.0
[    17.049] (II) Loading extension GLESX
[    17.049] (II) fglrx(0): GLESX enableFlags = 528
[    17.049] (II) fglrx(0): GLESX is enabled
[    17.049] (II) LoadModule: "amdxmm"
[    17.050] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    17.050] (II) Module amdxmm: vendor="X.Org Foundation"
[    17.050]     compiled for 1.4.99.906, module version = 2.0.0
[    17.050] (II) Loading extension AMDXVOPL
[    17.050] (II) Loading extension AMDXVBA
[    17.052] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    17.055] (II) fglrx(0): Enable composite support successfully
[    17.055] (II) fglrx(0): X context handle = 0x1
[    17.055] (II) fglrx(0): [DRI] installation complete
[    17.055] (==) fglrx(0): Silken mouse enabled
[    17.055] (==) fglrx(0): Using HW cursor of display infrastructure!
[    17.055] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    17.199] (--) RandR disabled
[    17.199] (II) Initializing built-in extension Generic Event Extension
[    17.199] (II) Initializing built-in extension SHAPE
[    17.199] (II) Initializing built-in extension MIT-SHM
[    17.199] (II) Initializing built-in extension XInputExtension
[    17.199] (II) Initializing built-in extension XTEST
[    17.199] (II) Initializing built-in extension BIG-REQUESTS
[    17.199] (II) Initializing built-in extension SYNC
[    17.199] (II) Initializing built-in extension XKEYBOARD
[    17.199] (II) Initializing built-in extension XC-MISC
[    17.199] (II) Initializing built-in extension SECURITY
[    17.199] (II) Initializing built-in extension XINERAMA
[    17.199] (II) Initializing built-in extension XFIXES
[    17.199] (II) Initializing built-in extension RENDER
[    17.199] (II) Initializing built-in extension RANDR
[    17.199] (II) Initializing built-in extension COMPOSITE
[    17.199] (II) Initializing built-in extension DAMAGE
[    17.199] (II) Initializing built-in extension GESTURE
[    17.229] ukiDynamicMajor: found major device number 249
[    17.229] ukiDynamicMajor: found major device number 249
[    17.229] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.229] ukiOpenDevice: node name is /dev/ati/card0
[    17.229] ukiOpenDevice: open result is 18, (OK)
[    17.229] ukiOpenByBusid: ukiOpenMinor returns 18
[    17.229] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.381] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    17.381] (II) fglrx(0): Enable the clock gating!
[    17.381] (II) fglrx(0): Setting screen physical size to 444 x 277
[    17.411] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.431] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.431] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.431] (II) LoadModule: "evdev"
[    17.447] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.448] (II) Module evdev: vendor="X.Org Foundation"
[    17.448]     compiled for 1.10.0, module version = 2.6.0
[    17.448]     Module class: X.Org XInput Driver
[    17.448]     ABI class: X.Org XInput driver, version 12.3
[    17.448] (II) Using input driver 'evdev' for 'Power Button'
[    17.448] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.448] (**) Power Button: always reports core events
[    17.448] (**) Power Button: Device: "/dev/input/event1"
[    17.464] (--) Power Button: Found keys
[    17.464] (II) Power Button: Configuring as keyboard
[    17.464] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.464] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.464] (**) Option "xkb_rules" "evdev"
[    17.464] (**) Option "xkb_model" "pc105"
[    17.464] (**) Option "xkb_layout" "us"
[    17.469] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.469] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.469] (II) Using input driver 'evdev' for 'Power Button'
[    17.469] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.469] (**) Power Button: always reports core events
[    17.469] (**) Power Button: Device: "/dev/input/event0"
[    17.469] (--) Power Button: Found keys
[    17.469] (II) Power Button: Configuring as keyboard
[    17.469] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.469] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.469] (**) Option "xkb_rules" "evdev"
[    17.469] (**) Option "xkb_model" "pc105"
[    17.469] (**) Option "xkb_layout" "us"
[    17.471] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event4)
[    17.471] (II) No input driver/identifier specified (ignoring)
[    17.475] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    17.475] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    17.475] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[    17.475] (--) Logitech USB-PS/2 Optical Mouse: Found 10 mouse buttons
[    17.475] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    17.475] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    17.475] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    17.475] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    17.475] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.475] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3/event3"
[    17.475] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    17.475] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    17.475] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    17.476] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    17.476] (II) No input driver/identifier specified (ignoring)
[    17.486] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    17.486] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.486] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.486] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.486] (**) AT Translated Set 2 keyboard: always reports core events
[    17.486] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    17.486] (--) AT Translated Set 2 keyboard: Found keys
[    17.486] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.486] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    17.486] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.486] (**) Option "xkb_rules" "evdev"
[    17.486] (**) Option "xkb_model" "pc105"
[    17.486] (**) Option "xkb_layout" "us"
[    17.532] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    18.238] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    18.238] (II) fglrx(0): Using EDID range info for horizontal sync
[    18.238] (II) fglrx(0): Using EDID range info for vertical refresh
[    18.238] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.238] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.238] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.238] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.238] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.238] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.238] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.238] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.238] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.238] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.238] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.238] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.238] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.238] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.238] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.239] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.239] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.239] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.589] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    18.589] (II) fglrx(0): Using hsync ranges from config file
[    18.589] (II) fglrx(0): Using vrefresh ranges from config file
[    18.589] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.589] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.589] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.590] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.590] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.590] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.590] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.590] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.590] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.590] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.590] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.590] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.590] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.590] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.590] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.590] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.590] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.590] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.941] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    18.941] (II) fglrx(0): Using hsync ranges from config file
[    18.941] (II) fglrx(0): Using vrefresh ranges from config file
[    18.942] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.942] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.942] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.942] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.942] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.942] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.942] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.942] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.942] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.942] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.942] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.942] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.942] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.942] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.942] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.942] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.942] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.942] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    19.293] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    19.293] (II) fglrx(0): Using hsync ranges from config file
[    19.293] (II) fglrx(0): Using vrefresh ranges from config file
[    19.293] (II) fglrx(0): Printing DDC gathered Modelines:
[    19.293] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    19.293] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    19.293] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.293] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.293] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.293] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.293] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.293] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.293] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.293] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.293] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    19.293] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.293] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    19.293] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    19.293] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    19.293] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.293] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    26.594] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    27.146] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    27.146] (II) fglrx(0): Using hsync ranges from config file
[    27.146] (II) fglrx(0): Using vrefresh ranges from config file
[    27.146] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.146] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    27.146] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    27.146] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.146] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.146] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.146] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.147] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.147] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.147] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.147] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.147] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.147] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.147] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.147] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    27.147] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    27.147] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.147] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    27.495] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    27.495] (II) fglrx(0): Using hsync ranges from config file
[    27.495] (II) fglrx(0): Using vrefresh ranges from config file
[    27.495] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.495] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    27.495] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    27.495] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.495] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.495] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.495] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.495] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.495] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.495] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.495] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.495] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.495] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.495] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.495] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    27.495] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    27.495] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.495] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    27.840] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    27.840] (II) fglrx(0): Using hsync ranges from config file
[    27.840] (II) fglrx(0): Using vrefresh ranges from config file
[    27.840] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.840] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    27.840] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    27.840] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.840] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.840] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.840] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.840] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.840] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.840] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.840] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.840] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.840] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.840] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.840] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    27.841] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    27.841] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.841] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    28.185] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    28.185] (II) fglrx(0): Using hsync ranges from config file
[    28.185] (II) fglrx(0): Using vrefresh ranges from config file
[    28.185] (II) fglrx(0): Printing DDC gathered Modelines:
[    28.185] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    28.185] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    28.185] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.185] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.185] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.185] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.186] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.186] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.186] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.186] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.186] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.186] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.186] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.186] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.186] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.186] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.186] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    28.975] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    28.976] (II) fglrx(0): Using hsync ranges from config file
[    28.976] (II) fglrx(0): Using vrefresh ranges from config file
[    28.976] (II) fglrx(0): Printing DDC gathered Modelines:
[    28.976] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    28.976] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    28.976] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.976] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.976] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.976] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.976] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.976] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.976] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.976] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.976] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.976] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.976] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.976] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.976] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.976] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.976] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    34.522] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[    34.522] (II) fglrx(0): Using hsync ranges from config file
[    34.522] (II) fglrx(0): Using vrefresh ranges from config file
[    34.522] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.522] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    34.522] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    34.522] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.522] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.522] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.522] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.522] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.522] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.522] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.522] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.522] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    34.522] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.522] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    34.522] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    34.522] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.522] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.522] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1396.322] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1396.322] (II) fglrx(0): Using hsync ranges from config file
[  1396.322] (II) fglrx(0): Using vrefresh ranges from config file
[  1396.322] (II) fglrx(0): Printing DDC gathered Modelines:
[  1396.322] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1396.322] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1396.322] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1396.322] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1396.322] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1396.322] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1396.322] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1396.322] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1396.322] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1396.322] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1396.322] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1396.322] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1396.322] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1396.322] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1396.322] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1396.322] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1396.322] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1396.696] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1396.696] (II) fglrx(0): Using hsync ranges from config file
[  1396.696] (II) fglrx(0): Using vrefresh ranges from config file
[  1396.696] (II) fglrx(0): Printing DDC gathered Modelines:
[  1396.696] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1396.696] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1396.696] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1396.696] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1396.696] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1396.696] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1396.696] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1396.696] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1396.696] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1396.696] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1396.696] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1396.696] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1396.696] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1396.696] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1396.696] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1396.696] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1396.696] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1398.261] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1398.261] (II) fglrx(0): Using hsync ranges from config file
[  1398.261] (II) fglrx(0): Using vrefresh ranges from config file
[  1398.261] (II) fglrx(0): Printing DDC gathered Modelines:
[  1398.261] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1398.261] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1398.261] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1398.261] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1398.261] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1398.261] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1398.261] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1398.261] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1398.261] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1398.261] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1398.261] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1398.261] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1398.261] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1398.261] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1398.261] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1398.261] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1398.261] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1399.088] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1399.088] (II) fglrx(0): Using hsync ranges from config file
[  1399.088] (II) fglrx(0): Using vrefresh ranges from config file
[  1399.088] (II) fglrx(0): Printing DDC gathered Modelines:
[  1399.088] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1399.088] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1399.088] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1399.088] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1399.088] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1399.088] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1399.088] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1399.088] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1399.088] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1399.088] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1399.088] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1399.088] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1399.088] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1399.088] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1399.088] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1399.088] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1399.088] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1399.460] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1399.460] (II) fglrx(0): Using hsync ranges from config file
[  1399.460] (II) fglrx(0): Using vrefresh ranges from config file
[  1399.461] (II) fglrx(0): Printing DDC gathered Modelines:
[  1399.461] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1399.461] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1399.461] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1399.461] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1399.461] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1399.461] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1399.461] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1399.461] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1399.461] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1399.461] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1399.461] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1399.461] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1399.461] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1399.461] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1399.461] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1399.461] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1399.461] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1402.213] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1402.214] (II) fglrx(0): Using hsync ranges from config file
[  1402.214] (II) fglrx(0): Using vrefresh ranges from config file
[  1402.214] (II) fglrx(0): Printing DDC gathered Modelines:
[  1402.214] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1402.214] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1402.214] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1402.214] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1402.214] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1402.214] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1402.214] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1402.214] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1402.214] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1402.214] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1402.214] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1402.214] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1402.214] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1402.214] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1402.214] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1402.214] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1402.214] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1402.586] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1402.586] (II) fglrx(0): Using hsync ranges from config file
[  1402.586] (II) fglrx(0): Using vrefresh ranges from config file
[  1402.586] (II) fglrx(0): Printing DDC gathered Modelines:
[  1402.586] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1402.587] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1402.587] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1402.587] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1402.587] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1402.587] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1402.587] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1402.587] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1402.587] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1402.587] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1402.587] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1402.587] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1402.587] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1402.587] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1402.587] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1402.587] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1402.587] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1418.597] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1418.597] (II) fglrx(0): Using hsync ranges from config file
[  1418.597] (II) fglrx(0): Using vrefresh ranges from config file
[  1418.597] (II) fglrx(0): Printing DDC gathered Modelines:
[  1418.597] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1418.597] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1418.598] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1418.598] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1418.598] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1418.598] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1418.598] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1418.598] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1418.598] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1418.598] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1418.598] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1418.598] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1418.598] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1418.598] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1418.598] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1418.598] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1418.598] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1423.399] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1423.399] (II) fglrx(0): Using hsync ranges from config file
[  1423.399] (II) fglrx(0): Using vrefresh ranges from config file
[  1423.399] (II) fglrx(0): Printing DDC gathered Modelines:
[  1423.399] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1423.399] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1423.399] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1423.400] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1423.403] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1423.403] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1423.403] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1423.403] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1423.403] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1423.403] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1423.403] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1423.403] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1423.403] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1423.403] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1423.403] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1423.403] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1423.403] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1423.859] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1423.859] (II) fglrx(0): Using hsync ranges from config file
[  1423.859] (II) fglrx(0): Using vrefresh ranges from config file
[  1423.859] (II) fglrx(0): Printing DDC gathered Modelines:
[  1423.859] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1423.859] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1423.859] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1423.859] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1423.859] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1423.859] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1423.859] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1423.859] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1423.859] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1423.859] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1423.859] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1423.859] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1423.859] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1423.859] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1423.859] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1423.859] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1423.859] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1692.464] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1692.464] (II) fglrx(0): Using hsync ranges from config file
[  1692.464] (II) fglrx(0): Using vrefresh ranges from config file
[  1692.464] (II) fglrx(0): Printing DDC gathered Modelines:
[  1692.464] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1692.464] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1692.464] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1692.464] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1692.464] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1692.464] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1692.464] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1692.464] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1692.464] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1692.464] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1692.464] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1692.464] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1692.464] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1692.464] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1692.464] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1692.464] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1692.464] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1697.000] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1697.000] (II) fglrx(0): Using hsync ranges from config file
[  1697.000] (II) fglrx(0): Using vrefresh ranges from config file
[  1697.000] (II) fglrx(0): Printing DDC gathered Modelines:
[  1697.001] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1697.001] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1697.001] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1697.001] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1697.001] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1697.001] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1697.001] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1697.001] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1697.001] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1697.001] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1697.001] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1697.001] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1697.001] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1697.001] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1697.001] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1697.001] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1697.001] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1697.379] (II) fglrx(0): EDID vendor "GSM", prod id 22116
[  1697.381] (II) fglrx(0): Using hsync ranges from config file
[  1697.381] (II) fglrx(0): Using vrefresh ranges from config file
[  1697.382] (II) fglrx(0): Printing DDC gathered Modelines:
[  1697.382] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1697.382] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1697.382] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1697.382] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1697.382] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1697.382] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1697.382] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1697.382] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1697.382] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1697.382] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1697.382] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1697.382] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1697.382] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1697.382] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  1697.382] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1697.382] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1697.382] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
```

---

### Post by Yellow Pasque on 2011-04-15
That looks like a log from an ATI card. Speaking of that, make sure you remove the fglrx driver: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by maxw3ll on 2011-04-15
Now this log file is from running my system with the old ATI inside since i cant do anything with the nvidia installed. idk if that will produce different log files or not or if i need to be looking somewhere else.


EDIT:

should i remove the drivers and reinstall those other packages? 


and how can i get to a log file with the nvidia installed if i cant boot up into regular operating system? 


i apologize for being so inexperienced... :(

---

### Post by Yellow Pasque on 2011-04-15
Try to boot with the nvidia. When it halts, reboot into recovery console and save/copy the Xorg log.

---

### Post by maxw3ll on 2011-04-15
So i hold shift to enter recovery console, will that take me to a terminal window? how can i get to the xorg log from there?

---

### Post by maxw3ll on 2011-04-16
Heres what i got


```
[    29.499] 
X.Org X Server 1.10.0.902 (1.10.1 RC 2)
Release Date: 2011-04-08
[    29.499] X Protocol Version 11, Revision 0
[    29.499] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    29.499] Current Operating System: Linux maxwell-Aspire-T690 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    29.499] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=b57193bd-41f7-4c87-b5f8-e01914f56c02 ro quiet splash vt.handoff=7
[    29.499] Build Date: 11 April 2011  07:04:59AM
[    29.499] xorg-server 2:1.10.0.902-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    29.499] Current version of pixman: 0.20.2
[    29.499]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.499] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.499] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 15 23:07:20 2011
[    29.499] (==) Using config file: "/etc/X11/xorg.conf"
[    29.499] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.500] (==) No Layout section.  Using the first Screen section.
[    29.500] (**) |-->Screen "Default Screen" (0)
[    29.500] (**) |   |-->Monitor "<default monitor>"
[    29.500] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    29.500] (**) |   |-->Device "Default Device"
[    29.500] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    29.500] (==) Automatically adding devices
[    29.500] (==) Automatically enabling devices
[    29.501] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.501]     Entry deleted from font path.
[    29.501] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    29.501] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.501] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.501] (II) Loader magic: 0x81ffde0
[    29.501] (II) Module ABI versions:
[    29.501]     X.Org ANSI C Emulation: 0.4
[    29.501]     X.Org Video Driver: 10.0
[    29.501]     X.Org XInput driver : 12.3
[    29.501]     X.Org Server Extension : 5.0
[    29.502] (--) PCI:*(0:1:0:0) 10de:1040:1b4c:0915 rev 161, Mem @ 0xfb000000/16777216, 0xc8000000/134217728, 0xd6000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/524288
[    29.502] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.502] (II) "extmod" will be loaded by default.
[    29.502] (II) "dbe" will be loaded by default.
[    29.502] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.502] (II) "record" will be loaded by default.
[    29.502] (II) "dri" will be loaded by default.
[    29.502] (II) "dri2" will be loaded by default.
[    29.502] (II) LoadModule: "glx"
[    29.503] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    29.548] (II) Module glx: vendor="NVIDIA Corporation"
[    29.548]     compiled for 4.0.2, module version = 1.0.0
[    29.548]     Module class: X.Org Server Extension
[    29.548] (II) NVIDIA GLX Module  270.41.03  Sat Apr  9 00:22:20 PDT 2011
[    29.548] (II) Loading extension GLX
[    29.548] (II) LoadModule: "extmod"
[    29.548] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.548] (II) Module extmod: vendor="X.Org Foundation"
[    29.548]     compiled for 1.10.0.902, module version = 1.0.0
[    29.548]     Module class: X.Org Server Extension
[    29.548]     ABI class: X.Org Server Extension, version 5.0
[    29.549] (II) Loading extension MIT-SCREEN-SAVER
[    29.549] (II) Loading extension XFree86-VidModeExtension
[    29.549] (II) Loading extension XFree86-DGA
[    29.549] (II) Loading extension DPMS
[    29.549] (II) Loading extension XVideo
[    29.549] (II) Loading extension XVideo-MotionCompensation
[    29.549] (II) Loading extension X-Resource
[    29.549] (II) LoadModule: "dbe"
[    29.549] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.549] (II) Module dbe: vendor="X.Org Foundation"
[    29.549]     compiled for 1.10.0.902, module version = 1.0.0
[    29.549]     Module class: X.Org Server Extension
[    29.549]     ABI class: X.Org Server Extension, version 5.0
[    29.549] (II) Loading extension DOUBLE-BUFFER
[    29.549] (II) LoadModule: "record"
[    29.549] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.550] (II) Module record: vendor="X.Org Foundation"
[    29.550]     compiled for 1.10.0.902, module version = 1.13.0
[    29.550]     Module class: X.Org Server Extension
[    29.550]     ABI class: X.Org Server Extension, version 5.0
[    29.550] (II) Loading extension RECORD
[    29.550] (II) LoadModule: "dri"
[    29.550] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.550] (II) Module dri: vendor="X.Org Foundation"
[    29.550]     compiled for 1.10.0.902, module version = 1.0.0
[    29.550]     ABI class: X.Org Server Extension, version 5.0
[    29.550] (II) Loading extension XFree86-DRI
[    29.550] (II) LoadModule: "dri2"
[    29.551] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.551] (II) Module dri2: vendor="X.Org Foundation"
[    29.551]     compiled for 1.10.0.902, module version = 1.2.0
[    29.551]     ABI class: X.Org Server Extension, version 5.0
[    29.551] (II) Loading extension DRI2
[    29.551] (II) LoadModule: "fglrx"
[    29.552] (WW) Warning, couldn't open module fglrx
[    29.552] (II) UnloadModule: "fglrx"
[    29.552] (II) Unloading fglrx
[    29.552] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    29.552] (EE) No drivers available.
[    29.552] 
Fatal server error:
[    29.552] no screens found
[    29.552] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    29.552] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    29.552] 
```

---

### Post by Yellow Pasque on 2011-04-16
You're still trying to load the ATI driver (probably in xorg.conf).
```
sudo mv xorg.conf xorg.conf.backup
```

---

### Post by cascade9 on 2011-04-16
> **Temüjin said:**
> The nvidia-current package has the latest nvidia driver. Boot to safe mode (hold down shift before GRUB loads) and choose recovery console with net access.
```
sudo apt-get update
sudo apt-get install nvidia-current
```

AFAIK nvidia-current wont work with the GT520 or any released version of ubuntu. It could possibly work with 11.04beta, if they have added the newest alpha drivers. 

GT520 support was added with 270.41.03, which is another one of those annoying "dont appear on the nvidia site, FTP only, pseudo-beta (aka "alpha" in all but name) drivers.

---

### Post by Yellow Pasque on 2011-04-16
> **cascade9 said:**
> AFAIK nvidia-current wont work with the GT520 or any released version of ubuntu. It could possibly work with 11.04beta, if they have added the newest alpha drivers.

The OP is using Natty and it has the latest driver: [http://packages.ubuntu.com/natty/nvidia-current](http://packages.ubuntu.com/natty/nvidia-current)
If OP wasn't using it, I would have linked to: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

