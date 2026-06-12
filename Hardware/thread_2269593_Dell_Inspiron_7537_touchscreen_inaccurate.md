---
title: "Dell Inspiron 7537 touchscreen inaccurate"
date: 2015-03-16
forum: Hardware
---

### Post by waxcan on 2015-03-16
Hi folks,
Noob here running Ubuntu 14.04 and Win 8.1 dual boot almost without issue.

A minor but kind of annoying issue relates to my touchscreen monitor when linked via HDMI to a second ASUS non-touchscreen monitor set up on the left. The cursor placement is quite inaccurate so that the cursor falls on the far left of the screen when touched on the right , although two-finger zooming works. 

Everything works fine when the HDMI cable is disconnected.

Some outputs:

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

lspci

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
03:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
04:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)


Lastly and perhaps this should be a separate topic, but the audio sounds better using the OEM Dell Realtek ALC3223 audio driver on Windows. 

[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=Y0XXV&fileId=3283877256&osCode=W864&productCode=inspiron-15-7537&languageCode=EN&categoryId=AU](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=Y0XXV&fileId=3283877256&osCode=W864&productCode=inspiron-15-7537&languageCode=EN&categoryId=AU)

Is there a way to install an equivalent for Ubunutu? It's advertised as having Waves MaxxAudio® Pro. That's all I know :/

---

