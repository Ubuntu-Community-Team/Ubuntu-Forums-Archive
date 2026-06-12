---
title: "USB sticks unmount by themselves"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by EarlGrey on 2007-11-03
Hello,

after gutsy upgrade, I ran into a problem that a few moments after I plug in anu USB stick (and it mounts properly) it unmounts by itself and keep mounting and unmounting. It is impossilbe access it as the unmounting is very quick.

I tested multiple various sticks.

Thanks for help!

---

### Post by aws910 on 2007-11-06
I've got the same problem!  What can we do?

---

### Post by EarlGrey on 2007-11-13
No idea. Does anybody have a clue what logs to post here?

Thanks!

---

### Post by aws910 on 2007-11-15
I have no idea.  When things like this happen, I think back to the time I was learning how to use Windows.... I think "did it really take me a month to figure something out like this?"

---

### Post by aws910 on 2007-11-21
ummm..... haven't been able to find anything.  Any ideas?

---

### Post by EXCiD3 on 2007-11-21
Both of you guys running Gutsy? What format are the drives, FAT32? Have you checked launchpad for bugs like this?

---

### Post by EarlGrey on 2007-11-22
Hello, thanks for your answer. I have checked the launchpad, but I am not quite experience with it. I have foud however these reports, if they are of any use:

DMESG
```

[  598.253352] usb 3-4: new high speed USB device using ehci_hcd and address 6
[  598.387088] usb 3-4: configuration #1 chosen from 1 choice
[  598.389025] scsi4 : SCSI emulation for USB Mass Storage devices
[  598.389445] usb-storage: device found at 6
[  598.389450] usb-storage: waiting for device to settle before scanning
[  603.386855] usb-storage: device scan complete
[  603.387561] scsi 4:0:0:0: Direct-Access     TrekStor USB MASS STORAGE 1.00 PQ: 0 ANSI: 0 CCS
[  603.391107] sd 4:0:0:0: [sdc] 2073600 512-byte hardware sectors (1062 MB)
[  603.391844] sd 4:0:0:0: [sdc] Write Protect is off
[  603.391852] sd 4:0:0:0: [sdc] Mode Sense: c0 00 00 00
[  603.391855] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  603.394336] sd 4:0:0:0: [sdc] 2073600 512-byte hardware sectors (1062 MB)
[  603.394962] sd 4:0:0:0: [sdc] Write Protect is off
[  603.394970] sd 4:0:0:0: [sdc] Mode Sense: c0 00 00 00
[  603.394973] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  603.395019]  sdc:
[  603.396787] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[  603.396895] sd 4:0:0:0: Attached scsi generic sg2 type 0


```
And on the first shell (ctlr +alt + F1)
```

[some numbres] sd 3.0.0.0: [sdc] Assuming drive cache: write though
[some numbres] sd 3.0.0.0: [sdc] Assuming drive cache: write though


```

---

