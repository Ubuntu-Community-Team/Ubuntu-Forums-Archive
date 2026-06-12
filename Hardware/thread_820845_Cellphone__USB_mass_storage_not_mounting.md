---
title: "Cellphone / USB mass storage not mounting"
date: 2008-06-06
forum: Hardware
---

### Post by lordhedgehog on 2008-06-06
I bought an Ericsson 580i which claims that when plugged into a computer's USB port, it will appear as an external hard drive on both Windows and Mac.  I figured it would work on my Feisty Fawn.  Normal USB thumb drives and MP3 players mount automatically on being plugged in, but I get nothing with this phone.

It seems to be connecting as /dev/sdb, but there's no /dev/sdb1 or /dev/sdb2.  Mounting /dev/sdb gives me a no medium error.  My /var/log/messages produces the following output:

Jun  6 13:34:54 hex kernel: [ 1580.504000] usb 2-1: new full speed USB device using ohci_hcd and address 3
Jun  6 13:34:55 hex kernel: [ 1580.740000] usb 2-1: configuration #2 chosen from 1 choice
Jun  6 13:34:55 hex kernel: [ 1580.864000] usbcore: registered new interface driver libusual
Jun  6 13:34:55 hex kernel: [ 1580.876000] Initializing USB Mass Storage driver...
Jun  6 13:34:55 hex kernel: [ 1580.880000] scsi2 : SCSI emulation for USB Mass Storage devices
Jun  6 13:34:55 hex kernel: [ 1580.880000] usbcore: registered new interface driver usb-storage
Jun  6 13:34:55 hex kernel: [ 1580.880000] USB Mass Storage support registered.
Jun  6 13:35:00 hex kernel: [ 1585.888000] scsi 2:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
Jun  6 13:35:00 hex kernel: [ 1585.900000] sd 2:0:0:0: Attached scsi removable disk sdb
Jun  6 13:35:00 hex kernel: [ 1585.900000] sd 2:0:0:0: Attached scsi generic sg1 type 0


Can anyone tell how to mount this to copy files on/off the phone?  Many thanks!

---

### Post by lordhedgehog on 2008-06-06
Found the solution, sort of.  The manual states that both internal memory and memory sticks can be used as USB mass storage devices.  Turns out only the memory stick can be used that way...  I put a memory stick in, and it works fine.  I still can't access internal memory, but that's OK.

---

