---
title: "USB flash drive not working... help! =O"
date: 2010-07-19
forum: Hardware
---

### Post by Iehova on 2010-07-19
Hi,

I have an 8GB USB flash drive that had recently stopped working. It is recognised by both windows and linux when I plug it in (ie they both physically recognise that a mass storage device has been plugged in) but it doesn't show up in Nautilus' Computer window (even as a disk that can't be mounted) and the system log reports a huge stream of error messages:

```
Jul  9 12:57:40 Lucy-Mk2 kernel: [ 4592.820093] usb 1-6: new high speed USB device using ehci_hcd and address 6
Jul  9 12:57:40 Lucy-Mk2 kernel: [ 4592.983422] usb 1-6: configuration #1 chosen from 1 choice
Jul  9 12:57:40 Lucy-Mk2 kernel: [ 4592.984080] scsi7 : SCSI emulation for USB Mass Storage devices
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4597.983467] scsi 7:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4597.985019] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4597.999169] sd 7:0:0:0: [sdb] 11 512-byte logical blocks: (5.63 kB/5.50 KiB)
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.000914] sd 7:0:0:0: [sdb] Write Protect is off
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.005913]  sdb:
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.007017] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.007028] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.007038] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.007053] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.007083] __ratelimit: 636 callbacks suppressed
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.008262] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.008270] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.008279] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.008289] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.009386] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.009394] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.009402] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.009412] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.010816] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.010826] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.010835] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.010846] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.012388] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.012396] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.012405] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.012414] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.013903] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.013912] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.013922] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.013933] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.015139] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.015148] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.015156] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.015166] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.016261] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.016269] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.016278] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.016289] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.017386] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.017394] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.017402] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.017411] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.017459] Dev sdb: unable to read RDB block 0
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.018511] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.018519] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.018527] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.018537] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.019636] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.019644] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.019652] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.019662] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.021140] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.021148] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.021157] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.021167] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.022262] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.022270] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.022278] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.022288] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.022333]  unable to read partition table
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.028914] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.040282] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.040294] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.040305] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.040319] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.041516] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.041524] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.041532] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.041542] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.042764] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.042772] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.042781] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.042790] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.043889] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.043897] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.043906] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.043915] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.045014] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.045022] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.045031] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.045040] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.046138] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.046146] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.046155] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.046164] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.047391] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.047400] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.047409] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.047418] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.048514] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.048523] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.048532] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.048541] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.049642] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.049651] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.049660] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.049669] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.051029] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.051037] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.051046] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.051055] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.056516] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.056524] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.056533] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.056542] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.057764] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.057772] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.057781] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.057791] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.058888] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.058896] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.058905] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.058914] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.060176] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.060185] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.060193] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.060203] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.061390] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.061398] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.061407] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.061416] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.062513] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.062521] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.062529] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.062539] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.063639] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.063648] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.063656] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.063666] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.064763] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.064772] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.064780] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.064789] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.065887] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.065896] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.065905] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.065915] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.067014] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.067023] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.067032] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.067041] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.068138] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.068146] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.068156] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.068165] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.070394] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.070403] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.070412] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.070422] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.071640] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.071648] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.071657] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.071666] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.072763] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.072771] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.072779] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.072789] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.073887] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.073895] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.073903] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.073913] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.075139] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.075146] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.075155] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.075164] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.076263] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.076271] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.076280] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.076290] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.077388] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.077396] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.077405] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.077414] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.078514] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.078522] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.078530] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.078540] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.079713] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.079721] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.079730] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.079739] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.081015] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.081024] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.081032] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.081042] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.082138] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.082146] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.082154] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.082164] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.083263] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.083271] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.083279] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.083288] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.084388] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.084396] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.084404] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.084413] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.085514] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.085522] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.085530] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.085539] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.086644] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.086653] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.086664] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.086673] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.087773] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.087781] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.087791] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.087801] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.090328] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.090338] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.090348] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.090359] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.091882] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.091891] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.091900] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.091911] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.093140] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.093149] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.093158] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.093167] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.094264] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.094273] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.094282] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.094291] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.095391] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.095399] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.095408] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.095418] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.096515] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.096523] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.096532] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.096542] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.097639] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.097647] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.097656] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.097667] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.098764] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.098773] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.098781] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.098791] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.099892] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.099900] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.099909] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.099919] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.101142] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.101151] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.101159] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.101169] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.102264] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.102272] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.102280] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.102289] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.103387] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.103395] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.103403] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.103413] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 01 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.104513] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.104521] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.104530] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.104539] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.105639] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.105647] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.105655] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.105665] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.119147] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.119161] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.119173] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.119187] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.120264] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.120272] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.120281] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.120290] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.121522] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.121530] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.121539] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.121548] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.162406] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.162421] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.162432] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.162445] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.164044] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.164061] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.164073] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.164088] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.170417] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.170432] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.170443] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.170455] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.172052] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.172063] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.172073] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.172086] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.173264] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.173272] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.173281] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.173292] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.174388] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.174396] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.174404] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.174414] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.175513] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.175521] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.175530] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.175540] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.176639] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.176646] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.176655] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.176665] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.177763] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.177771] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.177780] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.177790] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.178888] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.178897] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.178905] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.178915] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.180044] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.180059] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.180080] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.180098] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.181764] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.181773] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.181781] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.181790] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.183011] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.183021] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.183041] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.183061] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.184262] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.184271] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.184279] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.184289] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.185386] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.185394] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.185402] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.185411] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.186511] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.186518] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.186527] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.186545] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.187887] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.187896] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.187905] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.187916] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.189139] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.189148] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.189157] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.189167] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.190266] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.190275] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.190284] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.190294] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.191387] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.191396] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.191405] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.191415] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.192512] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.192520] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.192529] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.192539] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.193636] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.193645] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.193653] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.193663] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.194761] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.194770] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.194779] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.194789] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.195886] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.195894] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.195903] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.195913] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.197011] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.197020] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.197029] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.197039] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.198136] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.198146] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.198155] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.198164] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.199261] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.199271] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.199280] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.199289] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.200387] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.200397] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.200406] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.200416] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.201511] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.201520] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.201529] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.201538] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.202637] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.202646] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.202655] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.202665] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.203761] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.203769] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.203778] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.203788] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.204886] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.204894] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.204903] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.204913] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.206011] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.206020] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.206028] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.206038] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.207136] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.207144] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.207153] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.207163] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.208261] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.208270] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.208278] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.208288] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.209386] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.209394] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.209403] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.209413] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.210512] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.210521] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.210531] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.210541] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.211636] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.211645] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.211654] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.211664] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.212761] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.212770] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.212779] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.212789] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 01 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.213886] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.213894] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.213903] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.213913] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.215012] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.215020] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.215029] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:45 Lucy-Mk2 kernel: [ 4598.215039] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.578011] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.578018] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.578022] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.578028] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.579126] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.579130] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.579133] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.579137] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.580252] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.580255] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.580259] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.580262] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.581377] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.581380] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.581384] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.581388] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.582529] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.582536] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.582545] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.582553] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.583753] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.583757] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.583760] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.583764] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.584877] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.584880] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.584884] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.584887] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.586001] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.586005] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.586008] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.586012] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.587126] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.587130] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.587133] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.587136] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.588251] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.588254] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.588258] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.588261] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.589376] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.589379] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.589383] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.589386] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.590502] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.590505] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.590508] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.590512] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.591627] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.591630] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.591634] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.591637] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.592756] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.592759] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.592762] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.592766] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.594002] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.594006] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.594009] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.594013] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.595127] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.595130] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.595133] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.595137] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.596252] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.596255] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.596259] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.596263] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.597377] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.597380] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.597384] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.597388] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.598502] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.598505] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.598509] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.598513] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.599627] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.599630] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.599633] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.599637] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.600752] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.600755] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.600759] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.600763] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.601877] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.601880] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.601884] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.601888] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.603005] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.603009] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.603012] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.603016] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.604128] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.604131] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.604134] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.604138] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.605251] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.605255] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.605258] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.605262] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.606378] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.606381] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.606385] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.606388] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.607503] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.607506] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.607510] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.607513] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.608628] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.608632] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.608635] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.608639] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.609753] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.609757] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.609760] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.609764] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.610878] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.610881] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.610884] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.610888] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.612003] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.612006] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.612009] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.612013] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.613128] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.613132] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.613135] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.613139] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.614253] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.614256] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.614259] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.614263] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.615378] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.615382] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.615385] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.615389] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.616502] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.616506] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.616509] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.616513] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.617628] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.617631] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.617635] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.617639] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.618753] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.618756] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.618759] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.618763] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.619883] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.619887] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.619890] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.619894] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.620881] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.620884] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.620887] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.620891] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 01 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.622006] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.622009] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.622013] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.622017] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.623161] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.623168] sd 7:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.623173] sd 7:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jul  9 12:57:48 Lucy-Mk2 kernel: [ 4600.623179] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 03 00

```

There doesn't seem to be anything physically wrong with the device, at least from the outside, and if I leave it plugged into windows for long enough it appears as a drive in explorer but I can't explore it and even right clicking the drive is extremely slow (perhaps 10 minutes to open the menu).

The drive has a few years' worth of pictures on (I know, backup backup but it isn't mine) so if anyone could help in their recovery I'd be eternally grateful.

---

### Post by dv3500ea on 2010-07-19
It sounds like the drive is failing.
Try using ddrescue or gddrescue to rescue the data.
(You will need to install these)

---

