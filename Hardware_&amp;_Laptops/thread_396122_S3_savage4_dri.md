---
title: "S3 savage4 dri"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by tanozfood on 2007-03-29
Hello,
I have tried new ubuntu 7.04 to get dri works with my card (S3 savage4, 16M) after
people says to try a recent version of gnu/linux to have more chances..
However, even if all seems to be correctly configured, the pc hangs when I launch
glxgears, and need to be rebooted. I include logs here (I follow dri.freedesktop.org
steps on troubleshooting):

[FONT="Fixedsys"]
> lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 21)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0d)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0d.0 Communication controller: Rockwell International HSF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 04)
 
> dmesg | grep agp
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected VIA Apollo Pro 133 chipset
agpgart: AGP aperture is 64M @ 0xd8000000
agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
 
> dmesg | grep drm
[drm] Initialized drm 1.0.1 20051102
[drm] Initialized savage 2.4.1 20050313 on minor 0
 
> cat /var/log/Xorg.0.log | grep "Direct rendering"
(II) SAVAGE(0): Direct rendering enabled
 
..in Xorg.0.log there is also:
(II) SAVAGE: driver (version 2.0.2) for S3 Savage chipsets: Savage4,
 Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
 Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
 Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
 SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
 SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
 SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset Savage4 found
 
> xdriinfo
Screen 0: savage
 
> glxinfo | grep "direct rendering"
direct rendering: Yes
 
lsmod lists these modules : savage, drm, via_agp, agpart, i2c_savage4, i2c_algo_bit, i2c_viapro, i2c_core
[/FONT]

Any suggestion?
Thanks,
                  tano

---

