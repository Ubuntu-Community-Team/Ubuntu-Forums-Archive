---
title: "SOundporlbems with znonte 6224 after upgrading to 9.10 64 bit"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by noerbo on 2009-11-02
Hello

  I am having some problems with getting the sound to work on my laptop ater installing ubuntu 9.10 64 bit. It worked fine in 9.04 64bit.

  lspci gives:
[LIST]
[*]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
[*]00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
[*]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
[*]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
[*]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
[*]**00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)**
[*]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
[*]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
[*]00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
[*]00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
[*]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
[*]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
[*]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
[*]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
[*]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
[*]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
[*]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
[*]00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
[*]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
[*]01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
[*]04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
[*]05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
[*]06:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
[*]06:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
[*]06:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
[*]06:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
[/LIST]

  If i open system->preferences->sound->hardware it says 
  Internal audio 
  1 Output
  Analog Stereo Output.

  I have tried the build-in speakers off course and connecting headphones but neither works.

  Does anyone have an idea?

---

