---
title: "Wirless not functioning - Acert Extensa 5620z - Natty 11.04"
date: 2011-06-12
forum: Hardware
---

### Post by e4rendil on 2011-06-12
Hello guys,

yesterday I installed the newest release, 11.04 on my little Acer. Before I had the 10.04 and there wasn't any problem at all.
Right now I'm experiencing an issue regarding the wireless.

Drivers are ok, installed and, for Driver Manager's opinion, working properly.
Ethernet works fine.
Wireless is physically turned off, no way to turn on manually, the little switch is disabled/doesn't work.
If I run iwconfig, I obtain 3 prints, all of them : "no wireless extensions".

Is there any solution to turn on via terminal the wireless card?

I also checked the BIOS, but there's no option about this :(

Thank you very much guys!

---

### Post by webofunni on 2011-06-12
There should be a key or key combination in the keyboard to turn on the wireless

---

### Post by uRock on 2011-06-22
Can you please post the output of the **lspci** command in a terminal so that we can see exactly what hardware is in use?

---

### Post by Enkera on 2011-07-27
Same problem here on Extensa 5220, worked fine on 10.04
Additional drivers window shows broadcom drivers installed and active, even tried reinstall using synaptic.
It just won't turn on physically anymore, light doesn't work either
(there's a switch and a light on the front of the laptop)
bluetooth has a switch next to it, also doesn't work anymore, although wifi is the main issue here.

Any help would be hot :D

here's the terminal info;

anja@anja-Extensa-5220:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
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
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by Enkera on 2011-07-27
[SOLVED]

I followed the instructions posted here to install the older drivers!

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/23](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/23)

Still, someone should make sure wifi works out-of-the-box again!:popcorn:

---

### Post by swift100 on 2011-07-27
There seems to be a bug in 11.4 with the wifi driver. In my case on 2 laptops wireless was not detected with the most recent Broadcom driver. Removing the current driver and installing the earlier version worked. Read that more people had problems of this sort.

---

