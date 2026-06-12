---
title: "lucid won't mount sd card"
date: 2010-06-02
forum: Hardware
---

### Post by b0b138 on 2010-06-02
I've got a simple card reader that plugs into a usb port but it won't mount my sd cards. Worked fine in karmic.  Heres some info from the logs

```
Jun  2 14:43:32 neo kernel: [   26.907035] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jun  2 14:43:32 neo kernel: [   27.068583] usb 1-4: configuration #1 chosen from 1 choice
Jun  2 14:43:32 neo kernel: [   27.074294] Initializing USB Mass Storage driver...
Jun  2 14:43:32 neo kernel: [   27.074385] scsi7 : SCSI emulation for USB Mass Storage devices
Jun  2 14:43:32 neo kernel: [   27.074451] usbcore: registered new interface driver usb-storage
Jun  2 14:43:32 neo kernel: [   27.074452] USB Mass Storage support registered.
Jun  2 14:43:37 neo kernel: [   32.058184] scsi 7:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
Jun  2 14:43:37 neo kernel: [   32.058451] sd 7:0:0:0: Attached scsi generic sg3 type 0
Jun  2 14:44:08 neo kernel: [   62.933679] usb 1-4: USB disconnect, address 3
Jun  2 14:44:08 neo kernel: [   62.933687] sd 7:0:0:0: Device offlined - not ready after error recovery
Jun  2 14:44:08 neo kernel: [   62.933713] sd 7:0:0:0: [sdc] READ CAPACITY failed
Jun  2 14:44:08 neo kernel: [   62.933715] sd 7:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  2 14:44:08 neo kernel: [   62.933717] sd 7:0:0:0: [sdc] Sense not available.
Jun  2 14:44:08 neo kernel: [   62.933723] sd 7:0:0:0: [sdc] Write Protect is off
Jun  2 14:44:08 neo kernel: [   62.933843] sd 7:0:0:0: [sdc] READ CAPACITY failed
Jun  2 14:44:08 neo kernel: [   62.933844] sd 7:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  2 14:44:08 neo kernel: [   62.933846] sd 7:0:0:0: [sdc] Sense not available.
Jun  2 14:44:08 neo kernel: [   62.933855] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jun  2 14:44:09 neo kernel: [   63.272699] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jun  2 14:44:09 neo kernel: [   63.434170] usb 1-4: configuration #1 chosen from 1 choice
Jun  2 14:44:09 neo kernel: [   63.434807] scsi8 : SCSI emulation for USB Mass Storage devices
Jun  2 14:44:14 neo kernel: [   68.551907] usb 1-4: reset high speed USB device using ehci_hcd and address 4
Jun  2 14:44:14 neo kernel: [   68.710292] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
Jun  2 14:44:14 neo kernel: [   68.710704] sd 8:0:0:0: Attached scsi generic sg3 type 0
Jun  2 14:44:44 neo kernel: [   98.919838] usb 1-4: reset high speed USB device using ehci_hcd and address 4
Jun  2 14:44:47 neo kernel: [  101.151618] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Jun  2 14:45:35 neo kernel: [  116.993939] sd 8:0:0:0: [sdc] Spinning up disk....
Jun  2 14:45:35 neo kernel: [  148.997476] usb 1-4: reset high speed USB device using ehci_hcd and address 4
Jun  2 14:45:45 neo kernel: [  159.246522] usb 1-4: reset high speed USB device using ehci_hcd and address 4
Jun  2 14:45:45 neo kernel: [  159.316697] usb 1-4: USB disconnect, address 4
Jun  2 14:45:45 neo kernel: [  159.316701] sd 8:0:0:0: Device offlined - not ready after error recovery
Jun  2 14:45:45 neo kernel: [  159.316714] ready
Jun  2 14:45:45 neo kernel: [  159.316742] sd 8:0:0:0: [sdc] READ CAPACITY failed
Jun  2 14:45:45 neo kernel: [  159.316744] sd 8:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  2 14:45:45 neo kernel: [  159.316748] sd 8:0:0:0: [sdc] Sense not available.
Jun  2 14:45:45 neo kernel: [  159.535937] usb 1-4: new high speed USB device using ehci_hcd and address 5
Jun  2 14:45:45 neo kernel: [  159.697535] usb 1-4: configuration #1 chosen from 1 choice
Jun  2 14:45:45 neo kernel: [  159.698212] scsi9 : SCSI emulation for USB Mass Storage devices
Jun  2 14:45:50 neo kernel: [  164.689993] scsi 9:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
Jun  2 14:45:50 neo kernel: [  164.690535] sd 9:0:0:0: Attached scsi generic sg3 type 0
Jun  2 14:45:59 neo kernel: [  172.260607] sd 9:0:0:0: [sdc] Spinning up disk....
Jun  2 14:45:59 neo kernel: [  173.270013] sd 9:0:0:0: [sdc] Attached SCSI removable disk
Jun  2 14:46:07 neo kernel: [  181.289497] usb 1-4: USB disconnect, address 5
Jun  2 14:47:13 neo kernel: [  246.867415] usb 2-5: new high speed USB device using ehci_hcd and address 2
Jun  2 14:47:13 neo kernel: [  247.039109] usb 2-5: configuration #1 chosen from 1 choice
Jun  2 14:47:13 neo kernel: [  247.039772] scsi10 : SCSI emulation for USB Mass Storage devices
Jun  2 14:47:18 neo kernel: [  252.028564] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
Jun  2 14:47:18 neo kernel: [  252.028951] sd 10:0:0:0: Attached scsi generic sg3 type 0
Jun  2 14:47:42 neo kernel: [  275.729406] usb 2-5: USB disconnect, address 2
Jun  2 14:47:42 neo kernel: [  275.729600] sd 10:0:0:0: [sdc] READ CAPACITY failed
Jun  2 14:47:42 neo kernel: [  275.729603] sd 10:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  2 14:47:42 neo kernel: [  275.729608] sd 10:0:0:0: [sdc] Sense not available.
Jun  2 14:47:42 neo kernel: [  275.729621] sd 10:0:0:0: [sdc] Write Protect is off
Jun  2 14:47:42 neo kernel: [  275.729797] sd 10:0:0:0: [sdc] READ CAPACITY failed
Jun  2 14:47:42 neo kernel: [  275.729799] sd 10:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  2 14:47:42 neo kernel: [  275.729803] sd 10:0:0:0: [sdc] Sense not available.
Jun  2 14:47:42 neo kernel: [  275.729818] sd 10:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by samsamros on 2010-06-02
Welcome to the club.... I have reported this problem, nobody had any answers for me so i just stopped connecting my HD in fear of losing info every time it unmounts and disappears randomly. It appears to be less frequent in Kubuntu but it has happened there as well. I'm sorry i do not have more information regarding this issue, I have struggled months with this issue..... Ever since i moved to lucid. They say it's an old bug... but didn't happen before to me. 
Hope you find an answer to your problem.

---

### Post by b0b138 on 2010-06-03
ok so my issue seems to be my sd card reader.  I grabbed some older (and smaller at 2GB) cards and they worked fine. My newer 8GB card would lock up the computer in the middle of posting if left plugged in. So after comparing the cards I noticed that the 8 gig card is SDHC and after skimming through [http://en.wikipedia.org/wiki/Secure_Digital](http://en.wikipedia.org/wiki/Secure_Digital), have come to the conclusion that my old card reader doesn't know what to do with SDHC cards. :rolleyes:

---

### Post by Fatman_UK on 2010-08-13
> **samsamros said:**
> Welcome to the club

Same problem in Lucid for me, but I was about to put it down to a dusty old card reader I haven't even looked at in three years. Guess I'll go and subscribe to the bug. What's the bug ID?

---

