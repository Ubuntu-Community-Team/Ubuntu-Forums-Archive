---
title: "USB Recognition Problem"
date: 2008-09-26
forum: Hardware
---

### Post by Cjmkee on 2008-09-26
I have Ubuntu Linux on a IBM think pad and when I plug in my Wester Digital Ext HDD nothing happens. I have been working on this problem for 2 days now with no luck. Here are the outputs for lsusb, dmessage | tail -n 20, and sudo fdisk -l 

Does anyone know why its doing this?

lsusb

chris@chris-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

dmessage | tail -n 20
chris@chris-laptop:~$ dmesg | tail -n 20
[ 9895.790258] usb 4-4: new high speed USB device using ehci_hcd and address 44
[10949.703071] usb 4-4: new high speed USB device using ehci_hcd and address 54
[10950.227445] usb 4-4: new high speed USB device using ehci_hcd and address 58
[10951.913335] usb 4-4: new high speed USB device using ehci_hcd and address 72
[10957.955050] usb 4-4: new high speed USB device using ehci_hcd and address 112
[10962.148229] usb 4-4: new high speed USB device using ehci_hcd and address 126
[ 3868.181565] usb 4-4: new high speed USB device using ehci_hcd and address 4
[10966.132954] usb 4-4: new high speed USB device using ehci_hcd and address 10
[10967.066780] usb 4-4: new high speed USB device using ehci_hcd and address 21
[10967.271905] usb 4-4: new high speed USB device using ehci_hcd and address 22
[10967.600226] usb 4-4: new high speed USB device using ehci_hcd and address 24
[10968.180856] usb 4-4: new high speed USB device using ehci_hcd and address 29
[10969.574177] usb 4-4: new high speed USB device using ehci_hcd and address 40
[10970.376981] usb 4-4: new high speed USB device using ehci_hcd and address 47
[10971.009316] usb 4-4: new high speed USB device using ehci_hcd and address 51
[10971.689266] usb 4-4: new high speed USB device using ehci_hcd and address 56
[10972.124880] usb 4-4: new high speed USB device using ehci_hcd and address 59
[10972.940490] usb 4-4: new high speed USB device using ehci_hcd and address 65
[10973.981045] usb 4-4: new high speed USB device using ehci_hcd and address 74
[10974.260761] usb 4-4: new high speed USB device using ehci_hcd and address 76


chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b939b93

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris
chris@chris-laptop:~$

---

