---
title: "Toshiba Satellite M105-S3001 - IrDA and Memory Reader (SD, MMC,MS)"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by pereira on 2006-09-24
Hi,

I bought a Toshiuba Satellite M105-S3001 with this "lspci" output:

```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:05:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:05:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:05:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:05:06.3 0805: Texas Instruments: Unknown device 803c
0000:05:08.0 Ethernet controller: Intel Corporation: Unknown device 1093 (rev 02)

```

All hardware worked out of the box, except: IrDA and Memory Reader.

Not tested: Firewire, pcmcia.

I don't know which drive to load for IrDA and I'm looking for a debian package for the Memory Reader (TI FlashMedia xx12/xx21 driver). Some one know how to find out about this?

Thanks in advance.

---

### Post by digitalwave43 on 2007-12-19
If and when you find out, let me know.  I want to be able to use my SD memory cards while using 7.10.  I have a M105-S3094 though.

---

