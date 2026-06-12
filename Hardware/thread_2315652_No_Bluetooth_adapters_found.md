---
title: "No Bluetooth adapters found"
date: 2016-03-01
forum: Hardware
---

### Post by Ruben_D_Prieto on 2016-03-01
So I have installed Ubuntu 15.10 dualboot with windows 7 and there's this issue lately that when I open Bluetooth settings it says no Bluetooth adapters found even though on the status bar you cab turn Bluetooth on and off and see the available devices.
I would appreciate any help. Wouldn't have made a post if I wouldn't have spent at least 4 hours trying to solve it.
Thanks in advance to anyone with ideas:D

Here's info that may help:

rubend@rubend-Aspire-V3-772G:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0d:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
0e:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
rubend@rubend-Aspire-V3-772G:~$ sudo lsmod |grep blue
[sudo] password for rubend: 
bluetooth             516096  25 bnep,ath3k,btbcm,btrtl,btusb,btintel
rubend@rubend-Aspire-V3-772G:~$

---

### Post by jeremy31 on 2016-03-01
Might just be firmware as it shows ath3k loaded, so post ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

