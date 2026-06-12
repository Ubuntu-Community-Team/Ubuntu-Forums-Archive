---
title: "Can't mount Roland Fantom-X usb 'hard drive'"
date: 2008-07-18
forum: Hardware
---

### Post by luctor on 2008-07-18
I've got a new Roland Fantom-X7 synthesizer with built in 'usb harddrive'. It's actually the internal memory that's being mounted.
When I switch on 'USB storage' on the synth the following messages appear in /var/log/messages
```
usb 1-8.1: new full speed USB device using ohci_hcd and address 7
usb 1-8.1: configuration #1 chosen from 1 choice
scsi5 : SCSI emulation for USB Mass Storage devices
scsi 5:0:0:0: Direct-Access     Roland   FANTOM-X         2.00 PQ: 0 ANSI: 0
sd 5:0:0:0: [sdc] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg3 type 0
sd 5:0:0:0: [sdc] 64001 512-byte hardware sectors (33 MB)
sd 5:0:0:0: [sdc] Write Protect is off
sd 5:0:0:0: [sdc] 64001 512-byte hardware sectors (33 MB)
sd 5:0:0:0: [sdc] Write Protect is off
sdc: sdc1
end_request: I/O error, dev sdc, sector 64000
end_request: I/O error, dev sdc, sector 64000
end_request: I/O error, dev sdc, sector 63992
```
The **end_request: I/O** errors go on for about a 100 lines ..

Funny thing is I *can* mount it in a virtual WinXP machine using VirtualBox.

I'm running UbuntuStudio 8.04 AMD64
kernel 2.6.24-19-rt

Any help appreciated

Rob

---

