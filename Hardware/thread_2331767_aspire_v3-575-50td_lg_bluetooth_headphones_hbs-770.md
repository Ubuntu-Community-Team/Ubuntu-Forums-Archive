---
title: "aspire v3-575-50td lg bluetooth headphones hbs-770"
date: 2016-07-25
forum: Hardware
---

### Post by rev-matthewagilmore on 2016-07-25
the bluetooth connects but no sounds other then it saying connected.It does vibrate when  sound is sups to be coming in to the head set

---

### Post by jeremy31 on 2016-07-26
Post the results from terminal for ```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'; pactl list short | grep blue
```

---

### Post by rev-matthewagilmore on 2016-08-09
now bluetooth not working at all

---

### Post by jeremy31 on 2016-08-09
Please post the results for the commands as it just gets info about your bluetooth

---

### Post by rev-matthewagilmore on 2016-08-28
```
matti@matti-Aspire-V3-575:~$ lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'; pactl list short | grep blue01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1030]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Foxconn International, Inc. QCA6174 802.11ac Wireless Network Adapter [105b:e09d]
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b51f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0489:e09f Foxconn / Hon Hai 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 48:E2:44:AE:B6:12  ACL MTU: 1024:8  SCO MTU: 50:8
	UP RUNNING PSCAN 
	RX bytes:699 acl:0 sco:0 events:48 errors:0
	TX bytes:2469 acl:0 sco:0 commands:48 errors:0
	Features: 0xff 0xfe 0x8f 0xfe 0xd8 0x3f 0x5b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'matti-Aspire-V3-575'
	Class: 0x00010c
	Service Classes: Unspecified
	Device Class: Computer, Laptop
	HCI Version: 4.1 (0x7)  Revision: 0x0
	LMP Version: 4.1 (0x7)  Subversion: 0x25a
	Manufacturer: Qualcomm (29)


[    0.178428] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   13.268801] Bluetooth: Core ver 2.21
[   13.268816] Bluetooth: HCI device and connection manager initialized
[   13.268820] Bluetooth: HCI socket layer initialized
[   13.268822] Bluetooth: L2CAP socket layer initialized
[   13.268838] Bluetooth: SCO socket layer initialized
[   14.859944] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   14.927675] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   14.927680] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   27.090788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.090791] Bluetooth: BNEP filters: protocol multicast
[   27.090794] Bluetooth: BNEP socket layer initialized

```

---

### Post by jeremy31 on 2016-08-28
Looks like a working bluetooth so far
```
bluetoothctl
power on
scan on
devices
exit
```

---

