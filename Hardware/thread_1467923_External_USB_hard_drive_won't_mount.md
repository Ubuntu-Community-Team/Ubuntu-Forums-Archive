---
title: "External USB hard drive won't mount"
date: 2010-05-01
forum: Hardware
---

### Post by kaitenbushi on 2010-05-01
Hi,

I can't access my Buffalo external usb hard drive when I plug it in. It doesn't show up in "Computer". I normally use this drive on a Windows machine. The file system is FAT32.
Output from /var/log/messages:

```
May  1 16:51:16 heie-desktop kernel: [86616.296047] usb 1-7: new high speed USB device using ehci_hcd and address 8
May  1 16:51:16 heie-desktop kernel: [86616.434992] usb 1-7: configuration #1 chosen from 1 choice
May  1 16:51:16 heie-desktop kernel: [86616.438967] scsi5 : SCSI emulation for USB Mass Storage devices
May  1 16:51:21 heie-desktop kernel: [86621.437716] scsi 5:0:0:0: Direct-Access     SAMSUNG  SP2504C          VT10 PQ: 0 ANSI: 4
May  1 16:51:21 heie-desktop kernel: [86621.443173] sd 5:0:0:0: Attached scsi generic sg2 type 0
May  1 16:51:21 heie-desktop kernel: [86621.448073] sd 5:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
May  1 16:51:21 heie-desktop kernel: [86621.448803] sd 5:0:0:0: [sdb] Write Protect is off
May  1 16:51:21 heie-desktop kernel: [86621.451184]  sdb: sdb1
May  1 16:51:21 heie-desktop kernel: [86621.457811] sd 5:0:0:0: [sdb] Attached SCSI disk
May  1 16:51:29 heie-desktop kernel: [86629.112048] usb 1-7: reset high speed USB device using ehci_hcd and address 8
May  1 16:51:39 heie-desktop kernel: [86639.360045] usb 1-7: reset high speed USB device using ehci_hcd and address 8
May  1 16:51:55 heie-desktop kernel: [86655.608049] usb 1-7: reset high speed USB device using ehci_hcd and address 8
May  1 16:51:55 heie-desktop kernel: [86655.860039] usb 1-7: reset high speed USB device using ehci_hcd and address 8
May  1 16:52:06 heie-desktop kernel: [86666.104052] usb 1-7: reset high speed USB device using ehci_hcd and address 8
May  1 16:52:06 heie-desktop kernel: [86666.240078] sd 5:0:0:0: Device offlined - not ready after error recovery
```

dmesg shows:
```
[86616.296047] usb 1-7: new high speed USB device using ehci_hcd and address 8
[86616.434992] usb 1-7: configuration #1 chosen from 1 choice
[86616.438967] scsi5 : SCSI emulation for USB Mass Storage devices
[86616.439260] usb-storage: device found at 8
[86616.439265] usb-storage: waiting for device to settle before scanning
[86621.436741] usb-storage: device scan complete
[86621.437716] scsi 5:0:0:0: Direct-Access     SAMSUNG  SP2504C          VT10 PQ: 0 ANSI: 4
[86621.443173] sd 5:0:0:0: Attached scsi generic sg2 type 0
[86621.448073] sd 5:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[86621.448803] sd 5:0:0:0: [sdb] Write Protect is off
[86621.448808] sd 5:0:0:0: [sdb] Mode Sense: 11 00 00 00
[86621.448812] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[86621.451177] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[86621.451184]  sdb: sdb1
[86621.457802] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[86621.457811] sd 5:0:0:0: [sdb] Attached SCSI disk
[86629.112048] usb 1-7: reset high speed USB device using ehci_hcd and address 8
[86639.360045] usb 1-7: reset high speed USB device using ehci_hcd and address 8
[86655.608049] usb 1-7: reset high speed USB device using ehci_hcd and address 8
[86655.860039] usb 1-7: reset high speed USB device using ehci_hcd and address 8
[86666.104052] usb 1-7: reset high speed USB device using ehci_hcd and address 8
[86666.240078] sd 5:0:0:0: Device offlined - not ready after error recovery
```


When I type sudo fdisk -l no information about the hard drive shows up:
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4a5b4a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris
```

When I type ls /dev/sd*
```
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1
```
The two last entries are not there when unplugged.

lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0411:00a7 MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
The second last entry is not there when unplugged.

uname -a
```
Linux heie-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

I am using Ubuntu 10.04 Lucid Lynx, but have had the same problem in earlier distros.
Any help would be highly appreciated!

---

### Post by b3t0n on 2010-05-02
Hi there.
I'm having similar problem, however in my case usb device is only shown in lsusb.
When looking for it in /dev/ it isn't shown.
What's more weird, even when I connect my usb mouse while the ubuntu is running it won't be detected.

I'm running 10.04 stable. If it will help to solve the problem (which apparently many users have - many similar topics where created concerning similar issuses) I can attach logs from lsusb, dmesg and whataver else there is.

---

