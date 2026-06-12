---
title: "Problems with Nvidia on a Dell n5110"
date: 2011-09-11
forum: Hardware
---

### Post by seif12 on 2011-09-11
Hi , i am trying to install Ubuntu in a Dell n5110 laptop that i get it  from my brother . 
The problem is that i have no idea about the hardware on it , and the problem come exactly with the Nvidia devices it's Seems that Ubuntu doesn't  recognize it . 
My brother told me that the Graphic card is a 
Geforce GT525m so i donwloaded the driver from Nvidia website  and try to install it .
but after the installation there is a X server error with a message "no screen found"
and the X server is unable to start .
another problem that i have no sound .
So please help me if you can thanks .

**here is the output of lspci **

```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)lp
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4b (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
seif@seif-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4b (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)

```



```

**Motherboard :**
SMBios version 2.6
Dell Inc. 0FXK2Y A06
Bios: Dell Inc. A06 05/26/2011 taille: 2048Kb
[B]
Processor :[/B]
Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz (800Mhz) (L1: 0ko )

**Display **
Intel Corporation:Sandy Bridge Integrated Graphics Controller: 
Unknown Hardware (V:nVidia Corporation,D:0xdf5)

**Multimedia **
Intel Corporation:Cougar Point High Definition Audio Controller: 
Unknown Hardware (V:nVidia Corporation,D:0xbea)




```

---

