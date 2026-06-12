---
title: "USB Hard drive &quot;Add. Sense: No additional sense information&quot;"
date: 2009-07-12
forum: Hardware
---

### Post by Savvy84 on 2009-07-12
Hi Everyone,

First post here and I have searched through the forum and can't find an answer to this question.

I have an old 2.5 ide disk from a friend that he wanted me to get the files off of as it was failing but I have put it into my usb caddy and Ubuntu will not load a dev file.

Here is the dmesg output

```

10760.940063] usb 1-2: new high speed USB device using ehci_hcd and address 5
[10761.074707] usb 1-2: configuration #1 chosen from 1 choice
[10761.089694] scsi9 : SCSI emulation for USB Mass Storage devices
[10761.094601] usb-storage: device found at 5
[10761.094608] usb-storage: waiting for device to settle before scanning

```Then cycles over this

```

[10772.032262] sd 9:0:0:0: [sdb] Add. Sense: No additional sense information
[10772.038251] sd 9:0:0:0: [sdb] Sense Key : No Sense [current] 
[10772.038258] Info fld=0x0

```Until I disconnect the drive

```

[10772.096061] usb 1-2: USB disconnect, address 5
[10772.096516] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.096526] end_request: I/O error, dev sdb, sector 0
[10772.096537] __ratelimit: 5 callbacks suppressed
[10772.096544] Buffer I/O error on device sdb, logical block 0
[10772.100902] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.100918] end_request: I/O error, dev sdb, sector 0
[10772.100929] Buffer I/O error on device sdb, logical block 0
[10772.101000] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101008] end_request: I/O error, dev sdb, sector 0
[10772.101013] Buffer I/O error on device sdb, logical block 0
[10772.101054] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101062] end_request: I/O error, dev sdb, sector 0
[10772.101067] Buffer I/O error on device sdb, logical block 0
[10772.101105] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101112] end_request: I/O error, dev sdb, sector 0
[10772.101116] Buffer I/O error on device sdb, logical block 0
[10772.101134] ldm_validate_partition_table(): Disk read failed.
[10772.101159] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101166] end_request: I/O error, dev sdb, sector 0
[10772.101171] Buffer I/O error on device sdb, logical block 0
[10772.101205] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101212] end_request: I/O error, dev sdb, sector 0
[10772.101217] Buffer I/O error on device sdb, logical block 0
[10772.101252] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101259] end_request: I/O error, dev sdb, sector 0
[10772.101263] Buffer I/O error on device sdb, logical block 0
[10772.101297] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101304] end_request: I/O error, dev sdb, sector 0
[10772.101309] Buffer I/O error on device sdb, logical block 0
[10772.101326] Dev sdb: unable to read RDB block 0
[10772.101350] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101358] end_request: I/O error, dev sdb, sector 0
[10772.101362] Buffer I/O error on device sdb, logical block 0
[10772.101399] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101406] end_request: I/O error, dev sdb, sector 0
[10772.101467] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101475] end_request: I/O error, dev sdb, sector 24
[10772.101508] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101516] end_request: I/O error, dev sdb, sector 24
[10772.101551] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101558] end_request: I/O error, dev sdb, sector 0
[10772.101594] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10772.101601] end_request: I/O error, dev sdb, sector 0
[10772.101616]  unable to read partition table
[10772.101905] sd 9:0:0:0: [sdb] Attached SCSI disk
[10772.102092] sd 9:0:0:0: Attached scsi generic sg2 type 0

```Once I can get device file I'll use ddrecover to get an image.

Any help would be great.

Thanks,

Savvy

---

### Post by Savvy84 on 2009-07-13
Bump.

---

### Post by Savvy84 on 2009-07-13
Bump ............ please :(

---

### Post by mek1 on 2009-08-09
Bump, I am also having this problem with 4GB Gizmo drive.

---

### Post by freephile on 2009-08-15
bump - same here with Western Digital WD Scorpio WD1600BEVE-OOUYTO Enhanced IDE 2.5" notebook drive

I've been trying to rescue it with ddrescue (that's gddrescue on Ubuntu) but the system is having no luck reading the device.

---

