---
title: "HP touchsmart tx2,shud i get it."
date: 2010-02-04
forum: Hardware
---

### Post by akshay.sulakhe on 2010-02-04
Hello friends, m planning to buy Hp touchsmart tx2,i read a review [http://www.notebooks.com/2008/11/19/hp-touchsmart-tx2-first-consumer-multitouch-tablet-first-thoughts-pricing-video-demo/]("http://www.notebooks.com/2008/11/19/hp-touchsmart-tx2-first-consumer-multitouch-tablet-first-thoughts-pricing-video-demo/") which says "The TouchSmart tx2 is an improvement over HP’s previous tablet, the Pavilion tx2500z. The tx2500z does include a touchscreen, but you can only use one finger at time. The new capacitive touch is a really big deal and if you’re considering a tx-series tablet you should ignore the tx2500z, which is still being offered by retailers and on HP’s Web site, and opt for the tx2."
 so now what shud i say to the sales person which machine i want..i want the one which is capacitive touch and multi-touch....please help me. And also will ubuntu support multi touch. If u have any pointers,plz let me know..Thanks.

---

### Post by Ayuthia on 2010-02-05
> **akshay.sulakhe said:**
> Hello friends, m planning to buy Hp touchsmart tx2,i read a review [http://www.notebooks.com/2008/11/19/hp-touchsmart-tx2-first-consumer-multitouch-tablet-first-thoughts-pricing-video-demo/]("http://www.notebooks.com/2008/11/19/hp-touchsmart-tx2-first-consumer-multitouch-tablet-first-thoughts-pricing-video-demo/") which says "The TouchSmart tx2 is an improvement over HP’s previous tablet, the Pavilion tx2500z. The tx2500z does include a touchscreen, but you can only use one finger at time. The new capacitive touch is a really big deal and if you’re considering a tx-series tablet you should ignore the tx2500z, which is still being offered by retailers and on HP’s Web site, and opt for the tx2."
 so now what shud i say to the sales person which machine i want..i want the one which is capacitive touch and multi-touch....please help me. And also will ubuntu support multi touch. If u have any pointers,plz let me know..Thanks.

If you are going to a store to look at the computers, the best thing to do is check the system information (Control Panel->System if it is Windows 7).  Windows 7 will tell you how many fingers the touchscreen supports.  Another place to look is in the Device Manager and look at the Digitizer.  It will tell you what it is using.

If you are planning to go with HP, the tx2 series use the N-Trig digitizer.  The other HP laptops use Wacom.  If I recall, the desktop uses NextWindow.  The tx2 series come with model numbers like tx2 1025dx where the Wacom versions can be either tm2, tx2xxx, and the dv3.  So far for the N-Trig digitizer only one firmware has been able to support four fingers consistently but the most current one supports two fingers for the HP.  As for Wacom, the tm2 and the dv3 laptops can support two fingers at this time and I am not for sure if they are capable of having more in the future or not.  And you already read about the tx2xxx series having one finger.

As for Ubuntu multi-touch support on these devices, Wacom has some gestures built in their code for it right now but I don't think that the tm2 model has been added to the code yet.  However, the linuxwacom driver development tends to move pretty quick so I can't see it being too much of a problem in getting the tm2 working pretty soon.  As for N-trig, it does not provide any Linux support at this time, but there are developers that are actively working on it.  There is a driver available for N-trig in Linux that will provide single finger support.  I have created a two-finger scroll driver for the Vista and Windows 7 firmware that seems to be working for HP laptops.  Carlos Garnacho has made updates to the evdev driver that should provide multi-pointer capabilities for the N-Trig devices and does provide updates for Gnome.  He has a demo that uses Eye of Gnome with multitouch.  I am not for sure if it will make it into Lucid or not, but the source is available to compile if it is not.

I hope that information helps.

---

### Post by akshay.sulakhe on 2010-02-06
@Ayuthia :-Thanks very much. Now i need multi touch..is the tx2500 series different than tx2...m really confused(again)...so is it that tx1000 series has multi-touch..and i have heard that tx1000 series has some heating and wi-fi issues...which are fixed in tx2000 series...so bottom line what is the difference between tx2500,tx2..m not going for tm series..no dvd drive and performance is hit...due to those intel cpu's(low voltage one's)...what shud i tell in store..which model number i want...please help..thanks...

---

### Post by Favux on 2010-02-06
In order from oldest to newest.

TX1000 - touch screen (single finger touch); has stylus (pen) but not accurate because it isn't a digitizer

TX2000 - Wacom digitizer (stylus) + touch screen (single finger touch)
TX2500 - Wacom digitizer (stylus) + touch screen (single finger touch)

TX2 - N-trig 'digitizer', which acts as a digitizer and a touch screen in one device, instead of two separate devices (a digitizer and a touch screen) sandwiched together like the Wacom versions.  It can be 1 or 2 or more finger touch depending on firmware and drivers.  So far 1 or 2 finger.

TM2 - Wacom digitizer (stylus) + touch screen (2 finger touch).  Not clear if it can be more than two finger.

---

### Post by hypatia on 2010-03-11
I have a TM2 and it only supports two-finger multi-touch.

---

### Post by rsambuca on 2010-03-12
> **hypatia said:**
> I have a TM2 and it only supports two-finger multi-touch.

Have you installed linux on it?

---

### Post by hypatia on 2010-03-13
> **rsambuca said:**
> Have you installed linux on it?

Yup!  Was running 64-bit 9.10 for a while, but a bunch of things need 10.04 so I installed that this week.  There's a thread here:

[http://ubuntuforums.org/showthread.php?t=1410752](http://ubuntuforums.org/showthread.php?t=1410752)

where folks are working on getting all the parts going.

---

### Post by Hiphonepro on 2010-04-13
I have a TX2z and just loaded Ubuntu 10.04 beta 2 and the touchscreen works OTB but the stylus only clicks upon touching the screen and the finger only makes the pointer move you cant click anything. [FONT=monospace]Also you cant use the button on the stylus. My question is, is there a way to set this so it has the multi touch function. I ran this command in terminal [/FONT]xinput list and it shows all the ntrig drivers installed.

---

### Post by Ayuthia on 2010-04-13
> **Hiphonepro said:**
> I have a TX2z and just loaded Ubuntu 10.04 beta 2 and the touchscreen works OTB but the stylus only clicks upon touching the screen and the finger only makes the pointer move you cant click anything. [FONT=monospace]Also you cant use the button on the stylus. My question is, is there a way to set this so it has the multi touch function. I ran this command in terminal [/FONT]xinput list and it shows all the ntrig drivers installed.

Right now there is no official multi touch function for the N-trig device.  As for the pen, can you post your /var/log/Xorg.0.log results?  I just want to verify if yours is using evdev or wacom for its driver.

Even though the touchscreen works out of the box, I think that it might be missing the correct codes to make the pen work with evdev.  Most of the people here are using the Wacom driver.  Here is the [link]("http://ubuntuforums.org/showthread.php?t=1252492") where most of the discussion occurs.  [Post 891]("http://ubuntuforums.org/showpost.php?p=9111274&postcount=891") has a link to get an installer to automatically download the updated kernel module source and Wacom driver.  The only thing that would remain after that would be to configure it.

---

### Post by Hiphonepro on 2010-04-13
Heres my file and ill see if I can go to that thread and get it working
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux adam-laptop 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:20:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-20-generic root=UUID=ef645e2d-007c-42a0-a29b-be691a92ea7e ro quiet splash
Build Date: 12 April 2010  03:38:27PM
xorg-server 2:1.7.6-2ubuntu3 (Alexander Sack <asac@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 13 15:33:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9612:103c:3045 ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xc0000000/268435456, 0xd2300000/65536, 0xd2200000/1048576, I/O @ 0x00005000/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9612) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x14eb780
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics " (Chipset = 0x9612)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3045)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd2300000
(--) fglrx(0): I/O port at 0x00005000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780M
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 327680 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x14000000)
(II) fglrx(0): Interrupt handler installed at IRQ 29.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: LCD on internal LVDS [lvds]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CMO  Model: 1233  Serial#: 0
(II) fglrx(0): Year: 2008  Week: 45
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 26  vert.: 17
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.560 redY: 0.350   greenX: 0.340 greenY: 0.560
(II) fglrx(0): blueX: 0.159 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 69.3 MHz   Image Size:  260 x 170 mm
(II) fglrx(0): h_active: 1280  h_sync: 1320  h_sync_end 1346 h_blank_end 1412 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 807 v_blanking: 818 v_border: 0
(II) fglrx(0):  N121IB-L06
(II) fglrx(0):  CMO
(II) fglrx(0):  N121IB-L06
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff000daf331200000000
(II) fglrx(0):     2d120103801a11780a61c58f59578f28
(II) fglrx(0):     23505400000001010101010101010101
(II) fglrx(0):     010101010101121b008450201230281a
(II) fglrx(0):     340004aa10000018000000fe004e3132
(II) fglrx(0):     3149422d4c30360a2020000000fe0043
(II) fglrx(0):     4d4f0a202020202020202020000000fe
(II) fglrx(0):     004e31323149422d4c30360a202000c4
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output LVDS has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output TV has no monitor section
(II) fglrx(0): Output COMPONENT_VIDEO has no monitor section
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output TV disconnected
(II) fglrx(0): Output COMPONENT_VIDEO disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output LVDS using initial mode 1280x800
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 3200 Graphics  has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7feed91f7000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-20-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd2ff7000 FBMappedSize: 0x01004000
(II) fglrx(0): Reserved 0x02500000 bytes of sideport memory for power saving
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1280) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2000
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid Horizontal and Vertical Lines
    Driver provided ScreenToScreenBitBlt replacement
    Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
