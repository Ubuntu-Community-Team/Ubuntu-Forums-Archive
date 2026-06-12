---
title: "Ipod not working"
date: 2008-11-03
forum: General Help
---

### Post by buttari on 2008-11-03
Hello,
my ipod is not working with my Dell D630 laptop. When connect the ipod to the usb port, the ipod icon shows up on the desktop, rhythmbox is started but the ipod appears empty even when it's not. This is what I found in /var/log/messages:

```

Oct 27 08:48:58 attila kernel: [  803.787055] usb 7-2: new high speed USB device using ehci_hcd and address 12
Oct 27 08:48:58 attila kernel: [  803.921187] usb 7-2: configuration #1 chosen from 2 choices
Oct 27 08:48:58 attila kernel: [  804.029857] usbcore: registered new interface driver libusual
Oct 27 08:48:58 attila kernel: [  804.040082] Initializing USB Mass Storage driver...
Oct 27 08:48:58 attila kernel: [  804.041167] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 27 08:48:58 attila kernel: [  804.041793] usbcore: registered new interface driver usb-storage
Oct 27 08:48:58 attila kernel: [  804.041795] USB Mass Storage support registered.
Oct 27 08:49:03 attila kernel: [  809.031985] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Oct 27 08:49:03 attila kernel: [  809.035943] sd 4:0:0:0: [sdb] 7999487 512-byte hardware sectors (4096 MB)
Oct 27 08:49:03 attila kernel: [  809.037440] sd 4:0:0:0: [sdb] Write Protect is off
Oct 27 08:49:03 attila kernel: [  809.039934] sd 4:0:0:0: [sdb] 7999487 512-byte hardware sectors (4096 MB)
Oct 27 08:49:03 attila kernel: [  809.041059] sd 4:0:0:0: [sdb] Write Protect is off
Oct 27 08:49:03 attila kernel: [  809.041077]  sdb: sdb1 sdb2
Oct 27 08:49:03 attila kernel: [  809.045266] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Oct 27 08:49:03 attila kernel: [  809.045339] sd 4:0:0:0: Attached scsi generic sg2 type 0
Oct 27 08:49:04 attila kernel: [  809.927763] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  809.927771] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
Oct 27 08:49:04 attila kernel: [  809.927777] Info fld=0x0
Oct 27 08:49:04 attila kernel: [  809.927779] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
Oct 27 08:49:04 attila kernel: [  809.927785] end_request: I/O error, dev sdb, sector 175960
Oct 27 08:49:04 attila kernel: [  809.927793] lost page write due to I/O error on sdb2
Oct 27 08:49:04 attila kernel: [  809.936875] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  809.936882] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
Oct 27 08:49:04 attila kernel: [  809.936887] Info fld=0x0
Oct 27 08:49:04 attila kernel: [  809.936889] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
Oct 27 08:49:04 attila kernel: [  809.936895] end_request: I/O error, dev sdb, sector 175976
Oct 27 08:49:04 attila kernel: [  809.936903] lost page write due to I/O error on sdb2
Oct 27 08:49:04 attila kernel: [  809.936910] lost page write due to I/O error on sdb2
Oct 27 08:49:04 attila kernel: [  810.054820] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  810.054830] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
Oct 27 08:49:04 attila kernel: [  810.054836] Info fld=0x0
Oct 27 08:49:04 attila kernel: [  810.054837] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
Oct 27 08:49:04 attila kernel: [  810.054844] end_request: I/O error, dev sdb, sector 175952
Oct 27 08:49:04 attila kernel: [  810.063805] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  810.063812] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
Oct 27 08:49:04 attila kernel: [  810.063816] Info fld=0x0
Oct 27 08:49:04 attila kernel: [  810.063818] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
Oct 27 08:49:04 attila kernel: [  810.063824] end_request: I/O error, dev sdb, sector 175953
Oct 27 08:49:04 attila kernel: [  810.072926] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  810.072932] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
Oct 27 08:49:04 attila kernel: [  810.072937] Info fld=0x0
Oct 27 08:49:04 attila kernel: [  810.072938] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
Oct 27 08:49:04 attila kernel: [  810.072944] end_request: I/O error, dev sdb, sector 175952
Oct 27 08:49:04 attila kernel: [  810.082250] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 27 08:49:04 attila kernel: [  810.082260] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 

```

I used to have this problem with Hardy and I still have it in ibex.

Does anybody know how to solve this problem? Should I file a bug report?

Thanks in advance

Alfredo

---

### Post by buttari on 2008-11-05
bump...nothing?

---

### Post by 454abp on 2008-11-07
Hi, 

I have already filed the error as a bug: [https://bugs.launchpad.net/ubuntu/+bug/294391](https://bugs.launchpad.net/ubuntu/+bug/294391)

/454abp

---

### Post by buttari on 2008-11-07
> **454abp said:**
> Hi, 

I have already filed the error as a bug: [https://bugs.launchpad.net/ubuntu/+bug/294391](https://bugs.launchpad.net/ubuntu/+bug/294391)

/454abp

Hello,
well thank you very much for pointing this out. I actually managed to solve the problem by restoring the ipod using itunes under windows. 

Alfredo

---

### Post by PCessna on 2008-11-07
iPods are not for Linux. I hope you can get a solution to this problem, but  they are only labled compatible for Microsoft Windows XP, Vista, Mac OS X 10.3 or 4+

---

