---
title: "GeForce 840M OFF on Lenovo Z50-70"
date: 2014-11-03
forum: Hardware
---

### Post by LinuXXuniL on 2014-11-03
Hey,

I have a problem with my nVidia GeForce 840M on Lenovo Z50-70 laptop. This is the output of[FONT=courier new] lspci[/FONT] commnad:

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)

As you can see there is not VGA compatible controller asociated with my nVidia video card and only integrated graphics it's working. Not big deal cause I do not use Ubuntu with demanding video applications but I guess it would be a good thing to have them both working. I can't install the Additional Drivers for nVidia, cause the card is OFF since I've installed Ubuntu back in June. 

Please let me know if you have the same problem on your laptops or if you managed to solve this small issue!

I'm using Ubuntu 14.04 with kernel version 3.17.1.

Thank you!

---

### Post by kankaanp on 2014-11-27
Now this looks familiar! Got a new Asus X550LNV and an wondering about the graphics drivers also. Got very similar listing (lspci and lshw). Anyone got any thing helpful to tell us?

---

