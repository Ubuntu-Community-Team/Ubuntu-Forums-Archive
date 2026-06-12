---
title: "MSI CX620 ATI 5470 not working in Kubuntu Lucid"
date: 2010-06-10
forum: Hardware
---

### Post by michael vernersen on 2010-06-10
HI...

  Yesterday i got a new laptop MSI CX-620 - [http://www.msi.com/index.php?func=newsdesc&news_no=940](http://www.msi.com/index.php?func=newsdesc&news_no=940)
  and it's the model with the ATI 5470 graphics card in..
  I know for sure that this would cause some problems instead of using a GeForce graphics Card , but i read in
  this forum that someone with a simular card on a ASUS laptop has it up running..
  I now have tried everything i can find on the net but whatever thing i try i'll end up with either an 
  installation error when i use ATI Catalyst Drivers 10-2 - 10.5 from ATI or a blank screen when i use
  the drivers Kubuntu 10.4 Lucid has included.

  Does anyone have a working solution up running on this Graphics Card , or evven better a solution
  which actually works for the MSI....

  Right now i'm trying thing out on Fedore 13 , but i'll prefer the Kubuntu 10.4...

  Thanks

  /Michael

---

### Post by michael vernersen on 2010-06-19
A Little update...

  Today i have tried the Catalyst 10.6 driver on Ubuntu fresh install.
  Still no success. I have now included the xorg.conf + log file...

  xorg.conf
_______________________________________________________________________

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
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

Xorg.0.log
_______________________________________________________________________

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux michael 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=d6887afb-962d-4666-9327-e92a008d9031 ro quiet splash
Build Date: 09 June 2010  11:00:55AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 19 19:13:22 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:0046:1462:1055 Intel Corporation Core Processor Integrated Graphics Controller rev 18, Mem @ 0xf0400000/4194304, 0xd0000000/268435456, I/O @ 0x0000e080/8
(--) PCI: (0:1:0:0) 1002:68e0:1462:1055 ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] rev 0, Mem @ 0xe0000000/268435456, 0xf0020000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
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
        compiled for 1.7.1, module version = 8.74.4
        Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.7.1, module version = 8.74.4
(II) ATI Proprietary Linux Driver Version Identifier:8.74.4
(II) ATI Proprietary Linux Driver Release Identifier: 8.741                                
(II) ATI Proprietary Linux Driver Build Date: May 27 2010 12:52:57
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x68E0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0xe39680
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.1.0
        ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): ATI 2D Acceleration Architecture enabled
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 5400 Series " (Chipset = 0x68e0)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x1055)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf0020000
(--) fglrx(0): I/O port at 0x0000d000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Bad V_BIOS checksum
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdapter failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "fglrxdrm"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


ANY CLUE AT ALL , Getting serious desperate..

A knew it was a mistake buying ATI but didn't thing it was that bad...

THX

/Michael

---

### Post by AtexPatex on 2010-07-05
Hello!

I have exactly the same problem. The same notebook, and no luck under Linux at all. I tried  Ubuntu/Kubuntu, but nothing. As soon as I install any kind of Ati driver, I get nothing, but black screen...
I have installed win7, but don't want to keep it. Please tell me, if you have any success..
THX!!!

Atex

---

### Post by AtexPatex on 2010-10-28
Hi!

I have exactly the same notebook, and had the same problem.
I have managed to solve it. You have to update your bios with the newest driver from msi.com. For this you need a pendrive.
After this procedure you can select in the bios, that the primary driver not to be switchable, so linux can find it. I used Ubuntu 10.10 (Maverick) with ati driver 10.10.

Atex

---

### Post by ayqazi on 2011-03-20
Hi,

I just bought an HP laptop with switchable graphics - it uses an integrated Radeon HD 4250 by default and a Radeon HD 4570 discrete.  Under Windows anyway.

Under Linux I get exactly the same problem when trying to force the 5470 in the BIOS - and the HDMI port ONLY works with the 5470 (confirmed under windows).

Of course, HP being HP, they do not let me have a 'switchable' graphics option in the BIOS, and I was wondering if anyone had got it working using software solutions?

Thanks

Regards,
   Asfand

---

