---
title: "Buffer I/O error on removable USB prevents normal system startup"
date: 2008-08-04
forum: General Help
---

### Post by gkaragoulis on 2008-08-04
I would appreciate help on this one, I've been searching around and I can't find anything like it on Google.

At work we have this very important server with a USB external hard drive attached to it.  Whenever we restart the server it stops during the startup process with a few buffer i/o errors and prompts the user to press "Ctrl-D to continue".  When that is pressed and the server starts I can't find anything wrong with the device; fsck says it's clean and all the files are there and accessible.  The big problem is the server not starting up by itself, which can be very bad if it happens on a weekend and nobody is there to press "ctrl-D" for it.  Is there any way to either fix the device, or force Ubuntu to ignore the buffer i/o errors and start anyways?  Thank you for any help you can give me!

dmesg Relevant output:
```
[   97.825453] usb-storage: device scan complete
[   97.825939] scsi 3:0:0:0: Direct-Access     External AL25744_12345678      PQ: 0 ANSI: 2
[   97.827179] sd 3:0:0:0: [sdg] 3907050337 512-byte hardware sectors (2000410 MB)
[   97.827673] sd 3:0:0:0: [sdg] Write Protect is off
[   97.827674] sd 3:0:0:0: [sdg] Mode Sense: 1a 0c 00 00
[   97.827676] sd 3:0:0:0: [sdg] Assuming drive cache: write through
[   97.828794] sd 3:0:0:0: [sdg] 3907050337 512-byte hardware sectors (2000410 MB)
[   97.829297] sd 3:0:0:0: [sdg] Write Protect is off
[   97.829304] sd 3:0:0:0: [sdg] Mode Sense: 1a 0c 00 00
[   97.829305] sd 3:0:0:0: [sdg] Assuming drive cache: write through
[   97.829362]  sdg: sdg1
[   97.829995] sd 3:0:0:0: [sdg] Attached SCSI disk
[   97.830022] sd 3:0:0:0: Attached scsi generic sg8 type 0
[   97.877014] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.877018] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.877021] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.877025] end_request: I/O error, dev sdg, sector 3907050336
[   97.877028] Buffer I/O error on device sdg, logical block 3907050336
[   97.883884] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.883890] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.883893] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.883897] end_request: I/O error, dev sdg, sector 3907050336
[   97.883901] Buffer I/O error on device sdg, logical block 3907050336
[   97.891755] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.891758] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.891761] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.891765] end_request: I/O error, dev sdg, sector 3907050336
[   97.891767] Buffer I/O error on device sdg, logical block 3907050336
[   97.898628] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.898632] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.898635] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.898639] end_request: I/O error, dev sdg, sector 3907050336
[   97.898641] Buffer I/O error on device sdg, logical block 3907050336
[   97.905500] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.905503] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.905505] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.905508] end_request: I/O error, dev sdg, sector 3907050336
[   97.905511] Buffer I/O error on device sdg, logical block 3907050336
[   97.915365] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.915368] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.915370] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.915374] end_request: I/O error, dev sdg, sector 3907050336
[   97.915376] Buffer I/O error on device sdg, logical block 3907050336
[   97.922236] sd 3:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   97.922238] sd 3:0:0:0: [sdg] Sense Key : Aborted Command [current] 
[   97.922241] sd 3:0:0:0: [sdg] Add. Sense: No additional sense information
[   97.922244] end_request: I/O error, dev sdg, sector 3907050336
[   97.922246] Buffer I/O error on device sdg, logical block 3907050336
[   97.943983] VFS: Can't find ext3 filesystem on dev sdg.
[   98.017979] kjournald starting.  Commit interval 5 seconds
[   98.025829] EXT3 FS on sdg1, internal journal
[   98.025835] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by gkaragoulis on 2008-08-05
I think I figured this one out on my own:

In my fstab I was telling it to check the fs on my external drive.  It was throwing legitimate errors, my only problem was checking it on startup.  In case anyone is wondering, that's what the last number on each line of the fstab does!

---

