---
title: "ZIF drive mount error"
date: 2012-09-09
forum: Hardware
---

### Post by killerisation on 2012-09-09
I have a 30Gb zif drive originally from an ipod classic, but more recently from an Acer Aspire One netbook. It ran lubuntu 11.10 (on ext3 i think).

I have bought a ZIF to USB adapter/enclosure like this one [http://youtu.be/7vaMtXwqWXc](http://youtu.be/7vaMtXwqWXc) and am attempting to connect it to my desktop (Mint 13 Maya, 3.2.0-23-generic). It doesnt work. Dmesg has the following output:

[ 6401.320056] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[ 6401.455857] scsi3 : usb-storage 1-6:1.0
[ 6402.456649] scsi 3:0:0:0: Direct-Access     Initio   INIC-1511        1.06 PQ: 0 ANSI: 0
[ 6402.457906] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 6402.496750] sd 3:0:0:0: [sdb] Unit Not Ready
[ 6402.496756] sd 3:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 6402.496763] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 6402.617115] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 6402.617121] sd 3:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 6402.617127] sd 3:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 6402.617134] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 6402.657118] sd 3:0:0:0: [sdb] Write Protect is off
[ 6402.657125] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6402.697146] sd 3:0:0:0: [sdb] Asking for cache data failed
[ 6402.697152] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6402.736840] sd 3:0:0:0: [sdb] Unit Not Ready
[ 6402.736848] sd 3:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 6402.736855] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 6402.972821] sd 3:0:0:0: [sdb] Unit Not Ready
[ 6402.972830] sd 3:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 6402.972840] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 6403.017049] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 6403.017054] sd 3:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 6403.017060] sd 3:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 6403.017067] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 6403.097037] sd 3:0:0:0: [sdb] Asking for cache data failed
[ 6403.097044] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6403.097049] sd 3:0:0:0: [sdb] Attached SCSI removable disk

Any tips on how i can mount it? Is it even possible?
thanks

---

