---
title: "Sometimes USB flash drive does not get mounted"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by akwatve on 2008-01-28
At times my USB pendrive does not get mounted in KDE. I am using kubuntu 7.10
The problem is not replicable all the time. It happens randomly. I checked and verified kde daemon does run all the time ... but sometimes it just doesnt like my pen drive. This is frustrating becoz if i manually mount my pendrive using "mount /dev/sdb /media/disk" only root gets write access which is highly undesirble. I know there are quite a few posts similar to this but none answered my question,,, Why does my comp sometimes accepts the USB drive but sometimes refuses it ?

*EDIT* I have acer aspire 5052 with AMD Turion 64x2 with 64 bit kubuntu gutsy


Thanks

---

### Post by jeffus_il on 2008-01-28
Next time it refuses it, open a terminal and type > dmesg and post the output, the last 10 or 20 lines should be enough.

---

### Post by akwatve on 2008-01-29
Thanks,
I will surely do that... For now it seems to be working.
Next time when my comp stops recognizing it, I will post output of dmesg

P.S.
I have observed the same behaviour on two different machines. One is my laptop and other is my desktop (which has 32 bit kubuntu gutsy)

---

### Post by Yellow Pasque on 2008-01-29
Next time you have to mount manually, specify options to get access for regular users, e.g.:
```
sudo mount -o rw,auto,user,exec,uid=1000  /dev/sdb1  /media/disk
```

---

### Post by akwatve on 2008-01-29
Thanks Temüjin, I Will keep that in mind...

meanwhile, I faced the same problem on my desktop (though my laptop did mount it properly)....
Jeffus_il, below are the last 20 lines of dmesg :

> 
dmesg | tail -20
[95232.399257] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[95232.405644] Initializing USB Mass Storage driver...
[95232.406301] scsi2 : SCSI emulation for USB Mass Storage devices
[95232.406960] usb-storage: device found at 2
[95232.406965] usb-storage: waiting for device to settle before scanning
[95232.407213] usbcore: registered new interface driver usb-storage
[95232.407341] USB Mass Storage support registered.
[95237.404909] usb-storage: device scan complete
[95237.407923] scsi 2:0:0:0: Direct-Access     JetFlash TS1GJF2A/120     8.07 PQ: 0 ANSI: 2
[95237.417883] sd 2:0:0:0: [sdc] 2047998 512-byte hardware sectors (1049 MB)
[95237.420884] sd 2:0:0:0: [sdc] Write Protect is off
[95237.420889] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[95237.420892] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[95237.431887] sd 2:0:0:0: [sdc] 2047998 512-byte hardware sectors (1049 MB)
[95237.434878] sd 2:0:0:0: [sdc] Write Protect is off
[95237.434883] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[95237.434886] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[95237.434891]  sdc: sdc1
[95237.440978] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[95237.441031] sd 2:0:0:0: Attached scsi generic sg3 type 0


Thanks

---

### Post by akwatve on 2008-01-30
This just happened again for my laptop :-(

Here is the dmesg output

> [ 1437.605402] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 1493.406630] usb 3-5: USB disconnect, address 3
[ 1500.582402] usb 3-1: new high speed USB device using ehci_hcd and address 4
[ 1500.719021] usb 3-1: configuration #1 chosen from 1 choice
[ 1500.719375] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1500.719655] usb-storage: device found at 4
[ 1500.719658] usb-storage: waiting for device to settle before scanning
[ 1505.710818] usb-storage: device scan complete
[ 1505.711800] scsi 3:0:0:0: Direct-Access     JetFlash TS1GJF2A/120     8.07 PQ: 0 ANSI: 2
[ 1505.714569] sd 3:0:0:0: [sdb] 2047998 512-byte hardware sectors (1049 MB)
[ 1505.715403] sd 3:0:0:0: [sdb] Write Protect is off
[ 1505.715407] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1505.715417] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1505.717628] sd 3:0:0:0: [sdb] 2047998 512-byte hardware sectors (1049 MB)
[ 1505.718251] sd 3:0:0:0: [sdb] Write Protect is off
[ 1505.718255] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1505.718265] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1505.718270]  sdb: sdb1
[ 1505.719148] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1505.719227] sd 3:0:0:0: Attached scsi generic sg1 type 0


---

