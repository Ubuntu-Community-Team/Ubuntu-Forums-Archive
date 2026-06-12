---
title: "samsung mobile mass storage not detecting"
date: 2010-12-16
forum: Hardware
---

### Post by varunsr11 on 2010-12-16
my samsung s 5603 mobile usb mass storage not detecting in ubuntu 10.4.me new with linux os.  me give lsusb  lsusb Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 019: ID 05c6:1000 Qualcomm, Inc.  Bus 002 Device 018: ID 0421:042f Nokia Mobile Phones  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub   its shows as Qualcomm .pls help me

---

### Post by Fafler on 2010-12-16
It would be nice to know what happens when you connect the phone. From a terminal, type:
```
tail -f /var/log/messages
```
Now, connect the phone and post the output here. Also, make sure you have a memory card in the phone. On most (all?) phones, it's not possible to access the main phone memory in mass storage mode.

---

### Post by varunsr11 on 2010-12-17
Dec 17 22:43:28 varun-desktop kernel: [  347.856532] usb 2-2: new full speed USB device using uhci_hcd and address 3
Dec 17 22:43:29 varun-desktop kernel: [  348.075457] usb 2-2: configuration #1 chosen from 1 choice
Dec 17 22:43:29 varun-desktop kernel: [  348.081328] scsi4 : SCSI emulation for USB Mass Storage devices

---

### Post by Fafler on 2010-12-18
It registers to the kernel as mass storage, but doesn't give any info about media type or size. I think you should try to replicate the problem on another computer.

---

