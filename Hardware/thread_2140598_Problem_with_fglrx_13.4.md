---
title: "Problem with fglrx 13.4"
date: 2013-04-30
forum: Hardware
---

### Post by staim on 2013-04-30
X is not starting after manual update to fglrx 13.4

Xorg.0.log
```

[     4.903] (II) LoadModule: "fglrx"
[     4.903] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[     4.942] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     4.942] 	compiled for 1.4.99.906, module version = 12.10.5
[     4.942] 	Module class: X.Org Video Driver
[     4.943] (II) Loading sub module "fglrxdrm"
[     4.943] (II) LoadModule: "fglrxdrm"
[     4.943] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     4.947] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     4.947] 	compiled for 1.4.99.906, module version = 12.10.5
[     4.947] (II) AMD Proprietary Linux Driver Version Identifier:12.10.05
[     4.947] (II) AMD Proprietary Linux Driver Release Identifier: 12.104                               
[     4.947] (II) AMD Proprietary Linux Driver Build Date: Mar 28 2013 21:07:25
[     4.947] (++) using VT number 7


[     4.947] (WW) Falling back to old probe method for fglrx
[     4.955] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     4.958] ukiDynamicMajor: failed to open /proc/ati/major
[     4.958] ukiDynamicMajor: failed to open /proc/ati/major
[     4.960] (--) Chipset Supported AMD Graphics Processor (0x6840) found
[     4.961] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     4.961] (II) AMD Video driver is signed
[     4.961] (II) fglrx(0): pEnt->device->identifier=0x7f9d876b4f40
[     4.962] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[     4.962] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     4.962] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     4.962] (==) fglrx(0): Default visual is TrueColor
[     4.962] (**) fglrx(0): Option "DPMS" "true"
[     4.962] (==) fglrx(0): RGB weight 888
[     4.962] (II) fglrx(0): Using 8 bits per RGB 
[     4.962] (==) fglrx(0): Buffer Tiling is ON
[     4.963] (II) Loading sub module "fglrxdrm"
[     4.963] (II) LoadModule: "fglrxdrm"
[     4.963] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     4.963] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     4.963] 	compiled for 1.4.99.906, module version = 12.10.5
[     4.964] ukiDynamicMajor: failed to open /proc/ati/major
[     4.964] ukiDynamicMajor: failed to open /proc/ati/major
[     4.964] (**) fglrx(0): NoAccel = NO
[     4.964] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     4.964] (--) fglrx(0): Chipset: "AMD Radeon HD 7600M Series" (Chipset = 0x6840)
[     4.964] (--) fglrx(0): (PciSubVendor = 0x144d, PciSubDevice = 0xc0d8)
[     4.964] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     4.964] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     4.964] (--) fglrx(0): MMIO registers at 0xc0120000
[     4.964] (--) fglrx(0): I/O port at 0x00003000
[     4.964] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     4.968] (II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
[     4.968] (EE) fglrx(0): Invalid video BIOS signature!
[     4.968] (EE) fglrx(0): GetBIOSParameter failed
[     4.968] (EE) fglrx(0): PreInitAdapter failed
[     4.968] (EE) fglrx(0): PreInit failed
[     4.968] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === end
[     4.969] (II) UnloadModule: "fglrx"

```

Some problem with ATI BIOS? Why 13.1 worked ok?

lspci
```

staim@Kassiopeia:~$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series] (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device c0d8
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0120000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0100000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx_experimental_12, radeon

```


I'm confused with [color=red]Subsystem: Samsung Electronics Co Ltd Device c0d8[/color], why it is not AMD, but Samsung (I have Samsung laptop, but video mus be AMD), maybe some problem with bios, customized  by Samsung?


> 
root@Kassiopeia:~# uname -a
Linux Kassiopeia 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



Ubuntu 12.04.2 LTS 64 bit
Intel® Core™ i3-2370M CPU @ 2.40GHz × 4 
AMD Radeon HD 7600M Series 


13.1 works perfectly.


Please help to make them work ...

---

