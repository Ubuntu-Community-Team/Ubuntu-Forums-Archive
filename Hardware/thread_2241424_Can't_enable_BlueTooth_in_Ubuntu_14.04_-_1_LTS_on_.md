---
title: "Can't enable BlueTooth in Ubuntu 14.04 - 1 LTS on HP Compaq 15 - s001TU (G8D87PA)"
date: 2014-08-26
forum: Hardware
---

### Post by Dissel on 2014-08-26
Hello experts,

Please let me know how to enable Blue Tooth in Ubuntu 14.04 - 1 LTS eidtion. My Machine is HP Compaq 15 - s001TU (G8D87PA)

Here is the result of **lspci** command

> 
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
09:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
09:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth


Now here is a result of **rfkill list** comand

> 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no



here is the picture of setting panel

[IMG]http://i.imgur.com/sIU3cyN.png[/IMG]

There is no way I can enable it - if I click the Bluetooth ON button it still remain disable. It looks like Bluetooth already there but can't able to use it.

Experts please help me out.

---

### Post by delanov on 2014-10-05
Have you got your blue tooth to work?  I have the same problem.  If you got blue tooth up and running, please tell me how;)

---

### Post by Vladlenin5000 on 2014-10-05
[http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04)

---

### Post by Dissel on 2014-10-12
> **Vladlenin5000 said:**
> [http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04)

Followed the instruction from above mentioned link,

Well I'm able to install package using dkms command - everything went well - no error ,

But there is **no way I can enable BlueTooth** after following that method in 'ask ubuntu' forum.

---

### Post by jeremy31 on 2014-10-12
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1355096](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1355096)

Sounds like Realtek doesn't want to release the driver to get the bluetooth working

---

