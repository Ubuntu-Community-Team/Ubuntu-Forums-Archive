---
title: "Not recognized - Compact flash card on Multi card reader"
date: 2014-01-04
forum: Hardware
---

### Post by Resistent on 2014-01-04
Hi all !

I have following problem:

I connected a multi card reader to Ubuntu 13.10.
when I plug in an 1024 MB Compact Flash card from Kingston --> works OK, Ubuntu automount it.
when I plug in a 2 GB Compact Flash card from Platinum --> DON'T WORK, Ubuntu cannot automount it.

--> Can somebody give me a hint ?

**With not working PLATINUM **

1.) **lsusb** looks like:
```
Bus 002 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card ReaderBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c06a Logitech, Inc. USB Optical Mouse
Bus 003 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

2.) fdisk -l **don't shows** the Platinum card
3.) Ubuntu preferences -> Disks -> shows the multimedia slots and automount is on "**ON**".


**With working KINGSTON:**

1.) **lsusb** looks like: (looks the same)
```
Bus 002 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card ReaderBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c06a Logitech, Inc. USB Optical Mouse
Bus 003 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```
2.) fdisk -l **shows** the Platinum card
3.) Ubuntu preferences -> Disks -> shows the multimedia slots and automount is on "**ON**".

---

### Post by Resistent on 2014-01-04
Solved. It was a mechanical problem. 
One of the PINs on the Card Reader was bent, so it could not get into the small hole on the Compact Flash card.
Looks like this PIN was needed in the case of the 2 GB size Compact Flash card.

---

