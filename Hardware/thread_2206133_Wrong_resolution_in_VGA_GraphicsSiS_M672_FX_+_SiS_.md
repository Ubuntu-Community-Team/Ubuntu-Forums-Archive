---
title: "Wrong resolution in VGA Graphics	SiS M672 FX + SiS 307ELV and Xorg 1.13.3"
date: 2014-02-17
forum: Hardware
---

### Post by ÜberJorge on 2014-02-17
Hello!
Notebook with ubuntu 12.04.4 don't have right resolution 16x10 = 1280x800, only appears two 4x3 resolutions, either 1024x768, or 800x600.
Videocard is: SiS M672 FX + SiS 307ELV.
Core Logic: SiS M672 FX + SiS 968
X Server version is: 1.13.3.
Site of notebook model: [http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=3&DetailID=1023&DetailName=Feature&MenuID=93&LanID=0](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=3&DetailID=1023&DetailName=Feature&MenuID=93&LanID=0)

---------------
output of hwinfo --monitor:

23: None 00.1: 10002 LCD Monitor
  [Created at monitor.95]
  Unique ID: jyhG.SRB6MXIgU6D
  Hardware Class: monitor
  Model: "AUO LCD Monitor"
  Vendor: AUO "AUO"
  Device: eisa 0x4444 
  Resolution: 1280x800@60Hz
  Size: 304x190 mm
  Detailed Timings #0:
     Resolution: 1280x800
     Horizontal: 1280 1328 1360 1405 (+48 +80 +125) -hsync
       Vertical:  800  803  809  822 (+3 +9 +22) -vsync
    Frequencies: 69.30 MHz, 49.32 kHz, 60.00 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
--------------------

$ sudo lshw -C display

  *-display DISPONÍVEL    
       descrição: VGA compatible controller
       produto: 771/671 PCIE VGA Display Adapter
       fabricante: Silicon Integrated Systems [SiS]
       ID físico: 0
       informações do barramento: pci@0000:01:00.0
       versão: 10
       largura: 32 bits
       clock: 66MHz
       capacidades: pm agp agp-3.0 vga_controller cap_list
       configuração: latency=0
       recursos: memória:c0000000-cfffffff memória:d4000000-d401ffff porta de E/S:9000(tamanho=128)
------------------------------

What do I do?
Thank you very much!

---

### Post by Yellow Pasque on 2014-02-18
Get updated SiS driver here: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)
It should allow you to do 1280x800

---

### Post by ÜberJorge on 2014-02-18
I installed the package [xserver-xorg-video-sis-lts-raring_0.10.7-0ubuntu5~precise2_amd64.deb]("https://launchpad.net/%7Edtl131/+archive/mediahacks/+files/xserver-xorg-video-sis-lts-raring_0.10.7-0ubuntu5%7Eprecise2_amd64.deb"), but it doesn't solved the problem. And I was unable to install the [xserver-xorg-video-sis-lts-quantal_0.10.7-0ubuntu5~precise2_amd64.deb]("https://launchpad.net/%7Edtl131/+archive/mediahacks/+files/xserver-xorg-video-sis-lts-quantal_0.10.7-0ubuntu5%7Eprecise2_amd64.deb") because of the dependencies.
Thanks for now!

---

### Post by Yellow Pasque on 2014-02-18
The LTS packages are for Ubuntu Precise/12.04.

