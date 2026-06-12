---
title: "USB 2.0 LACIE BigDisk SCSI errors"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by manx801 on 2005-10-23
Hello,

I am trying to mount a Lacie 500BG USB 2.0 big disk on my system. So far, I have been unsucessful even when removing ehci and using uhci. What is worse, is that the system will continue to try to mount the disk generating tons of SCSI errors (see below), eventually bringing the system load to 100% and leaving lots of uninterruptable processes. The only fix I have found is to reboot the machine. I am running Ubuntu 5.10 on a Shuttle G2 system. I have no trouble mounting my BUSLINK USB 2.0 disk on the same system. I can also mount the Lacie on other systems running slackware for example. Has anyone experienced this type of problem with Lacie disks on Ubuntu?

Any help would be greatly appreciated!

I get the following output in dmesg after pluging in the disk (note the device index (14) which increments repeating the same errors until I unplug the drive):

[4314802.285000] usb 4-3: new high speed USB device using ehci_hcd and address 14
[4314802.369000] scsi11 : SCSI emulation for USB Mass Storage devices
[4314802.371000] usb-storage: device found at 14
[4314802.371000] usb-storage: waiting for device to settle before scanning
[4314807.371000]   Vendor: LaCie     Model: Big Disk G467     Rev:
[4314807.371000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4314807.374000] SCSI device sdb: 980469503 512-byte hdwr sectors (502000 MB)
[4314807.374000] sdb: assuming drive cache: write through
[4314807.377000] SCSI device sdb: 980469503 512-byte hdwr sectors (502000 MB)
[4314807.377000] sdb: assuming drive cache: write through
[4314807.377000]  /dev/scsi/host11/bus0/target0/lun0: p1
[4314807.385000] Attached scsi disk sdb at scsi11, channel 0, id 0, lun 0
[4314807.398000] usb-storage: device scan complete
[4314807.524000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.524000] end_request: I/O error, dev sdb, sector 0
[4314807.524000] printk: 86 messages suppressed.
[4314807.524000] Buffer I/O error on device sdb, logical block 0
[4314807.525000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.525000] end_request: I/O error, dev sdb, sector 1
[4314807.526000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.526000] end_request: I/O error, dev sdb, sector 2
[4314807.526000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.526000] end_request: I/O error, dev sdb, sector 3
[4314807.526000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.526000] end_request: I/O error, dev sdb, sector 4
[4314807.527000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.527000] end_request: I/O error, dev sdb, sector 5
.
repeats from sector 6 to sector 519
.
[4314807.570000] SCSI error : <11 0 0 0> return code = 0x70000
[4314807.570000] end_request: I/O error, dev sdb, sector 519
[4314807.574000] usb 4-3: USB disconnect, address 14

---

