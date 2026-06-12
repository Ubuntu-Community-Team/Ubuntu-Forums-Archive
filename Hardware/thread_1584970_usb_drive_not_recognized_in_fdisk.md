---
title: "usb drive not recognized in fdisk"
date: 2010-09-29
forum: Hardware
---

### Post by icoben on 2010-09-29
I upgraded to ubuntu 10.04.
After that, the system cannot recognize the usb drive.
It shows in lsusb, but not in fdisk.
It appears the system does not give a name (sdb1, sdb2...) to the usb drive.

here is the info..

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 059f:0341 LaCie, Ltd 
Bus 001 Device 002: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
[  225.673184] usb 1-5: configuration #1 chosen from 1 choice
[  410.822799] usb 1-5: USB disconnect, address 5
[  416.820038] usb 1-5: new high speed USB device using ehci_hcd and address 6
[  416.953063] usb 1-5: configuration #1 chosen from 1 choice
[  900.144800] usb 1-5: USB disconnect, address 6
[  905.968036] usb 1-6: new high speed USB device using ehci_hcd and address 7
[  906.101735] usb 1-6: configuration #1 chosen from 1 choice
[12473.842593] usb 1-6: USB disconnect, address 7
[12516.432029] usb 1-6: new high speed USB device using ehci_hcd and address 8
[12516.565714] usb 1-6: configuration #1 chosen from 1 choice

``````
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab68ab68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4796    38523838+  83  Linux
/dev/sda2            4797        4866      562275   82  Linux swap / Solaris

```

---

### Post by icoben on 2010-10-01
anybody could help??

---

