---
title: "USB Hard Drive Errors...  Yes, another post..."
date: 2008-12-22
forum: Hardware
---

### Post by Giric on 2008-12-22
Once more, someone's having issues getting a USB hard drive to work with 8.10.  I have been through the forums and looked at all kinds of links that address this issue.

The Machine:  Desktop with an A-Bit NF7-S motherboard and AMD x86 chip that rivaled the P-4.
The Device:  Maxtor 3200 USB External Hard Drive
As seen here:
```
eiela@Beckys:/var/log$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0d49:3200 Maxtor 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I've seen suggested to run the following:
```
eiela@Beckys:/var/log$ tail -f /var/log/syslog
Dec 22 15:16:50 Beckys kernel: [  535.432263] usb-storage: device scan complete
Dec 22 15:16:56 Beckys kernel: [  541.044022] usb 3-3: reset high speed USB device using ehci_hcd and address 4
Dec 22 15:17:01 Beckys kernel: [  546.156020] usb 3-3: device descriptor read/64, error -71
Dec 22 15:17:01 Beckys /USR/SBIN/CRON[5866]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 22 15:17:11 Beckys kernel: [  556.544019] usb 3-3: reset high speed USB device using ehci_hcd and address 4
Dec 22 15:17:27 Beckys kernel: [  572.792019] usb 3-3: reset high speed USB device using ehci_hcd and address 4
Dec 22 15:17:28 Beckys kernel: [  573.048041] usb 3-3: reset high speed USB device using ehci_hcd and address 4
Dec 22 15:17:38 Beckys kernel: [  583.296020] usb 3-3: reset high speed USB device using ehci_hcd and address 4
Dec 22 15:17:38 Beckys kernel: [  583.434180] scsi 6:0:0:0: Device offlined - not ready after error recovery
Dec 22 15:28:23 Beckys -- MARK --
Dec 22 15:30:24 Beckys kernel: [ 1349.182842] usb 3-3: USB disconnect, address 4
Dec 22 15:30:28 Beckys kernel: [ 1353.848038] usb 3-3: new high speed USB device using ehci_hcd and address 5
Dec 22 15:30:29 Beckys kernel: [ 1354.011186] usb 3-3: configuration #1 chosen from 1 choice
Dec 22 15:30:29 Beckys kernel: [ 1354.045001] scsi7 : SCSI emulation for USB Mass Storage devices
Dec 22 15:30:29 Beckys kernel: [ 1354.048516] usb-storage: device found at 5
Dec 22 15:30:29 Beckys kernel: [ 1354.048526] usb-storage: waiting for device to settle before scanning
Dec 22 15:30:34 Beckys kernel: [ 1359.048247] usb-storage: device scan complete
Dec 22 15:30:39 Beckys kernel: [ 1364.660038] usb 3-3: reset high speed USB device using ehci_hcd and address 5
Dec 22 15:30:44 Beckys kernel: [ 1369.772033] usb 3-3: device descriptor read/64, error -71
Dec 22 15:30:55 Beckys kernel: [ 1380.128034] usb 3-3: reset high speed USB device using ehci_hcd and address 5
Dec 22 15:31:11 Beckys kernel: [ 1396.376032] usb 3-3: reset high speed USB device using ehci_hcd and address 5
Dec 22 15:31:11 Beckys kernel: [ 1396.628025] usb 3-3: reset high speed USB device using ehci_hcd and address 5
Dec 22 15:31:21 Beckys kernel: [ 1406.876026] usb 3-3: reset high speed USB device using ehci_hcd and address 5
Dec 22 15:31:22 Beckys kernel: [ 1407.021046] scsi 7:0:0:0: Device offlined - not ready after error recovery
^C
```

At the --MARK-- pause point, I unplugged the hard drive and plugged it back in.  There's no difference, really, between that and dmesg.  So, I try this:```

eiela@Beckys:/var/log$ sudo rmmod ehci_hcd
eiela@Beckys:/var/log$ dmesg
[ 1597.678054] ehci_hcd 0000:00:02.2: remove, state 1
[ 1597.678076] usb usb3: USB disconnect, address 1
[ 1597.678079] usb 3-3: USB disconnect, address 5
[ 1597.682634] ehci_hcd 0000:00:02.2: USB bus 3 deregistered
[ 1597.682703] ehci_hcd 0000:00:02.2: PCI INT C disabled
[ 1598.056029] usb 2-1: new full speed USB device using ohci_hcd and address 2
[ 1598.285333] usb 2-1: configuration #1 chosen from 1 choice
[ 1598.346494] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1598.352789] usb-storage: device found at 2
[ 1598.352797] usb-storage: waiting for device to settle before scanning
[ 1603.353845] usb-storage: device scan complete
[ 1609.028032] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1619.416035] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1635.812031] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1636.204363] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1646.592029] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1646.805904] scsi 8:0:0:0: Device offlined - not ready after error recovery
```

And, finally,```

eiela@Beckys:/var/log$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1264c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7165    57552831   83  Linux
/dev/sdb2            7166        7476     2498107+   5  Extended
/dev/sdb5            7166        7476     2498076   82  Linux swap / Solaris
eiela@Beckys:/var/log$ lsusb
Bus 002 Device 002: ID 0d49:3200 Maxtor 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

My wife needs some stuff off the drive for work (she's a school librarian and in charge of the yearbook).  Any help would be appreciated.

Thanks,

Brandon Pisani

---

