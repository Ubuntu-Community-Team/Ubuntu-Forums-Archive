---
title: "fglrx issues"
date: 2010-11-14
forum: Hardware
---

### Post by Antithesis on 2010-11-14
I'm unable to have a working fglrx setup on my machine.

I have:
-Powercolor Radeon HD 4650
-Ubuntu Lucid
-2.6.31-14-generic x86_64
-Gigabyte P55-UD4P Motherboard


Installing:
ati-driver-installer-10-10-x86.x86_64.run

After previous failed attempts, I followed
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)


(I First did a full uninstall, then manual install).


Current state:

Warnings/Errors in Xorg.log
```

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.7.1, module version = 8.78.6
(II) ATI Proprietary Linux Driver Version Identifier:8.78.6
(II) ATI Proprietary Linux Driver Release Identifier: 8.783                                
(II) ATI Proprietary Linux Driver Build Date: Oct  5 2010 21:22:54
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9498) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x1e362f0
(WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
(II) fglrx(0): === [xdl_x750_atiddxPreInit] === begin
.....
.....
.....
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: failed to open /proc/ati/major
ukiDynamicMajor: failed to open /proc/ati/major
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): ATI 2D Acceleration Architecture enabled
(--) fglrx(0): Chipset: "ATI Radeon HD 4600 Series  " (Chipset = 0x9498)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2269)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfb9e0000
(--) fglrx(0): I/O port at 0x0000ae00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(EE) fglrx(0): ACPI: DRM connection failed
.....
.....
.....
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): ACPI: DRM connection failed
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
.....
.....
.....
(II) fglrx(0): DPI set to (68, 65)
(II) fglrx(0): Adapter ATI Radeon HD 4600 Series   has 2 configurable heads and 2 displays connected.
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************************
(WW) fglrx(0): * DRI initialization failed                               *
(WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
(WW) fglrx(0): * 2D and 3D acceleration disabled                         *
(WW) fglrx(0): ***********************************************************

```

fglrxinfo
```

$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18

```

When trying the intel agp fix suggested in the wiki, I realized that also:
```

$ modprobe fglrx
FATAL: Module fglrx not found.

```

Any help would be appreciated,
Thanks!

---

### Post by mpnordland on 2010-11-14
try using the Hardware Drivers utility in Lucid it is located in
System>Administration>Hardware Drivers
It will scan your system for hardware that has proprietary drivers available and install them if you like.

---

### Post by Yellow Pasque on 2010-11-14
You're using the old Karmic kernel (2.6.31). Don't do that...

---

### Post by Antithesis on 2010-11-14
> **Temüjin said:**
> You're using the old Karmic kernel (2.6.31). Don't do that...

Thanks.

I gave in and upgraded to maverick.


After I did, the problem persisted and I noticed my kernel stayed as it was and didn't move to 2.6.35.22 (a separate issue, even after new upgrade grub-mkconfig was only keeping old kernel).
I fixed that (manually for now, enough linux fiddeling today) and fglrx works great.

---

