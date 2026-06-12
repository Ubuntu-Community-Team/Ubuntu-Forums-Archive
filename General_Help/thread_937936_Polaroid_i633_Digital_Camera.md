---
title: "Polaroid i633 Digital Camera"
date: 2008-10-04
forum: General Help
---

### Post by cristianrosa on 2008-10-04
Hello, I have a Polaroid i633 camera and I can't get working the Mass Storage mode. I get the following error in dmesg
```

[  796.601079] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  909.695850] usb 1-1: configuration #1 chosen from 1 choice
[ 1274.581604] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1274.589146] usb-storage: device found at 7
[ 1274.589151] usb-storage: waiting for device to settle before scanning
[ 2130.710285] usb-storage: device scan complete
[ 2130.713296] scsi 3:0:0:0: Direct-Access     Digital  Camera   6MP-9FW 1.00 PQ: 0 ANSI: 2
[ 2130.731243] sd 3:0:0:0: [sdb] 1939456 512-byte hardware sectors (993 MB)
[ 2130.734234] sd 3:0:0:0: [sdb] Write Protect is off
[ 2130.734245] sd 3:0:0:0: [sdb] Mode Sense: 1f 00 00 08
[ 2130.734252] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2130.743232] sd 3:0:0:0: [sdb] 1939456 512-byte hardware sectors (993 MB)
[ 2130.746324] sd 3:0:0:0: [sdb] Write Protect is off
[ 2130.746334] sd 3:0:0:0: [sdb] Mode Sense: 1f 00 00 08
[ 2130.746341] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2130.746351]  sdb: sdb1
[ 2130.757314] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 2130.757411] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 2165.822118] usb 1-1: reset full speed USB device using uhci_hcd and address 7
[  816.297359] usb 1-1: reset full speed USB device using uhci_hcd and address 7
[ 2177.156759] usb 1-1: reset full speed USB device using uhci_hcd and address 7
[ 2187.815619] usb 1-1: reset full speed USB device using uhci_hcd and address 7
[ 2187.967364] sd 3:0:0:0: Device offlined - not ready after error recovery
[ 2187.967386] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2187.967398] end_request: I/O error, dev sdb, sector 1939444
[ 2187.967408] Buffer I/O error on device sdb1, logical block 1939217
[ 2187.967421] Buffer I/O error on device sdb1, logical block 1939218
[ 2187.967430] Buffer I/O error on device sdb1, logical block 1939219
[ 2187.967439] Buffer I/O error on device sdb1, logical block 1939220
[ 2187.967447] Buffer I/O error on device sdb1, logical block 1939221
[ 2187.967456] Buffer I/O error on device sdb1, logical block 1939222
[ 2187.967465] Buffer I/O error on device sdb1, logical block 1939223
[ 2187.967486] sd 3:0:0:0: rejecting I/O to offline device
[ 2187.967543] sd 3:0:0:0: rejecting I/O to offline device
[ 2187.967551] Buffer I/O error on device sdb1, logical block 1939217
[ 2187.967559] Buffer I/O error on device sdb1, logical block 1939218
[ 2187.967567] Buffer I/O error on device sdb1, logical block 1939219
[ 2187.967728] sd 3:0:0:0: rejecting I/O to offline device
[ 2187.967744] sd 3:0:0:0: rejecting I/O to offline device
...

```

If I set the camera to use the PictBridge USB mode then I can only import the pictures (through libgphoto2). It seems that the camera in this mode doesn't show the video files.

Any suggestion on how to download the videos?
Thanks!

---

### Post by phorim on 2008-10-04
You could get a cheap SD memory card reader.  I got one and never plug in the camera directly anymore.

---