(II) fglrx(0): Cannot set TV horizontal size.
(II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
(II) fglrx(0): Cannot set TV horizontal position.
(II) fglrx(0): Cannot set TV vertical position.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HP Webcam (/dev/input/event7)
(**) HP Webcam: Applying InputClass "evdev keyboard catchall"
(**) HP Webcam: always reports core events
(**) HP Webcam: Device: "/dev/input/event7"
(II) HP Webcam: Found keys
(II) HP Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/event10)
(**) N-Trig Touchscreen: Applying InputClass "evdev touchscreen catchall"
(**) N-Trig Touchscreen: always reports core events
(**) N-Trig Touchscreen: Device: "/dev/input/event10"
(II) N-Trig Touchscreen: Found absolute axes
(II) N-Trig Touchscreen: Found x and y absolute axes
(II) N-Trig Touchscreen: Found absolute touchscreen
(II) N-Trig Touchscreen: Configuring as touchscreen
(**) N-Trig Touchscreen: YAxisMapping: buttons 4 and 5
(**) N-Trig Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "N-Trig Touchscreen" (type: TOUCHSCREEN)
(II) N-Trig Touchscreen: initialized for absolute axes.
(II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig Pen (/dev/input/event8)
(**) N-Trig Pen: Applying InputClass "evdev tablet catchall"
(**) N-Trig Pen: always reports core events
(**) N-Trig Pen: Device: "/dev/input/event8"
(II) N-Trig Pen: Found 1 mouse buttons
(II) N-Trig Pen: Found absolute axes
(II) N-Trig Pen: Found x and y absolute axes
(II) N-Trig Pen: Found absolute tablet.
(II) N-Trig Pen: Configuring as tablet
(**) N-Trig Pen: YAxisMapping: buttons 4 and 5
(**) N-Trig Pen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "N-Trig Pen" (type: TABLET)
(II) N-Trig Pen: initialized for absolute axes.
(II) config/udev: Adding input device N-Trig Pen (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig MultiTouch (/dev/input/event9)
(**) N-Trig MultiTouch: Applying InputClass "evdev touchscreen catchall"
(**) N-Trig MultiTouch: always reports core events
(**) N-Trig MultiTouch: Device: "/dev/input/event9"
(II) N-Trig MultiTouch: Found absolute axes
(II) N-Trig MultiTouch: Found x and y absolute axes
(II) N-Trig MultiTouch: Found absolute touchscreen
(II) N-Trig MultiTouch: Configuring as touchscreen
(**) N-Trig MultiTouch: YAxisMapping: buttons 4 and 5
(**) N-Trig MultiTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "N-Trig MultiTouch" (type: TOUCHSCREEN)
(II) N-Trig MultiTouch: initialized for absolute axes.
(II) config/udev: Adding input device N-Trig MultiTouch (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event12"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) N-Trig Touchscreen: unable to handle keycode 333
(WW) fglrx(0): Cannot get updated TV attributes.
(II) XKB: generating xkmfile /var/lib/xkb/server-8199213BFD9155D5FF97EC02B93E2C9FEC5A1EBB.xkm
(II) fglrx(0): AC Offline
```

---

### Post by Hiphonepro on 2010-04-13
Thank you sooooo much that link and the ease of adding the touch was AWESOME someone had to have put a lot of work into that I run a touch screen forum and would like to invite anyone who has a touch screen device just search my name in youtube.
For the record I have huge hope for Linux in this arena because Ipad is a joke and Microsoft has absolutely no real development. I have given up on both and now here I am.

---

### Post by lawrencegoodman on 2010-06-18
Just for the record: I upgraded to kernel 2.6.34 and now have full touch capability (though not multitouch). I figure in time it will come.

---

### Post by cocoa117 on 2010-06-24
> **Favux said:**
> In order from oldest to newest.

TX1000 - touch screen (single finger touch); has stylus (pen) but not accurate because it isn't a digitizer

TX2000 - Wacom digitizer (stylus) + touch screen (single finger touch)
TX2500 - Wacom digitizer (stylus) + touch screen (single finger touch)

TX2 - N-trig 'digitizer', which acts as a digitizer and a touch screen in one device, instead of two separate devices (a digitizer and a touch screen) sandwiched together like the Wacom versions.  It can be 1 or 2 or more finger touch depending on firmware and drivers.  So far 1 or 2 finger.

TM2 - Wacom digitizer (stylus) + touch screen (2 finger touch).  Not clear if it can be more than two finger.

Thanks for this, now it clarified my old question.

---

