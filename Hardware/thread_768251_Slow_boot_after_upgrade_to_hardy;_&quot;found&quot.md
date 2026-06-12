---
title: "Slow boot after upgrade to hardy; &quot;found&quot; non-existing harddrive"
date: 2008-04-26
forum: Hardware
---

### Post by lvanderree on 2008-04-26
Hello all,

Since I upgraded my desktop from gutsy to hardy, It takes a long time before my system actually boots. It hangs at the initial-part where you see the indicator circling around (so not yet filling to 100%, but rotating over and over again).

It takes something like 15-30s before the booting actually proceeds. I think because it is looking for a harddrive which doesn't exists (and didn't ever existed either).

in my /var/log/syslog and dmesg I can see this:

```

[   34.998603] sd 7:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   34.998615] sd 7:0:0:0: [sdb] Write Protect is off
[   34.998618] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.998647] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   34.998685] sd 7:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   34.998693] sd 7:0:0:0: [sdb] Write Protect is off
[   34.998694] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.998708] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   34.998710]  sdb:<6>usb 3-2: new low speed USB device using uhci_hcd and address 2
[  125.060471] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060476] end_request: I/O error, dev sdb, sector 0
[  125.060479] Buffer I/O error on device sdb, logical block 0
[  125.060513] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060518] end_request: I/O error, dev sdb, sector 0
[  125.060520] Buffer I/O error on device sdb, logical block 0
[  125.060545] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060548] end_request: I/O error, dev sdb, sector 0
[  125.060551] Buffer I/O error on device sdb, logical block 0
[  125.060570] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060573] end_request: I/O error, dev sdb, sector 0
[  125.060576] Buffer I/O error on device sdb, logical block 0
[  125.060593] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060596] end_request: I/O error, dev sdb, sector 0
[  125.060599] Buffer I/O error on device sdb, logical block 0
[  125.060619] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060623] end_request: I/O error, dev sdb, sector 0
[  125.060625] Buffer I/O error on device sdb, logical block 0
[  125.060642] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060645] end_request: I/O error, dev sdb, sector 0
[  125.060648] Buffer I/O error on device sdb, logical block 0
[  125.060664] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060678] end_request: I/O error, dev sdb, sector 0
[  125.060680] Buffer I/O error on device sdb, logical block 0
[  125.060693] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060696] end_request: I/O error, dev sdb, sector 0
[  125.060697] Buffer I/O error on device sdb, logical block 0
[  125.060702] Dev sdb: unable to read RDB block 0
[  125.060712] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060714] end_request: I/O error, dev sdb, sector 0
[  125.060716] Buffer I/O error on device sdb, logical block 0
[  125.060729] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060732] end_request: I/O error, dev sdb, sector 0
[  125.060748] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060751] end_request: I/O error, dev sdb, sector 24
[  125.060762] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060765] end_request: I/O error, dev sdb, sector 24
[  125.060777] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060779] end_request: I/O error, dev sdb, sector 0
[  125.060792] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.060795] end_request: I/O error, dev sdb, sector 0
[  125.060850] sd 7:0:0:0: [sdb] Attached SCSI disk
[  125.096128] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.096133] end_request: I/O error, dev sdb, sector 0
[  125.096152] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  125.096156] end_request: I/O error, dev sdb, sector 0
[  133.370933] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  133.370938] end_request: I/O error, dev sdb, sector 0
[  133.370942] Buffer I/O error on device sdb, logical block 0
[  133.370957] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  133.370960] end_request: I/O error, dev sdb, sector 0
[  143.631044] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  143.631051] end_request: I/O error, dev sdb, sector 0
[  143.631056] Buffer I/O error on device sdb, logical block 0
[  143.631060] Buffer I/O error on device sdb, logical block 1
[  143.631075] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  143.631080] end_request: I/O error, dev sdb, sector 0
[ 6731.360150] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 6731.360157] end_request: I/O error, dev sdb, sector 0
[ 6731.360162] Buffer I/O error on device sdb, logical block 0
[ 6731.360167] Buffer I/O error on device sdb, logical block 1
[ 6731.360170] Buffer I/O error on device sdb, logical block 2
[ 6731.360173] Buffer I/O error on device sdb, logical block 3
[ 6731.360239] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 6731.360242] end_request: I/O error, dev sdb, sector 0
[ 6731.360245] Buffer I/O error on device sdb, logical block 0

```

But I don't have and sdb-device

The output of cat /proc/scsi/scsi is:
```

Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ASUS     Model: DRW-1608P3S      Rev: 1.24
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3320620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Config  Disk     Rev: RGL1
  Type:   Direct-Access                    ANSI  SCSI revision: 05

```

Where scsi7 is the non-existing drive...

Why does it detect this, and how can I get rid of it?

Any help appreciated

---

### Post by lvanderree on 2008-05-04
Can't anyone tell me where my system can take this information from, of assuming I have another harddrive during boottime?

---

