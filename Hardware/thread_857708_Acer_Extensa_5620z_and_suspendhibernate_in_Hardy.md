---
title: "Acer Extensa 5620z and suspend/hibernate in Hardy"
date: 2008-07-12
forum: Hardware
---

### Post by softtower on 2008-07-12
My setup: Ubuntu 8.04 + Gnome.

I have Acer Extensa 5620z with Intel X3100 graphics and Atheros WiFi card. Wifi initially did not work out of the box, so I had to download and compile the latest MadWifi release which was easy. (for those who'll be googling "extensa", "ubuntu" + "wifi")

The issue I cannot resolve is suspend/resume. When the laptop goes off to suspend mode, it cannot wake up: in fact it doesn't even get to the booting process:
- I select "Suspend" in Gnome
- It suspends fine. LED is flashing as it did in Windows
- I press the spacebar or any other key
- The laptop tries to wake up: jerks the hard drive, flashes LEDs for a second, then powers off, then repeats this 3 times and reboots.

I tried changing every possible option in /etc/default/acpi-supprt but none of them appeared to make any difference.

My lspci output is listed below.

Any ideas?
Thank you!

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


---

### Post by Trim123 on 2012-01-31
Hi,

I up this message because I've had same problem with Ubuntu 10.04 and 11.10 (resume doesn't work after suspend and/or hibernate).

I've also tried some available options with kernel and pm-suspend. But the solution was too simple : you need to go on acer website and download the latest bios (I had the 2007 version, so I've downloaded 2008 version).

After that all worked : suspend and hibernate.


PS: I had windows in dual boot, so I've used it to upgrade my bios, I don't know how to do it directly from Ubuntu or from usb drive.

---

