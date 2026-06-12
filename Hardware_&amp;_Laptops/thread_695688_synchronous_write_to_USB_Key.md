---
title: "synchronous write to USB Key"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by chatelp on 2008-02-13
Hi,

I just bought this new 2Gb USB key and it seems I can't copy small files to it from my xubuntu install. Files are copied on the automounted key, but it seems the write buffers are not emptied before unmount.

I tried the 'sync' command before unmounting the key but small files are still corrupted.

Strange thing is that I didn't observed this behaviour on my smaller 1Gb key ! I'm also sure the key is not broken since it works OK with OSX and Windows.

Do you know how to force synchronous write on all automounted storage peripherals by default and also, did some of you observed the same behaviour with xubuntu installs ?

Thanks,
Pierre

---

### Post by magicfab on 2008-02-13
Normally right clicking and choosing "unmount" should prevent this.

Not sure about forcing sync, however.

Can you post the last few lines of dmesg after you remove the key ?

---

### Post by chatelp on 2008-02-13
[ 4170.824000] usb 5-2: new high speed USB device using ehci_hcd and address 10
[ 4170.956000] usb 5-2: configuration #1 chosen from 1 choice
[ 4170.956000] scsi9 : SCSI emulation for USB Mass Storage devices
[ 4170.956000] usb-storage: device found at 10
[ 4170.956000] usb-storage: waiting for device to settle before scanning
[ 4175.956000] usb-storage: device scan complete
[ 4175.956000] scsi 9:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
[ 4175.960000] sd 9:0:0:0: [sdd] 3963904 512-byte hardware sectors (2030 MB)
[ 4175.960000] sd 9:0:0:0: [sdd] Write Protect is off
[ 4175.960000] sd 9:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 4175.960000] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 4175.964000] sd 9:0:0:0: [sdd] 3963904 512-byte hardware sectors (2030 MB)
[ 4175.964000] sd 9:0:0:0: [sdd] Write Protect is off
[ 4175.964000] sd 9:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 4175.964000] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 4175.964000]  sdd: sdd1
[ 4176.028000] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 4176.028000] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 4205.788000] usb 5-2: USB disconnect, address 10

This last line only appeared after I removed the key from the USB port.

Everything seems to indicate a hardware problem with this specific key since I can't observe this problem on my smaller 1Gb USB key with Xubuntu BUT, and that is the strange part, I have no problem whatsoever using the 2Gb key under OSX !

---

