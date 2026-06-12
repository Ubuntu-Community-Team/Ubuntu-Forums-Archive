---
title: "How to access my SD card slot?"
date: 2009-01-20
forum: Hardware
---

### Post by Peter Bell on 2009-01-20
Please help - I have searched, but cannot find any useful pointers.

I'm running Ubuntu 8.10 on a Shuttle X200.  This has one SD card slot on the front.

If I insert an SD card from my camera into the slot, a "USB Drive" icon appears in my Computer - File Browser window,

If I attempt to mount this drive (Right click -> Mount Volume) nothing appears to happen.  Properties for this drive are empty (Type: unknown type (application/octet-stream, Location: computer:///, everything else is 'unknown')

Double left clicking prompts an 'Unable to mount location' error.

While the card is inserted, lsusb includes the following: 
Bus 005 Device 005: ID 05e3:0712 Genesys Logic, Inc. Delkin Mass Storage Device.

fdisk -l only lists sda1, sda2 and sda5 - Linux. Extended and Linux swap / Solaris respectively.

How do I gain access to the SD card?

The system is, clearly, recognising the hardware, and knows when a card is inserted.  However, I am unable to proceed beyond this.

---

### Post by Peter Bell on 2009-01-21
Okay, a little bit of progress ... I did get the card to mount ... once.

I had been using a USB memory stick in the USB port (this works fine) then, while the stick was mounted, I reinserted the SD card and was surprised to find that it suddenly popped on the desktop.  However, I have been unable to repeat this! :(

So, I looked at DMESG, and see the following:

> [413548.088043] usb 5-4: new high speed USB device using ehci_hcd and address 17
[413548.225327] usb 5-4: configuration #1 chosen from 1 choice
[413548.226520] scsi19 : SCSI emulation for USB Mass Storage devices
[413548.229285] usb-storage: device found at 17
[413548.229301] usb-storage: waiting for device to settle before scanning
[413553.228735] usb-storage: device scan complete
[413553.231734] scsi 19:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9230 PQ: 0 ANSI: 0
[413553.324428] sd 19:0:0:0: [sdc] 1006592 512-byte hardware sectors (515 MB)
[413553.326631] sd 19:0:0:0: [sdc] Write Protect is off
[413553.326647] sd 19:0:0:0: [sdc] Mode Sense: 03 00 00 00
[413553.326654] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[413553.331288] sd 19:0:0:0: [sdc] 1006592 512-byte hardware sectors (515 MB)
[413553.334661] sd 19:0:0:0: [sdc] Write Protect is off
[413553.334674] sd 19:0:0:0: [sdc] Mode Sense: 03 00 00 00
[413553.334680] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[413553.339195]  sdc:<6>sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413554.669902] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413554.669921] end_request: I/O error, dev sdc, sector 0
[413554.669932] __ratelimit: 1 callbacks suppressed
[413554.669939] Buffer I/O error on device sdc, logical block 0
[413554.671747] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413554.671758] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413554.671773] end_request: I/O error, dev sdc, sector 0
[413554.671780] Buffer I/O error on device sdc, logical block 0
[413554.673754] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413554.673766] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413554.673777] end_request: I/O error, dev sdc, sector 0
[413554.673785] Buffer I/O error on device sdc, logical block 0
[413554.678257] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413554.678275] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413554.678287] end_request: I/O error, dev sdc, sector 0
[413554.678296] Buffer I/O error on device sdc, logical block 0
[413556.083242] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.083263] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.083280] end_request: I/O error, dev sdc, sector 0
[413556.083291] Buffer I/O error on device sdc, logical block 0
[413556.083331] ldm_validate_partition_table(): Disk read failed.
[413556.085221] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.085235] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.085246] end_request: I/O error, dev sdc, sector 0
[413556.085257] Buffer I/O error on device sdc, logical block 0
[413556.087219] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.087231] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.087245] end_request: I/O error, dev sdc, sector 0
[413556.087252] Buffer I/O error on device sdc, logical block 0
[413556.089221] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.089236] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.089247] end_request: I/O error, dev sdc, sector 0
[413556.089258] Buffer I/O error on device sdc, logical block 0
[413556.091219] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.091231] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.091242] end_request: I/O error, dev sdc, sector 0
[413556.091250] Buffer I/O error on device sdc, logical block 0
[413556.091274] Dev sdc: unable to read RDB block 0
[413556.093219] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.093233] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.093244] end_request: I/O error, dev sdc, sector 0
[413556.093255] Buffer I/O error on device sdc, logical block 0
[413556.095094] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.095108] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.095120] end_request: I/O error, dev sdc, sector 0
[413556.097094] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.097107] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.097118] end_request: I/O error, dev sdc, sector 24
[413556.099093] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.099106] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.099117] end_request: I/O error, dev sdc, sector 24
[413556.101093] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.101104] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.101119] end_request: I/O error, dev sdc, sector 0
[413556.103092] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413556.103106] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413556.103117] end_request: I/O error, dev sdc, sector 0
[413556.103143]  unable to read partition table
[413556.103351] sd 19:0:0:0: [sdc] Attached SCSI removable disk
[413556.103577] sd 19:0:0:0: Attached scsi generic sg3 type 0
[413557.513826] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413557.513847] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413557.513860] end_request: I/O error, dev sdc, sector 0
[413557.515816] sd 19:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[413557.515828] sd 19:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[413557.515840] end_request: I/O error, dev sdc, sector 0


Does this help to identify the problem, or point to a fix?

Why should the device work once, and then not again?

---

