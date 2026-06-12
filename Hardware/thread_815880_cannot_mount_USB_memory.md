---
title: "cannot mount USB memory"
date: 2008-06-02
forum: Hardware
---

### Post by dhap on 2008-06-02
I installed Ubuntu 8.04 2 days back, every thing went as usual until I found that the system couldn't mount USB memory! This is what I get from 
dmesg | tail 

[ 1340.153665] usb 4-4: new high speed USB device using ehci_hcd and address 25
[ 1340.641598] usb 4-4: new high speed USB device using ehci_hcd and address 27
[ 1342.257406] usb 4-4: new high speed USB device using ehci_hcd and address 35
[ 1347.256777] usb 4-4: new high speed USB device using ehci_hcd and address 61
[ 1347.744714] usb 4-4: new high speed USB device using ehci_hcd and address 63
[ 1349.360521] usb 4-4: new high speed USB device using ehci_hcd and address 71
[ 1350.788996] usb 4-4: new high speed USB device using ehci_hcd and address 78
[ 1352.592109] usb 4-4: new high speed USB device using ehci_hcd and address 87
[ 1353.831948] usb 4-4: new high speed USB device using ehci_hcd and address 93
[ 1354.131910] usb 4-4: new high speed USB device using ehci_hcd and address 94

The address filed keeps changing every time I type dmesg. Similar problem arises for other USB memories as well. However, the same memory sticks works perfectly fine in another Ubuntu 8.04 laptop. please help.

---

### Post by dhap on 2008-06-02
It suddenly worked for some time... but stopped later with the same dmesg output! please help. I am running an IBM T42.

---