Once you install the correct package ( [https://launchpad.net/~dtl131/+archive/mediahacks/+files/xserver-xorg-video-sis_0.10.7-0ubuntu5%7Eraring1_amd64.deb](https://launchpad.net/~dtl131/+archive/mediahacks/+files/xserver-xorg-video-sis_0.10.7-0ubuntu5%7Eraring1_amd64.deb) ), post the /var/log/Xorg.0.log (use code tags).

---

### Post by Bucky Ball on 2014-02-19
Don't know about get updated drivers, but get upgraded OS. 13.04 is no longer supported. Might be your problem as don't think you'll be getting any drivers from non-existent repositories without some tweaking to the backports or elsewhere.

No updates, and this includes security updates. As time goes by you'll probably get more unexplainable errors, more vulnerable to security breaches if you are online, and less chances of support or solution.

I use arandr for resolution issues generally. It tends to give native resolutions when other things don't (including the third-party nvidia and amd configuration apps). It's in the repositories which means I doubt you'll be able to install it directly from there. You'd need to do it manually.

---

### Post by ÜberJorge on 2014-02-19
> **Bucky Ball said:**
> Don't know about get updated drivers, but get upgraded OS. 13.04 is no longer supported. Might be your problem as don't think you'll be getting any drivers from non-existent repositories without some tweaking to the backports or elsewhere.

No updates, and this includes security updates. As time goes by you'll probably get more unexplainable errors, more vulnerable to security breaches if you are online, and less chances of support or solution.

I use arandr for resolution issues generally. It tends to give native resolutions when other things don't (including the third-party nvidia and amd configuration apps). It's in the repositories which means I doubt you'll be able to install it directly from there. You'd need to do it manually.

Oh, sorry. My ubuntu is the LTS Precise Pangolin 12.04. Corrected.

---

### Post by Bucky Ball on 2014-02-19
In that case;

> **Bucky Ball said:**
> 

I use arandr for resolution issues generally. It tends to give native resolutions when other things don't (including the third-party nvidia and amd configuration apps). It's in the repositories which means I doubt you'll be able to install it directly from there. You'd need to do it manually and not sure how.

I will also add that SiS graphics can be problematic in Ubuntu.

---

### Post by Yellow Pasque on 2014-02-19
> **Temüjin said:**
>  post the /var/log/Xorg.0.log (use code tags).

^

---

### Post by ÜberJorge on 2014-02-20
The output of /var/log/Xorg.0.log is:

```
[    19.291] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    19.291] X Protocol Version 11, Revision 0
[    19.291] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    19.291] Current Operating System: Linux mayara-I41SI 3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 x86_64
[    19.291] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic root=UUID=40dbb5df-2179-4274-8209-664cef8fcb93 ro quiet splash vt.handoff=7
[    19.291] Build Date: 16 October 2013  04:46:41PM
[    19.291] xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.291] Current version of pixman: 0.30.2
[    19.291]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    19.291] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.291] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 20 14:24:23 2014
[    19.334] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.373] (==) No Layout section.  Using the first Screen section.
[    19.373] (==) No screen section available. Using defaults.
[    19.373] (**) |-->Screen "Default Screen Section" (0)
[    19.373] (**) |   |-->Monitor "<default monitor>"
[    19.373] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.373] (==) Automatically adding devices
[    19.373] (==) Automatically enabling devices
[    19.373] (==) Automatically adding GPU devices
[    19.385] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.385]     Entry deleted from font path.
[    19.385] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.385] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.385] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.385] (II) Loader magic: 0x7f31be830c20
[    19.385] (II) Module ABI versions:
[    19.385]     X.Org ANSI C Emulation: 0.4
[    19.385]     X.Org Video Driver: 13.1
[    19.385]     X.Org XInput driver : 18.0
[    19.385]     X.Org Server Extension : 7.0
[    19.386] (--) PCI:*(0:1:0:0) 1039:6351:1019:5055 rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[    19.386] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.387] Initializing built-in extension Generic Event Extension
[    19.387] Initializing built-in extension SHAPE
[    19.387] Initializing built-in extension MIT-SHM
[    19.387] Initializing built-in extension XInputExtension
[    19.387] Initializing built-in extension XTEST
[    19.387] Initializing built-in extension BIG-REQUESTS
[    19.387] Initializing built-in extension SYNC
[    19.387] Initializing built-in extension XKEYBOARD
[    19.387] Initializing built-in extension XC-MISC
[    19.387] Initializing built-in extension SECURITY
[    19.387] Initializing built-in extension XINERAMA
[    19.387] Initializing built-in extension XFIXES
[    19.387] Initializing built-in extension RENDER
[    19.387] Initializing built-in extension RANDR
[    19.387] Initializing built-in extension COMPOSITE
[    19.387] Initializing built-in extension DAMAGE
[    19.387] Initializing built-in extension MIT-SCREEN-SAVER
[    19.387] Initializing built-in extension DOUBLE-BUFFER
[    19.387] Initializing built-in extension RECORD
[    19.387] Initializing built-in extension DPMS
[    19.387] Initializing built-in extension X-Resource
[    19.387] Initializing built-in extension XVideo
[    19.387] Initializing built-in extension XVideo-MotionCompensation
[    19.387] Initializing built-in extension XFree86-VidModeExtension
[    19.387] Initializing built-in extension XFree86-DGA
[    19.387] Initializing built-in extension XFree86-DRI
[    19.387] Initializing built-in extension DRI2
[    19.387] (II) LoadModule: "glx"
[    19.423] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.493] (II) Module glx: vendor="X.Org Foundation"
[    19.493]     compiled for 1.13.3, module version = 1.0.0
[    19.493]     ABI class: X.Org Server Extension, version 7.0
[    19.493] (==) AIGLX enabled
[    19.502] Loading extension GLX
[    19.502] (==) Matched sis as autoconfigured driver 0
[    19.502] (==) Matched vesa as autoconfigured driver 1
[    19.502] (==) Matched modesetting as autoconfigured driver 2
[    19.502] (==) Matched fbdev as autoconfigured driver 3
[    19.502] (==) Assigned the driver to the xf86ConfigLayout
[    19.502] (II) LoadModule: "sis"
[    19.502] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    19.591] (II) Module sis: vendor="X.Org Foundation"
[    19.591]     compiled for 1.13.3, module version = 0.10.7
[    19.591]     Module class: X.Org Video Driver
[    19.591]     ABI class: X.Org Video Driver, version 13.1
[    19.591] (II) LoadModule: "vesa"
[    19.592] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.627] (II) Module vesa: vendor="X.Org Foundation"
[    19.627]     compiled for 1.13.3, module version = 2.3.2
[    19.627]     Module class: X.Org Video Driver
[    19.627]     ABI class: X.Org Video Driver, version 13.1
[    19.627] (II) LoadModule: "modesetting"
[    19.628] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    19.668] (II) Module modesetting: vendor="X.Org Foundation"
[    19.668]     compiled for 1.13.3, module version = 0.7.0
[    19.668]     Module class: X.Org Video Driver
[    19.668]     ABI class: X.Org Video Driver, version 13.1
[    19.668] (II) LoadModule: "fbdev"
[    19.669] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.896] (II) Module fbdev: vendor="X.Org Foundation"
[    19.896]     compiled for 1.13.3, module version = 0.4.3
[    19.896]     Module class: X.Org Video Driver
[    19.896]     ABI class: X.Org Video Driver, version 13.1
[    19.896] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[    19.896] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[    19.896] (II) VESA: driver for VESA chipsets: vesa
[    19.896] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    19.896] (II) FBDEV: driver for framebuffer: fbdev
[    19.896] (++) using VT number 7

[    19.896] (WW) Falling back to old probe method for sis
[    19.897] (--) Assigning device section with no busID to primary device
[    19.897] (WW) Falling back to old probe method for modesetting
[    19.897] (EE) open /dev/dri/card0: No such file or directory
[    19.897] (WW) Falling back to old probe method for fbdev
[    19.897] (II) Loading sub module "fbdevhw"
[    19.897] (II) LoadModule: "fbdevhw"
[    19.897] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.931] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.931]     compiled for 1.13.3, module version = 0.0.2
[    19.931]     ABI class: X.Org Video Driver, version 13.1
[    19.931] (II) Loading sub module "vbe"
[    19.931] (II) LoadModule: "vbe"
[    19.932] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.987] (II) Module vbe: vendor="X.Org Foundation"
[    19.987]     compiled for 1.13.3, module version = 1.1.0
[    19.987]     ABI class: X.Org Video Driver, version 13.1
[    19.987] (II) Loading sub module "int10"
[    19.987] (II) LoadModule: "int10"
[    19.987] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.033] (II) Module int10: vendor="X.Org Foundation"
[    20.033]     compiled for 1.13.3, module version = 1.0.0
[    20.033]     ABI class: X.Org Video Driver, version 13.1
[    20.033] (II) VESA(0): initializing int10
[    20.038] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    20.040] (II) VESA(0): VESA BIOS detected
[    20.040] (II) VESA(0): VESA VBE Version 3.0
[    20.040] (II) VESA(0): VESA VBE Total Mem: 131072 kB
[    20.040] (II) VESA(0): VESA VBE OEM: SiS
[    20.040] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    20.040] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    20.040] (II) VESA(0): VESA VBE OEM Product: 6330
[    20.040] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.24a
[    20.056] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.056] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    20.056] (==) VESA(0): RGB weight 888
[    20.056] (==) VESA(0): Default visual is TrueColor
[    20.056] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.056] (II) Loading sub module "ddc"
[    20.056] (II) LoadModule: "ddc"
[    20.056] (II) Module "ddc" already built-in
[    20.147] (II) VESA(0): VESA VBE DDC supported
[    20.147] (II) VESA(0): VESA VBE DDC Level none
[    20.147] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    20.180] (II) VESA(0): VESA VBE DDC read failed
[    20.180] (II) VESA(0): Searching for matching VESA mode(s):
[    20.180] Mode: 101 (640x480)
[    20.180]     ModeAttributes: 0x9f
[    20.180]     WinAAttributes: 0x7
[    20.180]     WinBAttributes: 0x0
[    20.180]     WinGranularity: 64
[    20.180]     WinSize: 64
[    20.180]     WinASegment: 0xa000
[    20.180]     WinBSegment: 0xa000
[    20.180]     WinFuncPtr: 0xc00087f9
[    20.180]     BytesPerScanline: 640
[    20.181]     XResolution: 640
[    20.181]     YResolution: 480
[    20.181]     XCharSize: 8
[    20.181]     YCharSize: 16
[    20.181]     NumberOfPlanes: 1
[    20.181]     BitsPerPixel: 8
[    20.181]     NumberOfBanks: 1
[    20.181]     MemoryModel: 4
[    20.181]     BankSize: 0
[    20.181]     NumberOfImages: 24
[    20.181]     RedMaskSize: 0
[    20.181]     RedFieldPosition: 0
[    20.181]     GreenMaskSize: 0
[    20.181]     GreenFieldPosition: 0
[    20.181]     BlueMaskSize: 0
[    20.181]     BlueFieldPosition: 0
[    20.181]     RsvdMaskSize: 0
[    20.181]     RsvdFieldPosition: 0
[    20.181]     DirectColorModeInfo: 0
[    20.181]     PhysBasePtr: 0xc0000000
[    20.181]     LinBytesPerScanLine: 640
[    20.181]     BnkNumberOfImagePages: 24
[    20.181]     LinNumberOfImagePages: 24
[    20.181]     LinRedMaskSize: 0
[    20.181]     LinRedFieldPosition: 0
[    20.181]     LinGreenMaskSize: 0
[    20.181]     LinGreenFieldPosition: 0
[    20.181]     LinBlueMaskSize: 0
[    20.181]     LinBlueFieldPosition: 0
[    20.181]     LinRsvdMaskSize: 0
[    20.181]     LinRsvdFieldPosition: 0
[    20.181]     MaxPixelClock: 0
[    20.181] Mode: 100 (640x400)
[    20.181]     ModeAttributes: 0x9f
[    20.181]     WinAAttributes: 0x7
[    20.181]     WinBAttributes: 0x0
[    20.181]     WinGranularity: 64
[    20.181]     WinSize: 64
[    20.181]     WinASegment: 0xa000
[    20.181]     WinBSegment: 0xa000
[    20.181]     WinFuncPtr: 0xc00087f9
[    20.181]     BytesPerScanline: 640
[    20.181]     XResolution: 640
[    20.181]     YResolution: 400
[    20.181]     XCharSize: 8
[    20.181]     YCharSize: 16
[    20.181]     NumberOfPlanes: 1
[    20.181]     BitsPerPixel: 8
[    20.181]     NumberOfBanks: 1
[    20.181]     MemoryModel: 4
[    20.181]     BankSize: 0
[    20.181]     NumberOfImages: 31
[    20.181]     RedMaskSize: 0
[    20.181]     RedFieldPosition: 0
[    20.181]     GreenMaskSize: 0
[    20.181]     GreenFieldPosition: 0
[    20.181]     BlueMaskSize: 0
[    20.181]     BlueFieldPosition: 0
[    20.181]     RsvdMaskSize: 0
[    20.181]     RsvdFieldPosition: 0
[    20.181]     DirectColorModeInfo: 0
[    20.181]     PhysBasePtr: 0xc0000000
[    20.181]     LinBytesPerScanLine: 640
[    20.181]     BnkNumberOfImagePages: 31
[    20.181]     LinNumberOfImagePages: 31
[    20.181]     LinRedMaskSize: 0
[    20.181]     LinRedFieldPosition: 0
[    20.181]     LinGreenMaskSize: 0
[    20.181]     LinGreenFieldPosition: 0
[    20.181]     LinBlueMaskSize: 0
[    20.181]     LinBlueFieldPosition: 0
[    20.181]     LinRsvdMaskSize: 0
[    20.181]     LinRsvdFieldPosition: 0
[    20.181]     MaxPixelClock: 0
[    20.182] Mode: 103 (800x600)
[    20.182]     ModeAttributes: 0x9f
[    20.182]     WinAAttributes: 0x7
[    20.182]     WinBAttributes: 0x0
[    20.182]     WinGranularity: 64
[    20.182]     WinSize: 64
[    20.182]     WinASegment: 0xa000
[    20.182]     WinBSegment: 0xa000
[    20.182]     WinFuncPtr: 0xc00087f9
[    20.182]     BytesPerScanline: 800
[    20.182]     XResolution: 800
[    20.182]     YResolution: 600
[    20.182]     XCharSize: 8
[    20.182]     YCharSize: 16
[    20.182]     NumberOfPlanes: 1
[    20.182]     BitsPerPixel: 8
[    20.182]     NumberOfBanks: 1
[    20.182]     MemoryModel: 4
[    20.182]     BankSize: 0
[    20.182]     NumberOfImages: 15
[    20.182]     RedMaskSize: 0
[    20.182]     RedFieldPosition: 0
[    20.182]     GreenMaskSize: 0
[    20.182]     GreenFieldPosition: 0
[    20.182]     BlueMaskSize: 0
[    20.182]     BlueFieldPosition: 0
[    20.182]     RsvdMaskSize: 0
[    20.182]     RsvdFieldPosition: 0
[    20.182]     DirectColorModeInfo: 0
[    20.182]     PhysBasePtr: 0xc0000000
[    20.182]     LinBytesPerScanLine: 800
[    20.182]     BnkNumberOfImagePages: 15
[    20.182]     LinNumberOfImagePages: 15
[    20.182]     LinRedMaskSize: 0
[    20.182]     LinRedFieldPosition: 0
[    20.182]     LinGreenMaskSize: 0
[    20.182]     LinGreenFieldPosition: 0
[    20.182]     LinBlueMaskSize: 0
[    20.182]     LinBlueFieldPosition: 0
[    20.182]     LinRsvdMaskSize: 0
[    20.182]     LinRsvdFieldPosition: 0
[    20.182]     MaxPixelClock: 0
[    20.182] Mode: 104 (1024x768)
[    20.182]     ModeAttributes: 0x1f
[    20.182]     WinAAttributes: 0x7
[    20.182]     WinBAttributes: 0x0
[    20.182]     WinGranularity: 64
[    20.182]     WinSize: 64
[    20.183]     WinASegment: 0xa000
[    20.183]     WinBSegment: 0xa000
[    20.183]     WinFuncPtr: 0xc00087f9
[    20.183]     BytesPerScanline: 128
[    20.183]     XResolution: 1024
[    20.183]     YResolution: 768
[    20.183]     XCharSize: 8
[    20.183]     YCharSize: 16
[    20.183]     NumberOfPlanes: 4
[    20.183]     BitsPerPixel: 4
[    20.183]     NumberOfBanks: 1
[    20.183]     MemoryModel: 3
[    20.183]     BankSize: 0
[    20.183]     NumberOfImages: 15
[    20.183]     RedMaskSize: 0
[    20.183]     RedFieldPosition: 0
[    20.183]     GreenMaskSize: 0
[    20.183]     GreenFieldPosition: 0
[    20.183]     BlueMaskSize: 0
[    20.183]     BlueFieldPosition: 0
[    20.183]     RsvdMaskSize: 0
[    20.183]     RsvdFieldPosition: 0
[    20.183]     DirectColorModeInfo: 0
[    20.183]     PhysBasePtr: 0xc0000000
[    20.183]     LinBytesPerScanLine: 128
[    20.183]     BnkNumberOfImagePages: 15
[    20.183]     LinNumberOfImagePages: 15
[    20.183]     LinRedMaskSize: 0
[    20.183]     LinRedFieldPosition: 0
[    20.183]     LinGreenMaskSize: 0
[    20.183]     LinGreenFieldPosition: 0
[    20.183]     LinBlueMaskSize: 0
[    20.183]     LinBlueFieldPosition: 0
[    20.183]     LinRsvdMaskSize: 0
[    20.183]     LinRsvdFieldPosition: 0
[    20.183]     MaxPixelClock: 0
[    20.183] Mode: 105 (1024x768)
[    20.183]     ModeAttributes: 0x9f
[    20.183]     WinAAttributes: 0x7
[    20.183]     WinBAttributes: 0x0
[    20.183]     WinGranularity: 64
[    20.183]     WinSize: 64
[    20.183]     WinASegment: 0xa000
[    20.183]     WinBSegment: 0xa000
[    20.183]     WinFuncPtr: 0xc00087f9
[    20.183]     BytesPerScanline: 1024
[    20.183]     XResolution: 1024
[    20.183]     YResolution: 768
[    20.183]     XCharSize: 8
[    20.183]     YCharSize: 16
[    20.183]     NumberOfPlanes: 1
[    20.183]     BitsPerPixel: 8
[    20.183]     NumberOfBanks: 1
[    20.183]     MemoryModel: 4
[    20.183]     BankSize: 0
[    20.183]     NumberOfImages: 9
[    20.183]     RedMaskSize: 0
[    20.183]     RedFieldPosition: 0
[    20.183]     GreenMaskSize: 0
[    20.183]     GreenFieldPosition: 0
[    20.183]     BlueMaskSize: 0
[    20.183]     BlueFieldPosition: 0
[    20.183]     RsvdMaskSize: 0
[    20.183]     RsvdFieldPosition: 0
[    20.183]     DirectColorModeInfo: 0
[    20.183]     PhysBasePtr: 0xc0000000
[    20.183]     LinBytesPerScanLine: 1024
[    20.183]     BnkNumberOfImagePages: 9
[    20.183]     LinNumberOfImagePages: 9
[    20.183]     LinRedMaskSize: 0
[    20.183]     LinRedFieldPosition: 0
[    20.183]     LinGreenMaskSize: 0
[    20.183]     LinGreenFieldPosition: 0
[    20.183]     LinBlueMaskSize: 0
[    20.183]     LinBlueFieldPosition: 0
[    20.183]     LinRsvdMaskSize: 0
[    20.183]     LinRsvdFieldPosition: 0
[    20.183]     MaxPixelClock: 0
[    20.184] Mode: 10d (320x200)
[    20.184]     ModeAttributes: 0x9b
[    20.184]     WinAAttributes: 0x7
[    20.184]     WinBAttributes: 0x0
[    20.184]     WinGranularity: 64
[    20.184]     WinSize: 64
[    20.184]     WinASegment: 0xa000
[    20.184]     WinBSegment: 0xa000
[    20.184]     WinFuncPtr: 0xc00087f9
[    20.184]     BytesPerScanline: 640
[    20.184]     XResolution: 320
[    20.184]     YResolution: 200
[    20.184]     XCharSize: 8
[    20.184]     YCharSize: 8
[    20.184]     NumberOfPlanes: 1
[    20.184]     BitsPerPixel: 15
[    20.184]     NumberOfBanks: 1
[    20.184]     MemoryModel: 6
[    20.184]     BankSize: 0
[    20.184]     NumberOfImages: 63
[    20.184]     RedMaskSize: 5
[    20.184]     RedFieldPosition: 10
[    20.184]     GreenMaskSize: 5
[    20.184]     GreenFieldPosition: 5
[    20.184]     BlueMaskSize: 5
[    20.184]     BlueFieldPosition: 0
[    20.184]     RsvdMaskSize: 0
[    20.184]     RsvdFieldPosition: 0
[    20.184]     DirectColorModeInfo: 0
[    20.184]     PhysBasePtr: 0xc0000000
[    20.184]     LinBytesPerScanLine: 640
[    20.184]     BnkNumberOfImagePages: 63
[    20.184]     LinNumberOfImagePages: 63
[    20.184]     LinRedMaskSize: 5
[    20.184]     LinRedFieldPosition: 10
[    20.184]     LinGreenMaskSize: 5
[    20.184]     LinGreenFieldPosition: 5
[    20.184]     LinBlueMaskSize: 5
[    20.184]     LinBlueFieldPosition: 0
[    20.184]     LinRsvdMaskSize: 0
[    20.184]     LinRsvdFieldPosition: 0
[    20.184]     MaxPixelClock: 0
[    20.184] Mode: 10e (320x200)
[    20.185]     ModeAttributes: 0x9b
[    20.185]     WinAAttributes: 0x7
[    20.185]     WinBAttributes: 0x0
[    20.185]     WinGranularity: 64
[    20.185]     WinSize: 64
[    20.185]     WinASegment: 0xa000
[    20.185]     WinBSegment: 0xa000
[    20.185]     WinFuncPtr: 0xc00087f9
[    20.185]     BytesPerScanline: 640
[    20.185]     XResolution: 320
[    20.185]     YResolution: 200
[    20.185]     XCharSize: 8
[    20.185]     YCharSize: 8
[    20.185]     NumberOfPlanes: 1
[    20.185]     BitsPerPixel: 16
[    20.185]     NumberOfBanks: 1
[    20.185]     MemoryModel: 6
[    20.185]     BankSize: 0
[    20.185]     NumberOfImages: 63
[    20.185]     RedMaskSize: 5
[    20.185]     RedFieldPosition: 11
[    20.185]     GreenMaskSize: 6
[    20.185]     GreenFieldPosition: 5
[    20.185]     BlueMaskSize: 5
[    20.185]     BlueFieldPosition: 0
[    20.185]     RsvdMaskSize: 0
[    20.185]     RsvdFieldPosition: 0
[    20.185]     DirectColorModeInfo: 0
[    20.185]     PhysBasePtr: 0xc0000000
[    20.185]     LinBytesPerScanLine: 640
[    20.185]     BnkNumberOfImagePages: 63
[    20.185]     LinNumberOfImagePages: 63
[    20.185]     LinRedMaskSize: 5
[    20.185]     LinRedFieldPosition: 11
[    20.185]     LinGreenMaskSize: 6
[    20.185]     LinGreenFieldPosition: 5
[    20.185]     LinBlueMaskSize: 5
[    20.185]     LinBlueFieldPosition: 0
[    20.185]     LinRsvdMaskSize: 0
[    20.185]     LinRsvdFieldPosition: 0
[    20.185]     MaxPixelClock: 0
[    20.185] Mode: 110 (640x480)
[    20.185]     ModeAttributes: 0x9b
[    20.185]     WinAAttributes: 0x7
[    20.185]     WinBAttributes: 0x0
[    20.185]     WinGranularity: 64
[    20.185]     WinSize: 64
[    20.185]     WinASegment: 0xa000
[    20.185]     WinBSegment: 0xa000
[    20.185]     WinFuncPtr: 0xc00087f9
[    20.185]     BytesPerScanline: 1280
[    20.185]     XResolution: 640
[    20.185]     YResolution: 480
[    20.185]     XCharSize: 8
[    20.185]     YCharSize: 16
[    20.185]     NumberOfPlanes: 1
[    20.185]     BitsPerPixel: 15
[    20.185]     NumberOfBanks: 1
[    20.185]     MemoryModel: 6
[    20.185]     BankSize: 0
[    20.185]     NumberOfImages: 11
[    20.185]     RedMaskSize: 5
[    20.185]     RedFieldPosition: 10
[    20.185]     GreenMaskSize: 5
[    20.185]     GreenFieldPosition: 5
[    20.185]     BlueMaskSize: 5
[    20.185]     BlueFieldPosition: 0
[    20.185]     RsvdMaskSize: 0
[    20.185]     RsvdFieldPosition: 0
[    20.185]     DirectColorModeInfo: 0
[    20.185]     PhysBasePtr: 0xc0000000
[    20.185]     LinBytesPerScanLine: 1280
[    20.185]     BnkNumberOfImagePages: 11
[    20.185]     LinNumberOfImagePages: 11
[    20.185]     LinRedMaskSize: 5
[    20.185]     LinRedFieldPosition: 10
[    20.185]     LinGreenMaskSize: 5
[    20.185]     LinGreenFieldPosition: 5
[    20.185]     LinBlueMaskSize: 5
[    20.185]     LinBlueFieldPosition: 0
[    20.185]     LinRsvdMaskSize: 0
[    20.185]     LinRsvdFieldPosition: 0
[    20.186]     MaxPixelClock: 0
[    20.186] Mode: 111 (640x480)
[    20.186]     ModeAttributes: 0x9b
[    20.186]     WinAAttributes: 0x7
[    20.186]     WinBAttributes: 0x0
[    20.186]     WinGranularity: 64
[    20.186]     WinSize: 64
[    20.186]     WinASegment: 0xa000
[    20.186]     WinBSegment: 0xa000
[    20.186]     WinFuncPtr: 0xc00087f9
[    20.186]     BytesPerScanline: 1280
[    20.186]     XResolution: 640
[    20.186]     YResolution: 480
[    20.186]     XCharSize: 8
[    20.186]     YCharSize: 16
[    20.186]     NumberOfPlanes: 1
[    20.186]     BitsPerPixel: 16
[    20.186]     NumberOfBanks: 1
[    20.186]     MemoryModel: 6
[    20.186]     BankSize: 0
[    20.186]     NumberOfImages: 11
[    20.186]     RedMaskSize: 5
[    20.186]     RedFieldPosition: 11
[    20.186]     GreenMaskSize: 6
[    20.186]     GreenFieldPosition: 5
[    20.186]     BlueMaskSize: 5
[    20.186]     BlueFieldPosition: 0
[    20.186]     RsvdMaskSize: 0
[    20.186]     RsvdFieldPosition: 0
[    20.186]     DirectColorModeInfo: 0
[    20.186]     PhysBasePtr: 0xc0000000
[    20.186]     LinBytesPerScanLine: 1280
[    20.186]     BnkNumberOfImagePages: 11
[    20.186]     LinNumberOfImagePages: 11
[    20.186]     LinRedMaskSize: 5
[    20.186]     LinRedFieldPosition: 11
[    20.186]     LinGreenMaskSize: 6
[    20.186]     LinGreenFieldPosition: 5
[    20.186]     LinBlueMaskSize: 5
[    20.186]     LinBlueFieldPosition: 0
[    20.186]     LinRsvdMaskSize: 0
[    20.186]     LinRsvdFieldPosition: 0
[    20.186]     MaxPixelClock: 0
[    20.187] Mode: 113 (800x600)
[    20.187]     ModeAttributes: 0x9b
[    20.187]     WinAAttributes: 0x7
[    20.187]     WinBAttributes: 0x0
[    20.187]     WinGranularity: 64
[    20.187]     WinSize: 64
[    20.187]     WinASegment: 0xa000
[    20.187]     WinBSegment: 0xa000
[    20.187]     WinFuncPtr: 0xc00087f9
[    20.187]     BytesPerScanline: 1600
[    20.187]     XResolution: 800
[    20.187]     YResolution: 600
[    20.187]     XCharSize: 8
[    20.187]     YCharSize: 16
[    20.187]     NumberOfPlanes: 1
[    20.187]     BitsPerPixel: 15
[    20.187]     NumberOfBanks: 1
[    20.187]     MemoryModel: 6
[    20.187]     BankSize: 0
[    20.187]     NumberOfImages: 7
[    20.187]     RedMaskSize: 5
[    20.187]     RedFieldPosition: 10
[    20.187]     GreenMaskSize: 5
[    20.187]     GreenFieldPosition: 5
[    20.187]     BlueMaskSize: 5
[    20.187]     BlueFieldPosition: 0
[    20.187]     RsvdMaskSize: 0
[    20.187]     RsvdFieldPosition: 0
[    20.187]     DirectColorModeInfo: 0
[    20.187]     PhysBasePtr: 0xc0000000
[    20.187]     LinBytesPerScanLine: 1600
[    20.187]     BnkNumberOfImagePages: 7
[    20.187]     LinNumberOfImagePages: 7
[    20.187]     LinRedMaskSize: 5
[    20.187]     LinRedFieldPosition: 10
[    20.187]     LinGreenMaskSize: 5
[    20.187]     LinGreenFieldPosition: 5
[    20.187]     LinBlueMaskSize: 5
[    20.187]     LinBlueFieldPosition: 0
[    20.187]     LinRsvdMaskSize: 0
[    20.187]     LinRsvdFieldPosition: 0
[    20.187]     MaxPixelClock: 0
[    20.187] Mode: 114 (800x600)
[    20.187]     ModeAttributes: 0x9b
[    20.187]     WinAAttributes: 0x7
[    20.187]     WinBAttributes: 0x0
[    20.187]     WinGranularity: 64
[    20.187]     WinSize: 64
[    20.187]     WinASegment: 0xa000
[    20.187]     WinBSegment: 0xa000
[    20.187]     WinFuncPtr: 0xc00087f9
[    20.187]     BytesPerScanline: 1600
[    20.187]     XResolution: 800
[    20.187]     YResolution: 600
[    20.187]     XCharSize: 8
[    20.187]     YCharSize: 16
[    20.187]     NumberOfPlanes: 1
[    20.188]     BitsPerPixel: 16
[    20.188]     NumberOfBanks: 1
[    20.188]     MemoryModel: 6
[    20.188]     BankSize: 0
[    20.188]     NumberOfImages: 7
[    20.188]     RedMaskSize: 5
[    20.188]     RedFieldPosition: 11
[    20.188]     GreenMaskSize: 6
[    20.188]     GreenFieldPosition: 5
[    20.188]     BlueMaskSize: 5
[    20.188]     BlueFieldPosition: 0
[    20.188]     RsvdMaskSize: 0
[    20.188]     RsvdFieldPosition: 0
[    20.188]     DirectColorModeInfo: 0
[    20.188]     PhysBasePtr: 0xc0000000
[    20.188]     LinBytesPerScanLine: 1600
[    20.188]     BnkNumberOfImagePages: 7
[    20.188]     LinNumberOfImagePages: 7
[    20.188]     LinRedMaskSize: 5
[    20.188]     LinRedFieldPosition: 11
[    20.188]     LinGreenMaskSize: 6
[    20.188]     LinGreenFieldPosition: 5
[    20.188]     LinBlueMaskSize: 5
[    20.188]     LinBlueFieldPosition: 0
[    20.188]     LinRsvdMaskSize: 0
[    20.188]     LinRsvdFieldPosition: 0
[    20.188]     MaxPixelClock: 0
[    20.188] Mode: 116 (1024x768)
[    20.188]     ModeAttributes: 0x9b
[    20.188]     WinAAttributes: 0x7
[    20.188]     WinBAttributes: 0x0
[    20.188]     WinGranularity: 64
[    20.188]     WinSize: 64
[    20.188]     WinASegment: 0xa000
[    20.188]     WinBSegment: 0xa000
[    20.188]     WinFuncPtr: 0xc00087f9
[    20.188]     BytesPerScanline: 2048
[    20.188]     XResolution: 1024
[    20.188]     YResolution: 768
[    20.188]     XCharSize: 8
[    20.188]     YCharSize: 16
[    20.188]     NumberOfPlanes: 1
[    20.188]     BitsPerPixel: 15
[    20.188]     NumberOfBanks: 1
[    20.188]     MemoryModel: 6
[    20.188]     BankSize: 0
[    20.188]     NumberOfImages: 4
[    20.188]     RedMaskSize: 5
[    20.188]     RedFieldPosition: 10
[    20.188]     GreenMaskSize: 5
[    20.188]     GreenFieldPosition: 5
[    20.188]     BlueMaskSize: 5
[    20.188]     BlueFieldPosition: 0
[    20.188]     RsvdMaskSize: 0
[    20.188]     RsvdFieldPosition: 0
[    20.188]     DirectColorModeInfo: 0
[    20.188]     PhysBasePtr: 0xc0000000
[    20.188]     LinBytesPerScanLine: 2048
[    20.189]     BnkNumberOfImagePages: 4
[    20.189]     LinNumberOfImagePages: 4
[    20.189]     LinRedMaskSize: 5
[    20.189]     LinRedFieldPosition: 10
[    20.189]     LinGreenMaskSize: 5
[    20.189]     LinGreenFieldPosition: 5
[    20.189]     LinBlueMaskSize: 5
[    20.189]     LinBlueFieldPosition: 0
[    20.189]     LinRsvdMaskSize: 0
[    20.189]     LinRsvdFieldPosition: 0
[    20.189]     MaxPixelClock: 0
[    20.189] Mode: 117 (1024x768)
[    20.189]     ModeAttributes: 0x9b
[    20.189]     WinAAttributes: 0x7
[    20.189]     WinBAttributes: 0x0
[    20.189]     WinGranularity: 64
[    20.189]     WinSize: 64
[    20.189]     WinASegment: 0xa000
[    20.189]     WinBSegment: 0xa000
[    20.189]     WinFuncPtr: 0xc00087f9
[    20.189]     BytesPerScanline: 2048
[    20.189]     XResolution: 1024
[    20.189]     YResolution: 768
[    20.189]     XCharSize: 8
[    20.189]     YCharSize: 16
[    20.189]     NumberOfPlanes: 1
[    20.189]     BitsPerPixel: 16
[    20.189]     NumberOfBanks: 1
[    20.189]     MemoryModel: 6
[    20.189]     BankSize: 0
[    20.189]     NumberOfImages: 4
[    20.189]     RedMaskSize: 5
[    20.189]     RedFieldPosition: 11
[    20.189]     GreenMaskSize: 6
[    20.189]     GreenFieldPosition: 5
[    20.189]     BlueMaskSize: 5
[    20.189]     BlueFieldPosition: 0
[    20.189]     RsvdMaskSize: 0
[    20.189]     RsvdFieldPosition: 0
[    20.189]     DirectColorModeInfo: 0
[    20.189]     PhysBasePtr: 0xc0000000
[    20.189]     LinBytesPerScanLine: 2048
[    20.189]     BnkNumberOfImagePages: 4
[    20.189]     LinNumberOfImagePages: 4
[    20.189]     LinRedMaskSize: 5
[    20.189]     LinRedFieldPosition: 11
[    20.189]     LinGreenMaskSize: 6
[    20.189]     LinGreenFieldPosition: 5
[    20.189]     LinBlueMaskSize: 5
[    20.189]     LinBlueFieldPosition: 0
[    20.189]     LinRsvdMaskSize: 0
[    20.189]     LinRsvdFieldPosition: 0
[    20.189]     MaxPixelClock: 0
[    20.190] Mode: 127 (320x240)
[    20.190]     ModeAttributes: 0x9f
[    20.190]     WinAAttributes: 0x7
[    20.190]     WinBAttributes: 0x0
[    20.190]     WinGranularity: 64
[    20.190]     WinSize: 64
[    20.190]     WinASegment: 0xa000
[    20.190]     WinBSegment: 0xa000
[    20.190]     WinFuncPtr: 0xc00087f9
[    20.190]     BytesPerScanline: 320
[    20.190]     XResolution: 320
[    20.190]     YResolution: 240
[    20.190]     XCharSize: 8
[    20.190]     YCharSize: 8
[    20.190]     NumberOfPlanes: 1
[    20.190]     BitsPerPixel: 8
[    20.190]     NumberOfBanks: 1
[    20.190]     MemoryModel: 4
[    20.190]     BankSize: 0
[    20.190]     NumberOfImages: 63
[    20.190]     RedMaskSize: 0
[    20.190]     RedFieldPosition: 0
[    20.190]     GreenMaskSize: 0
[    20.190]     GreenFieldPosition: 0
[    20.190]     BlueMaskSize: 0
[    20.190]     BlueFieldPosition: 0
[    20.190]     RsvdMaskSize: 0
[    20.190]     RsvdFieldPosition: 0
[    20.190]     DirectColorModeInfo: 0
[    20.190]     PhysBasePtr: 0xc0000000
[    20.190]     LinBytesPerScanLine: 320
[    20.190]     BnkNumberOfImagePages: 63
[    20.190]     LinNumberOfImagePages: 63
[    20.190]     LinRedMaskSize: 0
[    20.190]     LinRedFieldPosition: 0
[    20.190]     LinGreenMaskSize: 0
[    20.190]     LinGreenFieldPosition: 0
[    20.190]     LinBlueMaskSize: 0
[    20.190]     LinBlueFieldPosition: 0
[    20.190]     LinRsvdMaskSize: 0
[    20.190]     LinRsvdFieldPosition: 0
[    20.190]     MaxPixelClock: 0
[    20.190] Mode: 128 (400x300)
[    20.190]     ModeAttributes: 0x9f
[    20.190]     WinAAttributes: 0x7
[    20.190]     WinBAttributes: 0x0
[    20.190]     WinGranularity: 64
[    20.190]     WinSize: 64
[    20.190]     WinASegment: 0xa000
[    20.190]     WinBSegment: 0xa000
[    20.190]     WinFuncPtr: 0xc00087f9
[    20.190]     BytesPerScanline: 400
[    20.190]     XResolution: 400
[    20.190]     YResolution: 300
[    20.190]     XCharSize: 8
[    20.190]     YCharSize: 8
[    20.190]     NumberOfPlanes: 1
[    20.190]     BitsPerPixel: 8
[    20.191]     NumberOfBanks: 1
[    20.191]     MemoryModel: 4
[    20.191]     BankSize: 0
[    20.191]     NumberOfImages: 63
[    20.191]     RedMaskSize: 0
[    20.191]     RedFieldPosition: 0
[    20.191]     GreenMaskSize: 0
[    20.191]     GreenFieldPosition: 0
[    20.191]     BlueMaskSize: 0
[    20.191]     BlueFieldPosition: 0
[    20.191]     RsvdMaskSize: 0
[    20.191]     RsvdFieldPosition: 0
[    20.191]     DirectColorModeInfo: 0
[    20.191]     PhysBasePtr: 0xc0000000
[    20.191]     LinBytesPerScanLine: 400
[    20.191]     BnkNumberOfImagePages: 63
[    20.191]     LinNumberOfImagePages: 63
[    20.191]     LinRedMaskSize: 0
[    20.191]     LinRedFieldPosition: 0
[    20.191]     LinGreenMaskSize: 0
[    20.191]     LinGreenFieldPosition: 0
[    20.191]     LinBlueMaskSize: 0
[    20.191]     LinBlueFieldPosition: 0
[    20.191]     LinRsvdMaskSize: 0
[    20.191]     LinRsvdFieldPosition: 0
[    20.191]     MaxPixelClock: 0
[    20.191] Mode: 129 (512x384)
[    20.191]     ModeAttributes: 0x9f
[    20.191]     WinAAttributes: 0x7
[    20.191]     WinBAttributes: 0x0
[    20.191]     WinGranularity: 64
[    20.191]     WinSize: 64
[    20.191]     WinASegment: 0xa000
[    20.191]     WinBSegment: 0xa000
[    20.191]     WinFuncPtr: 0xc00087f9
[    20.191]     BytesPerScanline: 512
[    20.191]     XResolution: 512
[    20.191]     YResolution: 384
[    20.191]     XCharSize: 8
[    20.191]     YCharSize: 8
[    20.191]     NumberOfPlanes: 1
[    20.191]     BitsPerPixel: 8
[    20.191]     NumberOfBanks: 1
[    20.191]     MemoryModel: 4
[    20.191]     BankSize: 0
[    20.191]     NumberOfImages: 41
[    20.191]     RedMaskSize: 0
[    20.191]     RedFieldPosition: 0
[    20.191]     GreenMaskSize: 0
[    20.191]     GreenFieldPosition: 0
[    20.191]     BlueMaskSize: 0
[    20.191]     BlueFieldPosition: 0
[    20.191]     RsvdMaskSize: 0
[    20.191]     RsvdFieldPosition: 0
[    20.191]     DirectColorModeInfo: 0
[    20.191]     PhysBasePtr: 0xc0000000
[    20.191]     LinBytesPerScanLine: 512
[    20.191]     BnkNumberOfImagePages: 41
[    20.191]     LinNumberOfImagePages: 41
[    20.191]     LinRedMaskSize: 0
[    20.191]     LinRedFieldPosition: 0
[    20.191]     LinGreenMaskSize: 0
[    20.191]     LinGreenFieldPosition: 0
[    20.191]     LinBlueMaskSize: 0
[    20.191]     LinBlueFieldPosition: 0
[    20.191]     LinRsvdMaskSize: 0
[    20.191]     LinRsvdFieldPosition: 0
[    20.191]     MaxPixelClock: 0
[    20.192] Mode: 12a (320x240)
[    20.192]     ModeAttributes: 0x9b
[    20.192]     WinAAttributes: 0x7
[    20.192]     WinBAttributes: 0x0
[    20.192]     WinGranularity: 64
[    20.192]     WinSize: 64
[    20.192]     WinASegment: 0xa000
[    20.192]     WinBSegment: 0xa000
[    20.192]     WinFuncPtr: 0xc00087f9
[    20.192]     BytesPerScanline: 640
[    20.192]     XResolution: 320
[    20.192]     YResolution: 240
[    20.192]     XCharSize: 8
[    20.192]     YCharSize: 8
[    20.192]     NumberOfPlanes: 1
[    20.192]     BitsPerPixel: 16
[    20.192]     NumberOfBanks: 1
[    20.192]     MemoryModel: 6
[    20.192]     BankSize: 0
[    20.192]     NumberOfImages: 41
[    20.192]     RedMaskSize: 5
[    20.192]     RedFieldPosition: 11
[    20.192]     GreenMaskSize: 6
[    20.192]     GreenFieldPosition: 5
[    20.192]     BlueMaskSize: 5
[    20.192]     BlueFieldPosition: 0
[    20.192]     RsvdMaskSize: 0
[    20.192]     RsvdFieldPosition: 0
[    20.192]     DirectColorModeInfo: 0
[    20.192]     PhysBasePtr: 0xc0000000
[    20.192]     LinBytesPerScanLine: 640
[    20.192]     BnkNumberOfImagePages: 41
[    20.192]     LinNumberOfImagePages: 41
[    20.192]     LinRedMaskSize: 5
[    20.192]     LinRedFieldPosition: 11
[    20.192]     LinGreenMaskSize: 6
[    20.192]     LinGreenFieldPosition: 5
[    20.192]     LinBlueMaskSize: 5
[    20.192]     LinBlueFieldPosition: 0
[    20.192]     LinRsvdMaskSize: 0
[    20.192]     LinRsvdFieldPosition: 0
[    20.192]     MaxPixelClock: 0
[    20.193] Mode: 12b (400x300)
[    20.193]     ModeAttributes: 0x9b
[    20.193]     WinAAttributes: 0x7
[    20.193]     WinBAttributes: 0x0
[    20.193]     WinGranularity: 64
[    20.193]     WinSize: 64
[    20.193]     WinASegment: 0xa000
[    20.193]     WinBSegment: 0xa000
[    20.193]     WinFuncPtr: 0xc00087f9
[    20.193]     BytesPerScanline: 800
[    20.193]     XResolution: 400
[    20.193]     YResolution: 300
[    20.193]     XCharSize: 8
[    20.193]     YCharSize: 8
[    20.193]     NumberOfPlanes: 1
[    20.193]     BitsPerPixel: 16
[    20.193]     NumberOfBanks: 1
[    20.193]     MemoryModel: 6
[    20.193]     BankSize: 0
[    20.193]     NumberOfImages: 31
[    20.193]     RedMaskSize: 5
[    20.193]     RedFieldPosition: 11
[    20.193]     GreenMaskSize: 6
[    20.193]     GreenFieldPosition: 5
[    20.193]     BlueMaskSize: 5
[    20.193]     BlueFieldPosition: 0
[    20.193]     RsvdMaskSize: 0
[    20.193]     RsvdFieldPosition: 0
[    20.193]     DirectColorModeInfo: 0
[    20.193]     PhysBasePtr: 0xc0000000
[    20.193]     LinBytesPerScanLine: 800
[    20.193]     BnkNumberOfImagePages: 31
[    20.193]     LinNumberOfImagePages: 31
[    20.193]     LinRedMaskSize: 5
[    20.193]     LinRedFieldPosition: 11
[    20.193]     LinGreenMaskSize: 6
[    20.193]     LinGreenFieldPosition: 5
[    20.193]     LinBlueMaskSize: 5
[    20.193]     LinBlueFieldPosition: 0
[    20.193]     LinRsvdMaskSize: 0
[    20.193]     LinRsvdFieldPosition: 0
[    20.193]     MaxPixelClock: 0
[    20.193] Mode: 12c (512x384)
[    20.193]     ModeAttributes: 0x9b
[    20.193]     WinAAttributes: 0x7
[    20.193]     WinBAttributes: 0x0
[    20.193]     WinGranularity: 64
[    20.193]     WinSize: 64
[    20.193]     WinASegment: 0xa000
[    20.193]     WinBSegment: 0xa000
[    20.193]     WinFuncPtr: 0xc00087f9
[    20.193]     BytesPerScanline: 1024
[    20.193]     XResolution: 512
[    20.193]     YResolution: 384
[    20.193]     XCharSize: 8
[    20.193]     YCharSize: 8
[    20.193]     NumberOfPlanes: 1
[    20.193]     BitsPerPixel: 16
[    20.193]     NumberOfBanks: 1
[    20.193]     MemoryModel: 6
[    20.193]     BankSize: 0
[    20.193]     NumberOfImages: 20
[    20.193]     RedMaskSize: 5
[    20.193]     RedFieldPosition: 11
[    20.193]     GreenMaskSize: 6
[    20.194]     GreenFieldPosition: 5
[    20.194]     BlueMaskSize: 5
[    20.194]     BlueFieldPosition: 0
[    20.194]     RsvdMaskSize: 0
[    20.194]     RsvdFieldPosition: 0
[    20.194]     DirectColorModeInfo: 0
[    20.194]     PhysBasePtr: 0xc0000000
[    20.194]     LinBytesPerScanLine: 1024
[    20.194]     BnkNumberOfImagePages: 20
[    20.194]     LinNumberOfImagePages: 20
[    20.194]     LinRedMaskSize: 5
[    20.194]     LinRedFieldPosition: 11
[    20.194]     LinGreenMaskSize: 6
[    20.194]     LinGreenFieldPosition: 5
[    20.194]     LinBlueMaskSize: 5
[    20.194]     LinBlueFieldPosition: 0
[    20.194]     LinRsvdMaskSize: 0
[    20.194]     LinRsvdFieldPosition: 0
[    20.194]     MaxPixelClock: 0
[    20.194] Mode: 12d (320x200)
[    20.194]     ModeAttributes: 0x9f
[    20.194]     WinAAttributes: 0x7
[    20.194]     WinBAttributes: 0x0
[    20.194]     WinGranularity: 64
[    20.194]     WinSize: 64
[    20.194]     WinASegment: 0xa000
[    20.194]     WinBSegment: 0xa000
[    20.194]     WinFuncPtr: 0xc00087f9
[    20.194]     BytesPerScanline: 320
[    20.194]     XResolution: 320
[    20.194]     YResolution: 200
[    20.194]     XCharSize: 8
[    20.194]     YCharSize: 8
[    20.194]     NumberOfPlanes: 1
[    20.194]     BitsPerPixel: 8
[    20.194]     NumberOfBanks: 1
[    20.194]     MemoryModel: 4
[    20.194]     BankSize: 0
[    20.194]     NumberOfImages: 127
[    20.194]     RedMaskSize: 0
[    20.194]     RedFieldPosition: 0
[    20.194]     GreenMaskSize: 0
[    20.194]     GreenFieldPosition: 0
[    20.194]     BlueMaskSize: 0
[    20.194]     BlueFieldPosition: 0
[    20.194]     RsvdMaskSize: 0
[    20.194]     RsvdFieldPosition: 0
[    20.194]     DirectColorModeInfo: 0
[    20.194]     PhysBasePtr: 0xc0000000
[    20.194]     LinBytesPerScanLine: 320
[    20.194]     BnkNumberOfImagePages: 127
[    20.194]     LinNumberOfImagePages: 127
[    20.194]     LinRedMaskSize: 0
[    20.194]     LinRedFieldPosition: 0
[    20.194]     LinGreenMaskSize: 0
[    20.194]     LinGreenFieldPosition: 0
[    20.194]     LinBlueMaskSize: 0
[    20.194]     LinBlueFieldPosition: 0
[    20.194]     LinRsvdMaskSize: 0
[    20.194]     LinRsvdFieldPosition: 0
[    20.194]     MaxPixelClock: 0
[    20.195] Mode: 131 (640x400)
[    20.195]     ModeAttributes: 0x9b
[    20.195]     WinAAttributes: 0x7
[    20.195]     WinBAttributes: 0x0
[    20.195]     WinGranularity: 64
[    20.195]     WinSize: 64
[    20.195]     WinASegment: 0xa000
[    20.195]     WinBSegment: 0xa000
[    20.195]     WinFuncPtr: 0xc00087f9
[    20.195]     BytesPerScanline: 1280
[    20.195]     XResolution: 640
[    20.195]     YResolution: 400
[    20.195]     XCharSize: 8
[    20.195]     YCharSize: 16
[    20.195]     NumberOfPlanes: 1
[    20.195]     BitsPerPixel: 16
[    20.195]     NumberOfBanks: 1
[    20.195]     MemoryModel: 6
[    20.195]     BankSize: 0
[    20.195]     NumberOfImages: 15
[    20.195]     RedMaskSize: 5
[    20.195]     RedFieldPosition: 11
[    20.195]     GreenMaskSize: 6
[    20.195]     GreenFieldPosition: 5
[    20.195]     BlueMaskSize: 5
[    20.195]     BlueFieldPosition: 0
[    20.195]     RsvdMaskSize: 0
[    20.195]     RsvdFieldPosition: 0
[    20.195]     DirectColorModeInfo: 0
[    20.195]     PhysBasePtr: 0xc0000000
[    20.195]     LinBytesPerScanLine: 1280
[    20.195]     BnkNumberOfImagePages: 15
[    20.195]     LinNumberOfImagePages: 15
[    20.195]     LinRedMaskSize: 5
[    20.195]     LinRedFieldPosition: 11
[    20.195]     LinGreenMaskSize: 6
[    20.195]     LinGreenFieldPosition: 5
[    20.195]     LinBlueMaskSize: 5
[    20.195]     LinBlueFieldPosition: 0
[    20.195]     LinRsvdMaskSize: 0
[    20.195]     LinRsvdFieldPosition: 0
[    20.195]     MaxPixelClock: 0
[    20.196] *Mode: 112 (640x480)
[    20.196]     ModeAttributes: 0x9b
[    20.196]     WinAAttributes: 0x7
[    20.196]     WinBAttributes: 0x0
[    20.196]     WinGranularity: 64
[    20.196]     WinSize: 64
[    20.196]     WinASegment: 0xa000
[    20.196]     WinBSegment: 0xa000
[    20.196]     WinFuncPtr: 0xc00087f9
[    20.196]     BytesPerScanline: 2560
[    20.196]     XResolution: 640
[    20.196]     YResolution: 480
[    20.196]     XCharSize: 8
[    20.196]     YCharSize: 16
[    20.196]     NumberOfPlanes: 1
[    20.196]     BitsPerPixel: 32
[    20.196]     NumberOfBanks: 1
[    20.196]     MemoryModel: 6
[    20.196]     BankSize: 0
[    20.196]     NumberOfImages: 5
[    20.196]     RedMaskSize: 8
[    20.196]     RedFieldPosition: 16
[    20.196]     GreenMaskSize: 8
[    20.196]     GreenFieldPosition: 8
[    20.196]     BlueMaskSize: 8
[    20.196]     BlueFieldPosition: 0
[    20.196]     RsvdMaskSize: 8
[    20.196]     RsvdFieldPosition: 24
[    20.196]     DirectColorModeInfo: 0
[    20.196]     PhysBasePtr: 0xc0000000
[    20.196]     LinBytesPerScanLine: 2560
[    20.196]     BnkNumberOfImagePages: 5
[    20.196]     LinNumberOfImagePages: 5
[    20.196]     LinRedMaskSize: 8
[    20.196]     LinRedFieldPosition: 16
[    20.196]     LinGreenMaskSize: 8
[    20.196]     LinGreenFieldPosition: 8
[    20.196]     LinBlueMaskSize: 8
[    20.196]     LinBlueFieldPosition: 0
[    20.196]     LinRsvdMaskSize: 8
[    20.196]     LinRsvdFieldPosition: 24
[    20.196]     MaxPixelClock: 0
[    20.197] *Mode: 115 (800x600)
[    20.197]     ModeAttributes: 0x9b
[    20.197]     WinAAttributes: 0x7
[    20.197]     WinBAttributes: 0x0
[    20.197]     WinGranularity: 64
[    20.197]     WinSize: 64
[    20.197]     WinASegment: 0xa000
[    20.197]     WinBSegment: 0xa000
[    20.197]     WinFuncPtr: 0xc00087f9
[    20.197]     BytesPerScanline: 3200
[    20.197]     XResolution: 800
[    20.197]     YResolution: 600
[    20.197]     XCharSize: 8
[    20.197]     YCharSize: 16
[    20.197]     NumberOfPlanes: 1
[    20.197]     BitsPerPixel: 32
[    20.197]     NumberOfBanks: 1
[    20.197]     MemoryModel: 6
[    20.197]     BankSize: 0
[    20.197]     NumberOfImages: 3
[    20.197]     RedMaskSize: 8
[    20.197]     RedFieldPosition: 16
[    20.197]     GreenMaskSize: 8
[    20.197]     GreenFieldPosition: 8
[    20.197]     BlueMaskSize: 8
[    20.197]     BlueFieldPosition: 0
[    20.197]     RsvdMaskSize: 8
[    20.197]     RsvdFieldPosition: 24
[    20.197]     DirectColorModeInfo: 0
[    20.197]     PhysBasePtr: 0xc0000000
[    20.197]     LinBytesPerScanLine: 3200
[    20.197]     BnkNumberOfImagePages: 3
[    20.197]     LinNumberOfImagePages: 3
[    20.197]     LinRedMaskSize: 8
[    20.197]     LinRedFieldPosition: 16
[    20.197]     LinGreenMaskSize: 8
[    20.197]     LinGreenFieldPosition: 8
[    20.197]     LinBlueMaskSize: 8
[    20.197]     LinBlueFieldPosition: 0
[    20.197]     LinRsvdMaskSize: 8
[    20.197]     LinRsvdFieldPosition: 24
[    20.197]     MaxPixelClock: 0
[    20.197] *Mode: 118 (1024x768)
[    20.198]     ModeAttributes: 0x9b
[    20.198]     WinAAttributes: 0x7
[    20.198]     WinBAttributes: 0x0
[    20.198]     WinGranularity: 64
[    20.198]     WinSize: 64
[    20.198]     WinASegment: 0xa000
[    20.198]     WinBSegment: 0xa000
[    20.198]     WinFuncPtr: 0xc00087f9
[    20.198]     BytesPerScanline: 4096
[    20.198]     XResolution: 1024
[    20.198]     YResolution: 768
[    20.198]     XCharSize: 8
[    20.198]     YCharSize: 16
[    20.198]     NumberOfPlanes: 1
[    20.198]     BitsPerPixel: 32
[    20.198]     NumberOfBanks: 1
[    20.198]     MemoryModel: 6
[    20.198]     BankSize: 0
[    20.198]     NumberOfImages: 1
[    20.198]     RedMaskSize: 8
[    20.198]     RedFieldPosition: 16
[    20.198]     GreenMaskSize: 8
[    20.198]     GreenFieldPosition: 8
[    20.198]     BlueMaskSize: 8
[    20.198]     BlueFieldPosition: 0
[    20.198]     RsvdMaskSize: 8
[    20.198]     RsvdFieldPosition: 24
[    20.198]     DirectColorModeInfo: 0
[    20.198]     PhysBasePtr: 0xc0000000
[    20.198]     LinBytesPerScanLine: 4096
[    20.198]     BnkNumberOfImagePages: 1
[    20.198]     LinNumberOfImagePages: 1
[    20.198]     LinRedMaskSize: 8
[    20.198]     LinRedFieldPosition: 16
[    20.198]     LinGreenMaskSize: 8
[    20.198]     LinGreenFieldPosition: 8
[    20.198]     LinBlueMaskSize: 8
[    20.198]     LinBlueFieldPosition: 0
[    20.198]     LinRsvdMaskSize: 8
[    20.198]     LinRsvdFieldPosition: 24
[    20.198]     MaxPixelClock: 0
[    20.198] Mode: 102 (800x600)
[    20.198]     ModeAttributes: 0x1f
[    20.198]     WinAAttributes: 0x7
[    20.198]     WinBAttributes: 0x0
[    20.198]     WinGranularity: 64
[    20.198]     WinSize: 64
[    20.198]     WinASegment: 0xa000
[    20.198]     WinBSegment: 0xa000
[    20.198]     WinFuncPtr: 0xc00087f9
[    20.198]     BytesPerScanline: 100
[    20.198]     XResolution: 800
[    20.198]     YResolution: 600
[    20.198]     XCharSize: 8
[    20.198]     YCharSize: 16
[    20.198]     NumberOfPlanes: 4
[    20.198]     BitsPerPixel: 4
[    20.198]     NumberOfBanks: 1
[    20.198]     MemoryModel: 3
[    20.198]     BankSize: 0
[    20.198]     NumberOfImages: 31
[    20.198]     RedMaskSize: 0
[    20.198]     RedFieldPosition: 0
[    20.198]     GreenMaskSize: 0
[    20.198]     GreenFieldPosition: 0
[    20.198]     BlueMaskSize: 0
[    20.198]     BlueFieldPosition: 0
[    20.198]     RsvdMaskSize: 0
[    20.198]     RsvdFieldPosition: 0
[    20.198]     DirectColorModeInfo: 0
[    20.198]     PhysBasePtr: 0xc0000000
[    20.198]     LinBytesPerScanLine: 100
[    20.199]     BnkNumberOfImagePages: 31
[    20.199]     LinNumberOfImagePages: 31
[    20.199]     LinRedMaskSize: 0
[    20.199]     LinRedFieldPosition: 0
[    20.199]     LinGreenMaskSize: 0
[    20.199]     LinGreenFieldPosition: 0
[    20.199]     LinBlueMaskSize: 0
[    20.199]     LinBlueFieldPosition: 0
[    20.199]     LinRsvdMaskSize: 0
[    20.199]     LinRsvdFieldPosition: 0
[    20.199]     MaxPixelClock: 0
[    20.199] 
[    20.199] (II) VESA(0): Total Memory: 2048 64KB banks (131072kB)
[    20.199] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    20.199] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    20.199] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    20.199] (WW) VESA(0): Unable to estimate virtual size
[    20.199] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    20.199] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    20.199] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    20.199] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    20.199] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    20.199] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    20.199] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    20.199] (WW) VESA(0): Unable to estimate virtual size
[    20.208] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    20.208] (**) VESA(0): *Built-in mode "1024x768"
[    20.208] (**) VESA(0): *Built-in mode "800x600"
[    20.208] (**) VESA(0): *Built-in mode "640x480"
[    20.208] (==) VESA(0): DPI set to (96, 96)
[    20.208] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    20.208] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    20.208] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    20.208] (**) VESA(0): Using "Shadow Framebuffer"
[    20.208] (II) Loading sub module "shadow"
[    20.208] (II) LoadModule: "shadow"
[    20.209] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    20.226] (II) Module shadow: vendor="X.Org Foundation"
[    20.227]     compiled for 1.13.3, module version = 1.1.0
[    20.227]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.227] (II) Loading sub module "fb"
[    20.227] (II) LoadModule: "fb"
[    20.227] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.242] (II) Module fb: vendor="X.Org Foundation"
[    20.242]     compiled for 1.13.3, module version = 1.0.0
[    20.242]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.242] (II) UnloadModule: "sis"
[    20.242] (II) Unloading sis
[    20.243] (II) UnloadModule: "modesetting"
[    20.243] (II) Unloading modesetting
[    20.243] (II) UnloadModule: "fbdev"
[    20.243] (II) Unloading fbdev
[    20.243] (II) UnloadSubModule: "fbdevhw"
[    20.243] (II) Unloading fbdevhw
[    20.243] (==) Depth 24 pixmap format is 32 bpp
[    20.243] (II) Loading sub module "int10"
[    20.243] (II) LoadModule: "int10"
[    20.243] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.243] (II) Module int10: vendor="X.Org Foundation"
[    20.243]     compiled for 1.13.3, module version = 1.0.0
[    20.243]     ABI class: X.Org Video Driver, version 13.1
[    20.243] (II) VESA(0): initializing int10
[    20.248] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    20.249] (II) VESA(0): VESA BIOS detected
[    20.249] (II) VESA(0): VESA VBE Version 3.0
[    20.249] (II) VESA(0): VESA VBE Total Mem: 131072 kB
[    20.249] (II) VESA(0): VESA VBE OEM: SiS
[    20.249] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    20.249] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    20.249] (II) VESA(0): VESA VBE OEM Product: 6330
[    20.249] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.24a
[    20.253] (II) VESA(0): virtual address = 0x7f31b2134000,
    physical address = 0xc0000000, size = 134217728
[    20.268] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    20.466] (==) VESA(0): Default visual is TrueColor
[    20.471] (==) VESA(0): Backing store disabled
[    20.472] (==) VESA(0): DPMS enabled
[    20.472] (==) RandR enabled
[    20.479] (II) AIGLX: Screen 0 is not DRI2 capable
[    20.479] (II) AIGLX: Screen 0 is not DRI capable
[    21.278] (II) AIGLX: Loaded and initialized swrast
[    21.278] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    21.390] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.401] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.401] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.401] (II) LoadModule: "evdev"
[    21.401] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.421] (II) Module evdev: vendor="X.Org Foundation"
[    21.421]     compiled for 1.13.3, module version = 2.7.3
[    21.421]     Module class: X.Org XInput Driver
[    21.421]     ABI class: X.Org XInput driver, version 18.0
[    21.421] (II) Using input driver 'evdev' for 'Power Button'
[    21.421] (**) Power Button: always reports core events
[    21.421] (**) evdev: Power Button: Device: "/dev/input/event3"
[    21.421] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.421] (--) evdev: Power Button: Found keys
[    21.421] (II) evdev: Power Button: Configuring as keyboard
[    21.421] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    21.421] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.421] (**) Option "xkb_rules" "evdev"
[    21.421] (**) Option "xkb_model" "pc105"
[    21.421] (**) Option "xkb_layout" "br"
[    21.426] (II) XKB: reuse xkmfile /var/lib/xkb/server-A37B2EFB8B2398771EA3BE2A51A1034B516E3F38.xkm
[    21.432] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    21.432] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.432] (II) Using input driver 'evdev' for 'Video Bus'
[    21.432] (**) Video Bus: always reports core events
[    21.432] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    21.432] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.433] (--) evdev: Video Bus: Found keys
[    21.433] (II) evdev: Video Bus: Configuring as keyboard
[    21.433] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0b/LNXVIDEO:00/input/input5/event5"
[    21.433] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.433] (**) Option "xkb_rules" "evdev"
[    21.433] (**) Option "xkb_model" "pc105"
[    21.433] (**) Option "xkb_layout" "br"
[    21.433] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.433] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.433] (II) Using input driver 'evdev' for 'Power Button'
[    21.433] (**) Power Button: always reports core events
[    21.433] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.433] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.433] (--) evdev: Power Button: Found keys
[    21.433] (II) evdev: Power Button: Configuring as keyboard
[    21.433] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    21.433] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    21.433] (**) Option "xkb_rules" "evdev"
[    21.433] (**) Option "xkb_model" "pc105"
[    21.433] (**) Option "xkb_layout" "br"
[    21.434] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    21.434] (II) No input driver specified, ignoring this device.
[    21.434] (II) This device may have been added with another device file.
[    21.434] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    21.434] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.434] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.435] (**) Sleep Button: always reports core events
[    21.435] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    21.435] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    21.435] (--) evdev: Sleep Button: Found keys
[    21.435] (II) evdev: Sleep Button: Configuring as keyboard
[    21.435] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    21.435] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    21.435] (**) Option "xkb_rules" "evdev"
[    21.435] (**) Option "xkb_model" "pc105"
[    21.435] (**) Option "xkb_layout" "br"
[    21.435] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event7)
[    21.435] (II) No input driver specified, ignoring this device.
[    21.435] (II) This device may have been added with another device file.
[    21.436] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event8)
[    21.436] (II) No input driver specified, ignoring this device.
[    21.436] (II) This device may have been added with another device file.
[    21.436] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    21.436] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.436] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.436] (**) AT Translated Set 2 keyboard: always reports core events
[    21.436] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    21.436] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.436] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.436] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.436] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    21.436] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    21.436] (**) Option "xkb_rules" "evdev"
[    21.436] (**) Option "xkb_model" "pc105"
[    21.436] (**) Option "xkb_layout" "br"
[    21.437] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    21.437] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.437] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.437] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    21.437] (II) LoadModule: "synaptics"
[    21.437] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.454] (II) Module synaptics: vendor="X.Org Foundation"
[    21.454]     compiled for 1.13.3, module version = 1.6.2
[    21.454]     Module class: X.Org XInput Driver
[    21.454]     ABI class: X.Org XInput driver, version 18.0
[    21.454] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    21.454] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.454] (**) Option "Device" "/dev/input/event6"
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.455] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.455] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    21.455] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    21.455] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.455] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    21.455] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    21.455] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.455] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.455] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.455] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.455] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.456] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    21.456] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    37.951] (II) XKB: reuse xkmfile /var/lib/xkb/server-E02741913840E34805965F50669C02EA49967696.xkm
```

---

### Post by Bucky Ball on 2014-02-20
Please use [code] tags for terminal output. Neater, smaller, and easier to read. I have added them to your last post.

---

