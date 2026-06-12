---
title: "[AMD/ATI] Sun PRO [Radeon HD 8570A/8570M] Ubuntu 14.04 non-functional"
date: 2014-04-28
forum: Hardware
---

### Post by huntredgo on 2014-04-28
Hey all, 

I've recently been a little stumped with my graphics setup. I have a hybrid system (AMD), yet I suspect my discrete graphics card isn't being utilized. Here is a little more info: 

Hardware: 
Lenovo Thinkpad e545
Processor: AMD A8-5550M APU with Radeon(tm) HD Graphics × 4 
Graphics: AMD Radeon HD 8550G
Discrete Graphics: AMD Radeon HD 8570M 2GB Discrete Graphics

```
~$ glxinfo | grep 'OpenGL renderer string'
OpenGL renderer string: AMD Radeon HD 8550G
```

This seems to signify it would only be using the one, right? 

UPDATED: Found some interesting info in the xorg.log... 

```
...
[    18.714] (WW)** fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found**
[    18.714] (--) Chipset Supported AMD Graphics Processor (0x990D) found
[    18.715] (WW)** fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found**
[    18.715] (**) ChipID override: 0x6663
[    18.715] (**) Chipset Supported AMD Graphics Processor (0x6663) found
[    18.717] (II) fglrx(0): pEnt->device->identifier=0x7ffbfc5b3e70
[    18.717] (II) pEnt->device->identifier=(nil)
[    18.718] (WW) Falling back to old probe method for modesetting
[    18.718] (EE) open /dev/dri/card0: No such file or directory
[    18.718] (WW) Falling back to old probe method for fbdev
[    18.718] (II) Loading sub module "fbdevhw"
[    18.718] (II) LoadModule: "fbdevhw"
[    18.719] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.719] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.719]    compiled for 1.15.1, module version = 0.0.2
[    18.719]    ABI class: X.Org Video Driver, version 15.0
[    18.719] **(WW) Falling back to old probe method for vesa**
[    18.719] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    18.720] (II) Loading sub module "vgahw"
[    18.720] (II) LoadModule: "vgahw"
[    18.755] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    18.755] (II) Module vgahw: vendor="X.Org Foundation"
[    18.755]    compiled for 1.15.1, module version = 0.1.0
    ABI class: X.Org Video Driver, version 15.0
[    18.757] (II) fglrx(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    18.757] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    18.757] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.757] (==) fglrx(0): Default visual is TrueColor
[    18.757] (==) fglrx(0): RGB weight 888
[    18.757] (II) fglrx(0): Using 8 bits per RGB
[    18.757] (==) fglrx(0): Buffer Tiling is ON
[    18.757] (II) Loading sub module "fglrxdrm"
[    18.757] (II) LoadModule: "fglrxdrm"
[    18.758] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.758] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    18.758]    compiled for 1.4.99.906, module version = 13.35.5
```

Could it be an issue with the driver itself and support for my hardware? I think it might be falling back to vesa...


```
~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
**00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8550G]**
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
**01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun PRO [Radeon HD 8570A/8570M]**
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

Current fglrx packages: 
```
||/ Name                      Version           Architecture      Description
+++-=========================-=================-=================-========================================================
rc  fglrx                     2:13.350.1-0ubunt amd64             Video driver for the AMD graphics accelerators
un  fglrx-amdcccle            <none>            <none>            (no description available)
ii  fglrx-amdcccle-updates    2:13.350.1-0ubunt amd64             Catalyst Control Center for the AMD graphics accelerator
un  fglrx-control             <none>            <none>            (no description available)
un  fglrx-control-qt2         <none>            <none>            (no description available)
un  fglrx-driver              <none>            <none>            (no description available)
un  fglrx-glx                 <none>            <none>            (no description available)
ii  fglrx-pxpress             1:0.2.91.4        amd64             transitional package for ubuntu-drivers-common
ii  fglrx-updates             2:13.350.1-0ubunt amd64             Video driver for the AMD graphics accelerators
```

hardinfo report: 

```
Devices
*******


Processor
---------

-Processors-
AMD A8-5550M APU with Radeon(tm) HD Graphics        : 1400.00MHz
AMD A8-5550M APU with Radeon(tm) HD Graphics        : 1400.00MHz
AMD A8-5550M APU with Radeon(tm) HD Graphics        : 2100.00MHz
AMD A8-5550M APU with Radeon(tm) HD Graphics        : 2100.00MHz

PCI Devices
-----------

-PCI Devices-
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
**VGA compatible controller        : Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8550G] (prog-if 00 [VGA controller])**
Audio device        : Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
SATA controller        : Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
SMBus        : Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
Audio device        : Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
ISA bridge        : Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
PCI bridge        : Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
**Display controller        : Advanced Micro Devices, Inc. [AMD/ATI] Sun PRO [Radeon HD 8570A/8570M]**
Ethernet controller        : Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
Network controller        : Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
```

amdcccle details:
[ATTACH=CONFIG]252620[/ATTACH]

Hopefully I gave you guys enough info :/ If there's something else I can throw up here, please let me know!

I tried as well to install the proprietary drivers from the AMD Website, but they wouldn't play nicely with Unity (nothing loaded after login, only background and mouse). 

Thank you so much!

---

### Post by ganda on 2014-05-31
you might want to check my last post in:
[http://ubuntuforums.org/showthread.php?t=2216720]("http://ubuntuforums.org/showthread.php?t=2216720")

---

