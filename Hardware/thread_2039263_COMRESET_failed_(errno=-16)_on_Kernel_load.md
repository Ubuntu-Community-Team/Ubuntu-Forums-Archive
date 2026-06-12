---
title: "COMRESET failed (errno=-16) on Kernel load"
date: 2012-08-08
forum: Hardware
---

### Post by testblageneric on 2012-08-08
Hello,

on my Samsung Series 5 Ultrabook i've got the following error when loading the Kernel of my Lubuntu install: "comreset failed (errno=-16)" This appears three times before giving up and delaying the boot up by around 40 sec.

The error is related to the internal SSD which somehow can't be accessed by the BIOS correctly anymore. The error appeared first after a bluescreen on my parallely booted Windows 7 occured. I'm quite sure that the SSD is already broken... 

My question now is:

"How can i instruct the Kernel to skip the broken drive?" 

(As i need the laptop , i can't have it replaced right now.) 

Excerpt of my kern.log:

> Aug  7 10:23:09 Ultrabook kernel: [    1.343423] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  7 10:23:09 Ultrabook kernel: [    1.344428] ata1.00: ATA-8: Hitachi HTS545050A7E380, GG2OA6C0, max UDMA/133
Aug  7 10:23:09 Ultrabook kernel: [    1.344438] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Aug  7 10:23:09 Ultrabook kernel: [    1.345577] ata1.00: configured for UDMA/133
Aug  7 10:23:09 Ultrabook kernel: [    1.345818] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 GG2O PQ: 0 ANSI: 5
Aug  7 10:23:09 Ultrabook kernel: [    1.346007] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Aug  7 10:23:09 Ultrabook kernel: [    1.346010] sd 0:0:0:0: [sda] 4096-byte physical blocks
Aug  7 10:23:09 Ultrabook kernel: [    1.346014] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  7 10:23:09 Ultrabook kernel: [    1.346119] sd 0:0:0:0: [sda] Write Protect is off
Aug  7 10:23:09 Ultrabook kernel: [    1.346121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  7 10:23:09 Ultrabook kernel: [    1.346190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  7 10:23:09 Ultrabook kernel: [    1.355404] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Aug  7 10:23:09 Ultrabook kernel: [    1.412527]  sda: sda1 sda2 sda3 < sda5 >
Aug  7 10:23:09 Ultrabook kernel: [    1.413708] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  7 10:23:09 Ultrabook kernel: [    1.488096] hub 1-1:1.0: USB hub found
Aug  7 10:23:09 Ultrabook kernel: [    1.488284] hub 1-1:1.0: 6 ports detected
Aug  7 10:23:09 Ultrabook kernel: [    1.599122] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Aug  7 10:23:09 Ultrabook kernel: [    1.731659] hub 2-1:1.0: USB hub found
Aug  7 10:23:09 Ultrabook kernel: [    1.731864] hub 2-1:1.0: 6 ports detected
Aug  7 10:23:09 Ultrabook kernel: [    1.786869] Refined TSC clocksource calibration: 1696.146 MHz.
Aug  7 10:23:09 Ultrabook kernel: [    1.786880] Switching to clocksource tsc
Aug  7 10:23:09 Ultrabook kernel: [    1.803016] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
Aug  7 10:23:09 Ultrabook kernel: [    2.298426] usb 2-1.4: new full-speed USB device number 3 using ehci_hcd
Aug  7 10:23:09 Ultrabook kernel: [    2.466223] usb 2-1.5: new full-speed USB device number 4 using ehci_hcd
Aug  7 10:23:09 Ultrabook kernel: [    6.377364] ata2: link is slow to respond, please be patient (ready=0)
Aug  7 10:23:09 Ultrabook kernel: [   11.019854] ata2: COMRESET failed (errno=-16)
Aug  7 10:23:09 Ultrabook kernel: [   16.373401] ata2: link is slow to respond, please be patient (ready=0)
Aug  7 10:23:09 Ultrabook kernel: [   21.015894] ata2: COMRESET failed (errno=-16)
Aug  7 10:23:09 Ultrabook kernel: [   26.369438] ata2: link is slow to respond, please be patient (ready=0)
Aug  7 10:23:09 Ultrabook kernel: [   56.014014] ata2: COMRESET failed (errno=-16)
Aug  7 10:23:09 Ultrabook kernel: [   56.014020] ata2: limiting SATA link speed to 3.0 Gbps
Aug  7 10:23:09 Ultrabook kernel: [   61.039947] ata2: COMRESET failed (errno=-16)
Aug  7 10:23:09 Ultrabook kernel: [   61.039958] ata2: reset failed, giving up
Regards,
Andreas

---

