---
title: "External Hard Drive Not Found"
date: 2009-08-21
forum: Hardware
---

### Post by tir38 on 2009-08-21
I have a new Western Digital HD. I want to format it (with gParted) to use with Ubuntu. I am having trouble even finding the hard drive.

fdisk -l shows only my two internal HDs:
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x314d314c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61d40e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8454    67906723+   7  HPFS/NTFS
```

lsubs shows only my mouse and wireless dongle:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 004 Device 002: ID 0967:0204 Acer (??) WarpLink 802.11b Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


lastly, tail -f /var/log/messages shows:
```
Aug 21 18:44:42 black kernel: [ 2434.821104] linkstatus=AP_OUTOFRANGE (unhandled)
Aug 21 18:44:43 black kernel: [ 2435.343087] linkstatus=AP_INRANGE
Aug 21 18:49:08 black kernel: [ 2700.671874] linkstatus=AP_OUTOFRANGE (unhandled)
Aug 21 18:49:09 black kernel: [ 2701.147852] linkstatus=AP_INRANGE
Aug 21 18:49:58 black kernel: [ 2750.134345] linkstatus=AP_OUTOFRANGE (unhandled)
Aug 21 18:50:01 black kernel: [ 2753.078431] linkstatus=AP_INRANGE
Aug 21 19:04:31 black -- MARK --
Aug 21 19:11:12 black kernel: [ 4024.865118] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Aug 21 19:11:45 black kernel: [ 4057.589073] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Aug 21 19:14:35 black kernel: [ 4227.428963] usb 1-2: USB disconnect, address 2
```

any guesses what to do now? why is my USB device disconnecting?

---

