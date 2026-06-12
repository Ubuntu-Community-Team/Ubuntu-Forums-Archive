---
title: "Network cards not detected on Sony VAIO VPCEG16FM on Ubuntu 10.04"
date: 2011-08-11
forum: Hardware
---

### Post by nandugopan on 2011-08-11
Guys, 
My friend bought a new lappie. The model is Sony Vaio VPCEG16FM. It came pre-installed with Windows 7. I installed Ubuntu 10.04 on it for him. All went well. But after bootup, the networks cards wouldnt work. Both the wired and the wireless network cards arent being detected. Any workarounds to this?

The kernel is 2.6.32

I did go through some related threads and the first step seemed to be to post the output of lspci:

00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Device 0885 (rev 67)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
09:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)

Hope this info is useful and someone can suggest a workaround. 
Thanks in advance.

---

### Post by nandugopan on 2011-08-12
Guys,
The issue is solved. Incase anyone else runs into this issue, do download the **Atheros AR8151 driver for linux **and then 'make' it. Works good here!:KS
Once thats done do a full update and install the backport stuff for wifi.

---

### Post by poojasaraff on 2012-01-17
Hey can you please give me the link to download the drivers from

thanks

---

