---
title: "Toshiba Satellite Pro S300-S2504"
date: 2009-06-18
forum: Hardware
---

### Post by ScottTE on 2009-06-18
Hi,

I loaded Ubuntu 9.04 on this laptop with no problem at all. As far as I can see most everything is working to include the built in camera, with the exception of sound it seems to be fine.

I had Ubuntu use the entire HD and deleted VISTA that was preloaded. When I boot an identical Laptop under VISTA it sees the sounds as a Realtek HighDef Audio w/EC. I went to Realtek's website and downloaded the Realtek Audio HD Linux drivers, but I don't know how to install the drivers?

I was able to extract the tar.gzb file a directory and can see all the file and subfolders but don't know how to install these drivers. In windows I would just add a new driver and navigate to the directory.. But how do I load these drivers in Ubuntu??

Thanks. Scott.

---

### Post by aharown07 on 2009-08-27
I'd be interested in this also.

And to the OP... did you say you got the webcam working? Is there an applet somewhere that makes it work? I'm not finding anything to show if mine is even working (I'm also s300 s2504)

Edit: nevermind about the webcam... have it working with Cheese, though it doesn't work w/Camorama at present... "Could not connect to video device (/dev/video0)"

---

### Post by IcarusR on 2009-08-29
From terminal type lspci & post output, to check sound card details.

---

### Post by aharown07 on 2009-08-29
Here's the output...
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567V Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:0b.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:0b.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:0b.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
05:0b.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
05:0b.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
05:0b.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

---

### Post by IcarusR on 2009-08-29
My Tosh A100-305 has the previous version of the same Intel HD Audio Controller. In Ubuntu 8.10 it works out of the box.
On my system it uses the snd_hda_intel module.

To install the driver from Realtek you first need to install the following package build-essential

```
sudo apt-get install build-essential
```

If you have already extracted the tarball contents then **carefully** read the Readme.txt & follow the instructions.

I'm not altogether sure that this will resolve your issue though.

---

