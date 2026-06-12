---
title: "USB stick mounting problem after hardy upgrade"
date: 2008-09-06
forum: Hardware
---

### Post by c-shadow on 2008-09-06
After upgedading to hardy, my usb sticks and other storage devices only automount the first time after a clean boot. Right clicking on the icon on desktop and chossing unmount does that, but 'Places' menu still retains the entries...picture attached
dmesg and syslog look clean, no errors:
```

[ 6034.284612] usb 2-10: new high speed USB device using ehci_hcd and address 8
[ 6034.361048] usb 2-10: configuration #1 chosen from 1 choice
[ 6034.353336] scsi9 : SCSI emulation for USB Mass Storage devices
[ 6034.353988] usb-storage: device found at 8
[ 6034.353992] usb-storage: waiting for device to settle before scanning
[ 6036.859445] usb-storage: device scan complete
[ 6036.852029] scsi 9:0:0:0: Direct-Access     OTi      Flash Disk       2.00 PQ: 0 ANSI: 2
[ 6037.382508] ready
[ 6037.382817] sd 9:0:0:0: [sdd] 256000 512-byte hardware sectors (131 MB)
[ 6037.383189] sd 9:0:0:0: [sdd] Write Protect is off
[ 6037.383192] sd 9:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 6037.383194] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 6037.384688] sd 9:0:0:0: [sdd] 256000 512-byte hardware sectors (131 MB)
[ 6037.385000] sd 9:0:0:0: [sdd] Write Protect is off
[ 6037.385003] sd 9:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 6037.385005] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 6037.385010]  sdd: sdd1
[ 6037.385590] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 6037.385625] sd 9:0:0:0: Attached scsi generic sg4 type 0
[ 6048.368695] usb 2-10: USB disconnect, address 8

```
I can still mount manually. Clicking on an entry in 'Places' menu also mounts it in the /media folder, usually /media/disk. 
Already looked in lauchpad bugs #224085 and #211760 and no help since I don't get any errors mentioned there and gconf has no usefree entry. formatting usb sticks (FAT16,FAT32,ext2/3) doesn't affect the problem.

---

