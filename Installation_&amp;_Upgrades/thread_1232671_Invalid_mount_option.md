---
title: "Invalid mount option"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by deez on 2009-08-05
Hello Ubuntu Community, 

I just upgraded to 9.04.  My camera won't auto mount.  I can manually mount it fine.  I've already searched looking for my answer but none of the remedies work.  I've tried editing /etc/fstab as well as removing the 'usefree' option in gconf, but that wasn't even there. The error message is:

Cannont mount volume.  Invalid mount option when attempting to mount the volume.  


Any ideas?

Thanks

Deez

---

### Post by merlinus on 2009-08-05
Check settings in System/Preferences/Removable Drives and Media.

---

### Post by lensman3 on 2009-08-06
Just after it fails to mount do a "dmesg" from a command line and see if the last 10 lines or so gives a hint.  dmesg will spite out the kernel errors.

---

### Post by deez on 2009-08-06
Merlin, 

Checking Removable Drives and Media doesn't change anything.  

Here is the output from dmesg:

[ 1285.171346] Initializing USB Mass Storage driver...
[ 1285.174506] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1285.175049] usbcore: registered new interface driver usb-storage
[ 1285.175061] USB Mass Storage support registered.
[ 1285.231237] usb-storage: device found at 4
[ 1285.231247] usb-storage: waiting for device to settle before scanning
[ 1290.229282] usb-storage: device scan complete
[ 1290.231613] scsi 2:0:0:0: Direct-Access     Samsung  Digital Camera        PQ: 0 ANSI: 0 CCS
[ 1290.278022] sd 2:0:0:0: [sdb] 999936 512-byte hardware sectors: (511 MB/488 MiB)
[ 1290.281440] sd 2:0:0:0: [sdb] Write Protect is off
[ 1290.281450] sd 2:0:0:0: [sdb] Mode Sense: 00 06 00 00
[ 1290.281458] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1290.291174] sd 2:0:0:0: [sdb] 999936 512-byte hardware sectors: (511 MB/488 MiB)
[ 1290.292662] sd 2:0:0:0: [sdb] Write Protect is off
[ 1290.292671] sd 2:0:0:0: [sdb] Mode Sense: 00 06 00 00
[ 1290.292679] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1290.292692]  sdb: sdb1
[ 1290.297278] sdb: p1 size 1000215 limited to end of disk
[ 1290.297640] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1290.297854] sd 2:0:0:0: Attached scsi generic sg1 type 0


Thanks

---

