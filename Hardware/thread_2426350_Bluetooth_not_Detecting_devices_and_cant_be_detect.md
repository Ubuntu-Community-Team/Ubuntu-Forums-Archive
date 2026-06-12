---
title: "Bluetooth not Detecting devices and cant be detected"
date: 2019-09-07
forum: Hardware
---

### Post by eggyeggs on 2019-09-07
Hi, I got a Dell Inspiron 15 3543. I decided to check out my new pair of bluetooth headsets and found out the Ubuntu doesn't detect any of my bluetooth devices. 


eggy@eggy-Inspiron-3543:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux eggy-Inspiron-3543 5.0.0-27-generic #28~18.04.1-Ubuntu SMP Thu Aug 22 03:00:32 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:0655]
	Kernel driver in use: r8169
	Kernel modules: r8169
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0c45:670b Microdia 
Bus 001 Device 003: ID 276d:1160  
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    9.566617] Bluetooth: Core ver 2.22
[    9.566636] Bluetooth: HCI device and connection manager initialized
[    9.566640] Bluetooth: HCI socket layer initialized
[    9.566642] Bluetooth: L2CAP socket layer initialized
[    9.566645] Bluetooth: SCO socket layer initialized
[    9.811553] Bluetooth: hci0: BCM: chip id 70
[    9.812548] Bluetooth: hci0: BCM: features 0x06
[    9.828568] Bluetooth: hci0: eggy-Inspiron-3543
[    9.829566] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   10.120772] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-21d7.hcd failed with error -2
[   10.120780] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0a5c-21d7.hcd not found
[   12.145242] Bluetooth: hci0: command 0x1003 tx timeout
[   12.146574] Bluetooth: hci0: unexpected event for opcode 0x1003
[   23.406050] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.406051] Bluetooth: BNEP filters: protocol multicast
[   23.406055] Bluetooth: BNEP socket layer initialized
[   25.585258] Bluetooth: hci0: command 0x1003 tx timeout
[   25.586610] Bluetooth: hci0: unexpected event for opcode 0x1003
[   70.771743] Bluetooth: RFCOMM TTY layer initialized
[   70.771751] Bluetooth: RFCOMM socket layer initialized
[   70.771757] Bluetooth: RFCOMM ver 1.11
[  101.718650] Bluetooth: hci0: command 0x1003 tx timeout
[  101.720180] Bluetooth: hci0: unexpected event for opcode 0x1003
[    0.105745] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.145601] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   10.120772] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-21d7.hcd failed with error -2
bluetooth             557056  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           28672  1 bluetooth

Help Please!!

---

### Post by jeremy31 on 2019-09-07
Try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0a5c-21d7.hcd
```

Shut down the computer and then boot

---

### Post by eggyeggs on 2019-09-07
Thank You so much, It worked like a miracle. Could I ask about something else as well.

---

### Post by alisabri on 2020-03-14
[COLOR=#000000]Thank You , It worked  my Ubuntu System[/COLOR]

---

