---
title: "please help detect AMD 6490M video card (10.04 LTS)"
date: 2011-07-23
forum: Hardware
---

### Post by cdiem on 2011-07-23
I have installed ubuntu 10.04 LTS, 64 bit, on a HP Probook 4530s with AMD 6490M video card. However, the display is running in a strange resolution, and on gnome-display-properties the monitor says "Unknown".

lspci 
```

00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6760
24:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
24:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
24:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
25:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
26:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

When running a 32 bit live CD with ubuntu 11.04, it detects it as AMD 6470 instead of 6490 (but runs it in fine resolution and the effects run ok). As far as I can understand, here it is detected as 6760 (or it may be detecting the Intel VGA, I'm not sure). Please help

---

### Post by cdiem on 2011-07-23
Funny thing, after issuing

update-pciids

The new lspci also shows the videocard as 
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

but still doesn't detect it on gnome-display-properties.

---

