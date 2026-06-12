---
title: "Trouble mounting iriver device"
date: 2008-10-11
forum: General Help
---

### Post by gausie on 2008-10-11
Hi all

I'm plugging in the device in emergency connect mode and I get this from dmesg:

> [  674.046593] usb 7-4: new high speed USB device using ehci_hcd and address 15
[  674.182082] usb 7-4: configuration #1 chosen from 1 choice
[  674.199480] scsi18 : SCSI emulation for USB Mass Storage devices
[  674.199810] usb-storage: device found at 15
[  674.199813] usb-storage: waiting for device to settle before scanning
[  676.323791] usb-storage: device scan complete
[  676.324270] scsi 18:0:0:0: Direct-Access     iriver   iriver H10            PQ: 0 ANSI: 0
[  676.326129] sd 18:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[  676.326133] sd 18:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[  676.327005] sd 18:0:0:0: [sdb] Write Protect is off
[  676.327008] sd 18:0:0:0: [sdb] Mode Sense: 45 00 00 00
[  676.327011] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[  676.385748] sd 18:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[  676.385756] sd 18:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[  676.386742] sd 18:0:0:0: [sdb] Write Protect is off
[  676.386747] sd 18:0:0:0: [sdb] Mode Sense: 45 00 00 00
[  676.386750] sd 18:0:0:0: [sdb] Assuming drive cache: write through

But I can't find the device anywhere in /dev/, and it hasn't mounted as expected.

Any ideas?

Gausie

---

### Post by Julius1988 on 2008-10-11
check this link they have discussed this issue.
```

http://ubuntuforums.org/showthread.php?t=105944

```

---

### Post by gausie on 2008-10-11
Thanks, but I found earlier that that doesn't apply to my device. I have the H10, and ifp is for the iFP series. I tried that program but it could not detect my device.

Do you have any other suggestions?

Gausie

---

