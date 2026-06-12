---
title: "Connecting Boss/Roland BR-1200CD as USB drive"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by skaboobie on 2007-11-29
I have a **[COLOR="Blue"][Boss BR-1200CD multitrack recorder]("http://http://rolandus.com/products/productdetails.aspx?ObjectId=738&ParentId=110")[/COLOR] **that has a feature where it can be connected to a Windows PC or Mac as a USB drive so that you can copy the audio files off of it.  This feature works fine when I boot into Windows.

I am running Ubuntu Studio Gutsy, and I wanted to do the same thing.  However, when I do, the BR-1200CD displays a message, "HDD damaged! Please turn off power now."  When I restart the BR-1200CD, it's fine; it's internal drive certainly is not damaged.  I wonder if it thinks the Linux machine that it is connecting to is damaged.  Here is what /var/log messages shows.  [Note: this shows 2 attempts to connect.] 

```

dudek@skaboobie:~$ tail -f /var/log/messages
Nov 29 22:14:28 skaboobie kernel: [   95.650551] usbcore: registered new interface driver usb-storage
Nov 29 22:14:28 skaboobie kernel: [   95.650712] USB Mass Storage support registered.
Nov 29 22:14:33 skaboobie kernel: [  100.663195] scsi 0:0:0:0: Direct-Access     BOSS     BR-1200CD        1.00 PQ: 0 ANSI: 0
Nov 29 22:14:33 skaboobie kernel: [  100.706375] sd 0:0:0:0: [sda] Attached SCSI removable disk
Nov 29 22:14:33 skaboobie kernel: [  100.722533] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 29 22:14:33 skaboobie kernel: [  100.824053] sd 0:0:0:0: [sda] 78165361 512-byte hardware sectors (40021 MB)
Nov 29 22:14:33 skaboobie kernel: [  100.831044] sd 0:0:0:0: [sda] Write Protect is on
Nov 29 22:14:33 skaboobie kernel: [  100.846032] sd 0:0:0:0: [sda] 78165361 512-byte hardware sectors (40021 MB)
Nov 29 22:14:33 skaboobie kernel: [  100.853024] sd 0:0:0:0: [sda] Write Protect is on
Nov 29 22:14:33 skaboobie kernel: [  100.853033]  sda: sda1
Nov 29 22:15:04 skaboobie kernel: [  131.271198] usb 3-2: reset full speed USB device using ohci_hcd and address 2
Nov 29 22:15:16 skaboobie kernel: [  143.508605] usb 3-2: USB disconnect, address 2
Nov 29 22:15:16 skaboobie kernel: [  143.509089] scsi 0:0:0:0: scsi: Device offlined - not ready after error recovery
Nov 29 22:15:16 skaboobie kernel: [  143.513258] scsi 0:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 29 22:15:16 skaboobie kernel: [  143.513266] end_request: I/O error, dev sda, sector 78165352
Nov 29 22:16:49 skaboobie kernel: [  235.800426] usb 3-2: new full speed USB device using ohci_hcd and address 3
Nov 29 22:16:49 skaboobie kernel: [  236.038381] usb 3-2: configuration #1 chosen from 1 choice
Nov 29 22:16:49 skaboobie kernel: [  236.050456] scsi1 : SCSI emulation for USB Mass Storage devices
Nov 29 22:16:54 skaboobie kernel: [  241.061268] scsi 1:0:0:0: Direct-Access     BOSS     BR-1200CD        1.00 PQ: 0 ANSI: 0
Nov 29 22:16:54 skaboobie kernel: [  241.088280] sd 1:0:0:0: [sda] Attached SCSI removable disk
Nov 29 22:16:54 skaboobie kernel: [  241.088323] sd 1:0:0:0: Attached scsi generic sg0 type 0
Nov 29 22:16:54 skaboobie kernel: [  241.226118] sd 1:0:0:0: [sda] 78165361 512-byte hardware sectors (40021 MB)
Nov 29 22:16:54 skaboobie kernel: [  241.233111] sd 1:0:0:0: [sda] Write Protect is on
Nov 29 22:16:54 skaboobie kernel: [  241.248099] sd 1:0:0:0: [sda] 78165361 512-byte hardware sectors (40021 MB)
Nov 29 22:16:54 skaboobie kernel: [  241.255092] sd 1:0:0:0: [sda] Write Protect is on
Nov 29 22:16:54 skaboobie kernel: [  241.255100]  sda: sda1
Nov 29 22:17:24 skaboobie kernel: [  271.705246] usb 3-2: reset full speed USB device using ohci_hcd and address 3
Nov 29 22:17:55 skaboobie kernel: [  302.414578] usb 3-2: reset full speed USB device using ohci_hcd and address 3
Nov 29 22:18:26 skaboobie kernel: [  333.123912] usb 3-2: reset full speed USB device using ohci_hcd and address 3
Nov 29 22:18:36 skaboobie kernel: [  343.534877] usb 3-2: reset full speed USB device using ohci_hcd and address 3
Nov 29 22:18:45 skaboobie kernel: [  352.635017] usb 3-2: USB disconnect, address 3
Nov 29 22:18:45 skaboobie kernel: [  352.637486] scsi 1:0:0:0: scsi: Device offlined - not ready after error recovery
Nov 29 22:18:45 skaboobie kernel: [  352.639367] scsi 1:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 29 22:18:45 skaboobie kernel: [  352.639376] end_request: I/O error, dev sda, sector 78165352

```

I've been running various Linux distros since '92, but I'm a bit of a noob when it comes to how USB and firewire drives are handled.  Is there some setting that I should be using so that the BR-1200CD doesn't freak out?

:guitar:

---

