---
title: "my computer wont recognise my Mp3/USB device"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by iiDopDop!! on 2008-02-22
Hey i have a 1gb Mp3 player and every time i try to put music on my device my computer wont recognize the device. What can i do to the computer to make it recognize the device?

---

### Post by jmate24 on 2008-02-24
Is it iPod?

---

### Post by kevmitch on 2008-02-25
run the command "dmesg", plug in the device and wait a few seconds, then run dmesg again and post the lines that are added the second time around here.

---

### Post by iiDopDop!! on 2008-03-06
sorry i took so long... No its not an ipod i have tried alot of different types of ipods on my computer and they work perfectly. I did what you told me and here are a bit of the results i dont know how much you wanted.


[27851.583876] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[27851.583983] sd 2:0:0:0: Attached scsi generic sg3 type 0
[27861.460833] usb 1-1.2: USB disconnect, address 4
[27890.185382] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[27890.309470] usb 1-1.2: configuration #1 chosen from 1 choice
[27890.314536] scsi3 : SCSI emulation for USB Mass Storage devices
[27890.314657] usb-storage: device found at 5
[27890.314661] usb-storage: waiting for device to settle before scanning
[27895.310600] usb-storage: device scan complete
[27895.313609] scsi 3:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
[27895.320607] sd 3:0:0:0: [sdb] 511104 2048-byte hardware sectors (1047 MB)
[27895.323545] sd 3:0:0:0: [sdb] Write Protect is off
[27895.323556] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[27895.323561] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[27895.332533] sd 3:0:0:0: [sdb] 511104 2048-byte hardware sectors (1047 MB)
[27895.335569] sd 3:0:0:0: [sdb] Write Protect is off
[27895.335582] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[27895.335586] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[27895.335596]  sdb: sdb1
[27895.343647] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[27895.343741] sd 3:0:0:0: Attached scsi generic sg3 type 0 


there is alot more than that but any help appreciated from what i have given.

---

