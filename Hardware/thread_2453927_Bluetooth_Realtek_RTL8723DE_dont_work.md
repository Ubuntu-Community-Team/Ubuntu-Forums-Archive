---
title: "Bluetooth Realtek RTL8723DE dont work"
date: 2020-11-19
forum: Hardware
---

### Post by spice0xff on 2020-11-19
Hi!

Notebook HP 15-DA1054UR 6PU75EA
Ubuntu 20.04.1 LTS

After install wi-fi works fine, but bluetooth dont work.
In settings on part bluetooth dongle is disabled (blocked).
On windows its work fine.

Any idea?

lspci
00:00.0 Host bridge: Intel Corporation Coffee Lake HOST and DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0b)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)
00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)
00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 30)
00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #10 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723DE 802.11b/g/n PCIe Adapter

---

### Post by spice0xff on 2020-11-22
lsusb
Bus 002 Device 002: ID 17e9:4300 DisplayLink USB3.0 to DVI Adapter
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0408:5321 Quanta Computer, Inc. HP Webcam
Bus 001 Device 005: ID 8564:1000 Transcend Information, Inc. JetFlash
Bus 001 Device 004: ID 09da:054f A4Tech Co., Ltd. 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg | grep -i blue
nofing

usb-devices
nofing

---

### Post by spice0xff on 2020-11-22
Disables "Fast Startup" in windows not helped.

---

### Post by spice0xff on 2020-11-24
What i done? Restored BIOS settings to default, turn off all peripheral. But problem is not solved.

Is this forum alive?))

---

### Post by CelticWarrior on 2020-11-25
The forum is alive.
Lack of response means no one knows yet (I don't know either).

---

