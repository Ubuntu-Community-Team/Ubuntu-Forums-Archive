---
title: "No Bluetooth adapters found"
date: 2014-11-03
forum: Hardware
---

### Post by Aceninja on 2014-11-03
Hi,

I'm running Ubuntu 14.10 and have an ASUS X79 DELUXE LGA 2011 Intel MotherBoard with built in bluetooth adapter. It works fine in Windows but I can't seem to get Ubuntu to recognize it. When I click on Bluetooth in System settings, it says "No Bluetooth Adapters found". As far as I know ASUS does not make drivers for Ubuntu or Linux for that matter. 

Did anyone else have the same issue? Any idea on how to resolve it will be appreciated. Newbie here.

Thanks!

---

### Post by weatherman2 on 2014-11-03
Open a terminal (Ctrl - Alt - t) and type these command, then copy the output here.  These commands are diagnostic commands - they won't fix anything but can help others try to figure out what's wrong:

```

rfkill list all
lspci -nn
lsusb
grep -i bluetooth /var/log/syslog

```

---

### Post by Aceninja on 2014-11-03
> **weatherman2 said:**
> Open a terminal (Ctrl - Alt - t) and type these command, then copy the output here.  These commands are diagnostic commands - they won't fix anything but can help others try to figure out what's wrong:

```

rfkill list all
lspci -nn
lsusb
grep -i bluetooth /var/log/syslog

```

Thanks for the reply. Here is the info:

**rfkill list all**

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

**lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 DMI2 [8086:0e00] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 1a [8086:0e02] (rev 04)
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 1b [8086:0e03] (rev 04)
00:02.0 PCI bridge [0604]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 2a [8086:0e04] (rev 04)
00:03.0 PCI bridge [0604]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 3a [8086:0e08] (rev 04)
00:05.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 VTd/Memory Map/Misc [8086:0e28] (rev 04)
00:05.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 IIO RAS [8086:0e2a] (rev 04)
00:05.4 PIC [0800]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 IOAPIC [8086:0e2c] (rev 04)
00:11.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port [8086:1d3e] (rev 06)
00:16.0 Communication controller [0780]: Intel Corporation C600/X79 series chipset MEI Controller #1 [8086:1d3a] (rev 05)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 [8086:1d2d] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation C600/X79 series chipset High Definition Audio Controller [8086:1d20] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 [8086:1d10] (rev b6)
00:1c.1 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 [8086:1d12] (rev b6)
00:1c.2 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 [8086:1d14] (rev b6)
00:1c.3 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 4 [8086:1d16] (rev b6)
00:1c.4 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 5 [8086:1d18] (rev b6)
00:1c.5 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 6 [8086:1d1a] (rev b6)
00:1c.7 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 8 [8086:1d1e] (rev b6)
00:1d.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 [8086:1d26] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation C600/X79 series chipset LPC Controller [8086:1d41] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller [8086:1d02] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation C600/X79 series chipset SMBus Host Controller [8086:1d22] (rev 06)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 760] [10de:1187] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
04:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller [1b4b:9230] (rev 10)
06:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
07:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
08:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
09:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
0a:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
0c:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
ff:08.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Link 0 [8086:0e80] (rev 04)
ff:09.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Link 1 [8086:0e90] (rev 04)
ff:0a.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 0 [8086:0ec0] (rev 04)
ff:0a.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 1 [8086:0ec1] (rev 04)
ff:0a.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 2 [8086:0ec2] (rev 04)
ff:0a.3 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 3 [8086:0ec3] (rev 04)
ff:0b.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 UBOX Registers [8086:0e1e] (rev 04)
ff:0b.3 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 UBOX Registers [8086:0e1f] (rev 04)
ff:0c.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee0] (rev 04)
ff:0c.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee2] (rev 04)
ff:0c.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee4] (rev 04)
ff:0d.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee1] (rev 04)
ff:0d.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee3] (rev 04)
ff:0d.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers [8086:0ee5] (rev 04)
ff:0e.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Home Agent 0 [8086:0ea0] (rev 04)
ff:0e.1 Performance counters [1101]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Home Agent 0 [8086:0e30] (rev 04)
ff:0f.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Target Address/Thermal Registers [8086:0ea8] (rev 04)
ff:0f.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 RAS Registers [8086:0e71] (rev 04)
ff:0f.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers [808... (rev 04)
ff:0f.3 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers [808... (rev 04)
ff:0f.4 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers [808... (rev 04)
ff:0f.5 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers [808... (rev 04)
ff:10.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 0 [8086:0eb0] (rev 04)
ff:10.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 1 [8086:0eb1] (rev 04)
ff:10.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 0 [8086:0eb2] (rev 04)
ff:10.3 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 1 [8086:0eb3] (rev 04)
ff:10.4 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 2 [8086:0eb4] (rev 04)
ff:10.5 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 3 [8086:0eb5] (rev 04)
ff:10.6 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 2 [8086:0eb6] (rev 04)
ff:10.7 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 3 [8086:0eb7] (rev 04)
ff:13.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 R2PCIe [8086:0e1d] (rev 04)
ff:13.1 Performance counters [1101]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 R2PCIe [8086:0e34] (rev 04)
ff:13.4 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Ring Registers [8086:0e81] (rev 04)
ff:13.5 Performance counters [1101]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Ring Performance Ring Monitoring [8086:0e36] (rev 04)
ff:16.0 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 System Address Decoder [8086:0ec8] (rev 04)
ff:16.1 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Broadcast Registers [8086:0ec9] (rev 04)
ff:16.2 System peripheral [0880]: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Broadcast Registers [8086:0eca] (rev 04)

**lsusb**

Bus 002 Device 004: ID 1b1c:0c04 Corsair 
Bus 002 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 8564:4000  
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**grep -i bluetooth /var/log/syslog**

Nov  3 00:18:47 ubudesk bluetoothd[839]: Terminating
Nov  3 00:18:47 ubudesk bluetoothd[839]: Stopping SDP server
Nov  3 00:18:47 ubudesk bluetoothd[839]: Exit
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Bluetooth daemon 4.101
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Starting SDP server
Nov  3 00:44:17 ubudesk bluetoothd[4574]: DIS cannot start: GATT is disabled
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init deviceinfo plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init proximity plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init time plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init alert plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init thermometer plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Failed to init gatt_example plugin
Nov  3 00:44:17 ubudesk bluetoothd[4574]: Bluetooth Management interface initialized
Nov  3 00:51:51 ubudesk bluetoothd[760]: Bluetooth daemon 4.101
Nov  3 00:51:51 ubudesk bluetoothd[760]: Starting SDP server
Nov  3 00:51:51 ubudesk bluetoothd[760]: DIS cannot start: GATT is disabled
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init deviceinfo plugin
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init proximity plugin
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init time plugin
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init alert plugin
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init thermometer plugin
Nov  3 00:51:51 ubudesk kernel: [    4.087162] Bluetooth: Core ver 2.19
Nov  3 00:51:51 ubudesk kernel: [    4.087180] Bluetooth: HCI device and connection manager initialized
Nov  3 00:51:51 ubudesk kernel: [    4.087186] Bluetooth: HCI socket layer initialized
Nov  3 00:51:51 ubudesk kernel: [    4.087188] Bluetooth: L2CAP socket layer initialized
Nov  3 00:51:51 ubudesk kernel: [    4.087196] Bluetooth: SCO socket layer initialized
Nov  3 00:51:51 ubudesk kernel: [    4.092702] Bluetooth: RFCOMM TTY layer initialized
Nov  3 00:51:51 ubudesk kernel: [    4.092710] Bluetooth: RFCOMM socket layer initialized
Nov  3 00:51:51 ubudesk kernel: [    4.092714] Bluetooth: RFCOMM ver 1.11
Nov  3 00:51:51 ubudesk kernel: [    4.093517] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  3 00:51:51 ubudesk kernel: [    4.093519] Bluetooth: BNEP filters: protocol multicast
Nov  3 00:51:51 ubudesk kernel: [    4.093522] Bluetooth: BNEP socket layer initialized
Nov  3 00:51:51 ubudesk bluetoothd[760]: Failed to init gatt_example plugin
Nov  3 00:51:51 ubudesk bluetoothd[760]: Bluetooth Management interface initialized
Nov  3 17:35:00 ubudesk bluetoothd[974]: Bluetooth daemon 4.101
Nov  3 17:35:00 ubudesk bluetoothd[974]: Starting SDP server
Nov  3 17:35:00 ubudesk kernel: [    4.180493] Bluetooth: Core ver 2.19
Nov  3 17:35:00 ubudesk kernel: [    4.180507] Bluetooth: HCI device and connection manager initialized
Nov  3 17:35:00 ubudesk kernel: [    4.180514] Bluetooth: HCI socket layer initialized
Nov  3 17:35:00 ubudesk kernel: [    4.180515] Bluetooth: L2CAP socket layer initialized
Nov  3 17:35:00 ubudesk kernel: [    4.180523] Bluetooth: SCO socket layer initialized
Nov  3 17:35:00 ubudesk bluetoothd[974]: DIS cannot start: GATT is disabled
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init deviceinfo plugin
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init proximity plugin
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init time plugin
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init alert plugin
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init thermometer plugin
Nov  3 17:35:00 ubudesk kernel: [    4.182667] Bluetooth: RFCOMM TTY layer initialized
Nov  3 17:35:00 ubudesk kernel: [    4.182672] Bluetooth: RFCOMM socket layer initialized
Nov  3 17:35:00 ubudesk kernel: [    4.182675] Bluetooth: RFCOMM ver 1.11
Nov  3 17:35:00 ubudesk bluetoothd[974]: Failed to init gatt_example plugin
Nov  3 17:35:00 ubudesk bluetoothd[974]: Bluetooth Management interface initialized
Nov  3 17:35:00 ubudesk kernel: [    4.187345] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  3 17:35:00 ubudesk kernel: [    4.187346] Bluetooth: BNEP filters: protocol multicast
Nov  3 17:35:00 ubudesk kernel: [    4.187349] Bluetooth: BNEP socket layer initialized
Nov  3 18:13:51 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:13:51 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:13:56 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('bluez-alsa')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:13:57 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String('bluez-alsa')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:13:57 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:13:57 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:15:07 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:15:07 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:28:50 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:28:50 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:29:24 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:29:24 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:29:26 ubudesk AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s'))'
Nov  3 18:29:26 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:29:38 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:29:38 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:29:43 ubudesk AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s'))'
Nov  3 18:29:43 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:31:35 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:31:36 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('gnome-bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:32:07 ubudesk URfkill[10913]: Setting BLUETOOTH devices to unblocked
Nov  3 18:34:19 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:34:20 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:34:22 ubudesk AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Nov  3 18:34:23 ubudesk AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('bluetooth')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov  3 18:45:50 ubudesk bluetoothd[770]: Bluetooth daemon 4.101
Nov  3 18:45:50 ubudesk bluetoothd[770]: Starting SDP server
Nov  3 18:45:50 ubudesk bluetoothd[770]: DIS cannot start: GATT is disabled
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init deviceinfo plugin
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init proximity plugin
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init time plugin
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init alert plugin
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init thermometer plugin
Nov  3 18:45:50 ubudesk kernel: [    4.186592] Bluetooth: Core ver 2.19
Nov  3 18:45:50 ubudesk kernel: [    4.186610] Bluetooth: HCI device and connection manager initialized
Nov  3 18:45:50 ubudesk kernel: [    4.186618] Bluetooth: HCI socket layer initialized
Nov  3 18:45:50 ubudesk kernel: [    4.186620] Bluetooth: L2CAP socket layer initialized
Nov  3 18:45:50 ubudesk kernel: [    4.186628] Bluetooth: SCO socket layer initialized
Nov  3 18:45:50 ubudesk kernel: [    4.194199] Bluetooth: RFCOMM TTY layer initialized
Nov  3 18:45:50 ubudesk kernel: [    4.194206] Bluetooth: RFCOMM socket layer initialized
Nov  3 18:45:50 ubudesk kernel: [    4.194210] Bluetooth: RFCOMM ver 1.11
Nov  3 18:45:50 ubudesk bluetoothd[770]: Failed to init gatt_example plugin
Nov  3 18:45:50 ubudesk kernel: [    4.197755] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  3 18:45:50 ubudesk kernel: [    4.197757] Bluetooth: BNEP filters: protocol multicast
Nov  3 18:45:50 ubudesk kernel: [    4.197760] Bluetooth: BNEP socket layer initialized
Nov  3 18:45:50 ubudesk bluetoothd[770]: Bluetooth Management interface initialized
Nov  3 18:45:50 ubudesk URfkill[750]: Setting BLUETOOTH devices to unblocked

---

### Post by weatherman2 on 2014-11-04
I think this is your bluetooth device:

```

Bus 002 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 

```

Here's a thread with a similar problem for the same hardware you have, with a half solution at the end (the fix didn't "stick" after reboot, but you can try it):

[http://ubuntuforums.org/showthread.php?t=2243407](http://ubuntuforums.org/showthread.php?t=2243407)

---

