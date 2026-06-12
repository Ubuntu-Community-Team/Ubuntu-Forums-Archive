---
title: "Second graphics not working"
date: 2012-04-06
forum: Hardware
---

### Post by Freek07 on 2012-04-06
As I can see on google, this bug has been around for a long time: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919) but as I can see the thing is still not working in 11.10 with all updates.

the problem is, with two graphics cards, Xorg cannot read V_BIOS of second card. Even if I try using **only** the secondary card in config it's the same.

LOG says (example for VESA):
[  1227.384] (II) VESA(0): initializing int10
[  1227.384] (EE) VESA(0): Cannot read V_BIOS (3) Input/output error
[  1227.384] (II) UnloadModule: "vesa"
[  1227.384] (II) Unloading vesa
[  1227.384] (II) UnloadModule: "int10"
[  1227.384] (II) Unloading int10
[  1227.384] (II) UnloadModule: "vbe"
[  1227.384] (II) Unloading vbe
[  1227.384] (EE) Screen(s) found, but none have a usable configuration.


Mach64 isn't so exact but same thing happens:
[  1213.226] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[  1213.226] (**) MACH64(0): Depth 24, (--) framebuffer bpp 32
[  1213.226] (==) MACH64(0): Using XAA acceleration architecture
[  1213.226] (WW) MACH64: Mach64 in slot 5:0:0 could not be detected!
[  1213.226] (II) UnloadModule: "mach64"
[  1213.226] (II) Unloading mach64
[  1213.226] (EE) Screen(s) found, but none have a usable configuration.


lspci:
may@Grandis:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
05:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] (rev 3a)

may@Grandis:~$ dmesg
(...)
[ 1227.384830] pci 0000:05:00.0: Invalid ROM contents

Device section from xorg.conf:
Section "Device"
    Identifier     "Device0"
    Driver         "ati"
    BusID       "PCI:00:05:00"
    VendorName     "ATI"
    BoardName      "Mach"
EndSection

X version:

X.Org X Server 1.10.4
Release Date: 2011-08-19

Kernel:
may@Grandis:~$ uname -a
Linux Grandis 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I've tried with S3, GF4, RageII and matrox PCI cards- NONE work.
Funny, I was using this configuration (well, AGP+PCI) a decade ago without problems so it sucks it's broken now...

Any ideas / workarounds? I've tried NoInt10=true with no success.

---

