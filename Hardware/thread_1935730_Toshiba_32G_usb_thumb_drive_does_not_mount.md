---
title: "Toshiba 32G usb thumb drive does not mount"
date: 2012-03-04
forum: Hardware
---

### Post by readyrevolver on 2012-03-04
Hey,

I just bought a 32G Toshiba usb flash thumb drive and it wont mount in ubuntu. Other thumb drives I have mount just fine, and this new one mounts fine on my OS X box.

The device is detected and attached as an scsi drive:

Mar  5 13:27:38 edge kernel: [ 3018.231821] usb 1-1.2: new high speed USB device using ehci_hcd and address 15
Mar  5 13:27:39 edge kernel: [ 3018.430803] scsi13 : usb-storage 1-1.2:1.0
Mar  5 13:27:40 edge kernel: [ 3019.421616] scsi 13:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
Mar  5 13:27:40 edge kernel: [ 3019.422919] sd 13:0:0:0: Attached scsi generic sg3 type 0
Mar  5 13:27:40 edge kernel: [ 3019.424341] sd 13:0:0:0: [sdc] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
Mar  5 13:27:40 edge kernel: [ 3019.425847] sd 13:0:0:0: [sdc] Write Protect is off
Mar  5 13:27:40 edge kernel: [ 3019.425856] sd 13:0:0:0: [sdc] Mode Sense: 03 00 00 00
Mar  5 13:27:40 edge kernel: [ 3019.425862] sd 13:0:0:0: [sdc] Assuming drive cache: write through
Mar  5 13:27:40 edge kernel: [ 3019.427967] sd 13:0:0:0: [sdc] Assuming drive cache: write through
Mar  5 13:27:40 edge kernel: [ 3019.575456]  sdc: sdc1
Mar  5 13:27:40 edge kernel: [ 3019.577172] sd 13:0:0:0: [sdc] Assuming drive cache: write through
Mar  5 13:27:40 edge kernel: [ 3019.577179] sd 13:0:0:0: [sdc] Attached SCSI removable disk

But is not auto-mounted, and any attempted to manually mount results in mount just hanging. Running "fdisk -l" with the device inserted takes a very long time to complete (not sure exactly how long as I gave up waiting but came back to the terminal later and noticed it had finally completed), but when it finally does this is the relevant output:

Disk /dev/sdc: 33.6 GB, 33554432000 bytes
255 heads, 63 sectors/track, 4079 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4080    32767938    b  W95 FAT32

I'm really at a loss as to why this device is causing this behaviour under Ubuntu but works fine under OS X, any help would be greatly appreciated.

---

### Post by readyrevolver on 2012-03-04
I've also noticed these in syslog:

Mar  5 13:41:05 edge kernel: [ 3823.140332] usb 1-1.2: reset high speed USB device using ehci_hcd and address 15

---

### Post by readyrevolver on 2012-03-04
Just saw this in syslog as well:

Mar  5 13:56:03 edge kernel: [ 4718.890623] usb 1-1.1: reset high speed USB device using ehci_hcd and address 16
Mar  5 13:56:03 edge kernel: [ 4719.084972] sd 14:0:0:0: [sdc] Unhandled error code
Mar  5 13:56:03 edge kernel: [ 4719.084979] sd 14:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Mar  5 13:56:03 edge kernel: [ 4719.084985] sd 14:0:0:0: [sdc] CDB: Read(10): 28 00 03 e7 ff f8 00 00 01 00
Mar  5 13:56:03 edge kernel: [ 4719.084998] end_request: I/O error, dev sdc, sector 65535992
Mar  5 13:56:03 edge kernel: [ 4719.085005] Buffer I/O error on device sdc, logical block 8191999

---

