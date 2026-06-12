---
title: "'Dead' external usb harddrive"
date: 2008-06-03
forum: Hardware
---

### Post by rhp on 2008-06-03
Hi all,

For a while now, I've had an external usb drive attached to my computer. When I am stressing this drive (e.g. playing movie, copying files, and doing a build at the same time) the drive disconnects with the following messages:

Jun  2 16:38:00 asus kernel: [282994.653897] usb 3-5: reset high speed USB device using ehci_hcd and address 20
Jun  2 16:38:07 asus kernel: [283001.667035] usb 3-5: USB disconnect, address 20
Jun  2 16:38:07 asus kernel: [283001.667425] sd 2:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jun  2 16:38:07 asus kernel: [283001.667433] end_request: I/O error, dev sda, sector 288455015
Jun  2 16:38:07 asus kernel: [283001.667488] lost page write due to I/O error on sda1
Jun  2 16:38:07 asus kernel: [283001.684650] __journal_remove_journal_head: freeing b_frozen_data
Jun  2 16:38:08 asus kernel: [283001.798943] usb 3-5: new high speed USB device using ehci_hcd and address 22

After that I have to disconnect the usb cable, after connecting I can resume operation.

Any ideas whether this is a drive problem, or a usb kernel driver problem or anything else?

Thanks,

Ronald Pijnacker

---

