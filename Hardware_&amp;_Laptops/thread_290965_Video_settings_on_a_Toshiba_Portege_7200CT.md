---
title: "Video settings on a Toshiba Portege 7200CT"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by J4DED on 2006-11-01
I was given a Portege 7200CT that I would like to install Xubuntu on. I had to pop the HD into another machine in order to install it because it didn't have a cd drive or even an OS on it. Once I put it back in the Toshiba the video stopped working after the splash screen.

It was suggested that I run **sudo dpkg-reconfigure xserver-xorg** but I cannot determine which settings to use.

I haven't been able to find anything that I understand through google or searching this forum.

I have found out that it has the following /sbin/lspci output:

[FONT="Courier New"]0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
 0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
 0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
 0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
 0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
 0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
 0000:00:06.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 05)
 0000:00:07.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
 0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
 0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
 0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
 0000:00:0c.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
 0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)[/FONT]

Can anyone suggest either a setting or a link?

Thanks.

The laptop I initially installed it on was a P4 3.2GHz w/2GB of RAM while the Toshiba is a PIII 600 w/192 MB of RAM. Would (X)Ubuntu have installed the same version of the kernal regardless or will I need to install a different kernal if i get this up and running?

This is my first time using Linux.

---

### Post by J4DED on 2006-11-05
Just updating this thread in case anyone needs the info in the future:

The lspci output I quoted above might have been inaccurate. I was able to get a usable desktop out of the trident driver.

---

