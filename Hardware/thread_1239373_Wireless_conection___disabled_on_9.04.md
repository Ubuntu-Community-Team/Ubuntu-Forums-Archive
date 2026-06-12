---
title: "Wireless conection   disabled on 9.04"
date: 2009-08-13
forum: Hardware
---

### Post by shadow9821 on 2009-08-13
Just installed ubuntu on my laptop, it's a Lenovo Y310. When i boot up, the wireless is disabled. Is there a way to enable it? The options on the network manager are unclickable.

---

### Post by zkriesse on 2009-08-13
Can you post a screenshot of the wireless menu?

---

### Post by sergiom99 on 2009-08-13
you can try to install Wicd instead of Network Manager. Works MUCH better
```
sudo apt-get install wicd
```

Besides, which is your wireless card? 
Post the output of the command lspci typed in a terminal.

---

### Post by shadow9821 on 2009-08-14
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)




Just keep in mind, that i have no internet connection on my laptop

---

### Post by sergiom99 on 2009-08-14
I searched for your chipset in the forums and several threads came up.
I would start with:
[http://ubuntuforums.org/showthread.php?t=1135116&highlight=intel+3945ABG](http://ubuntuforums.org/showthread.php?t=1135116&highlight=intel+3945ABG)
[http://ubuntuforums.org/showthread.php?t=991967&highlight=intel+3945ABG](http://ubuntuforums.org/showthread.php?t=991967&highlight=intel+3945ABG)
[http://ubuntuforums.org/showthread.php?t=1135218](http://ubuntuforums.org/showthread.php?t=1135218)
(Search results: [http://ubuntuforums.org/search.php?searchid=62961467&pp=25](http://ubuntuforums.org/search.php?searchid=62961467&pp=25))

Please keep in mind that you'll need to get some kind of internet connection to make it work.
At least to update to the latest packages and kernel.
```
sudo apt-get update && sudo apt-get upgrade
```

---

