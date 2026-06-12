---
title: "Problems detecting file-backed storage gadget on usb"
date: 2008-09-23
forum: General Help
---

### Post by john linn on 2008-09-23
I am running Ubuntu 6.10 as a USB Host machine.  

I am plugging in an embedded device running open source linux 2.6.27 with the file-backed storage gadget running. I plug it into the USB port of the Ubuntu machine and expect the host to add a new scsi device sd* when it sees it but it never does.  Other mass storage devices seem to work fine.

When plugging in the embedded device with file-backed storage gadget I only get the following messages.

Sep 23 09:29:12 wolfgang-pc kernel: [21976600.100000] usb 5-5: new high speed USB device using ehci_hcd and address 71

Sep 23 09:29:13 wolfgang-pc kernel: [21976600.644000] usb 5-5: new high speed USB device using ehci_hcd and address 72

Sep 23 09:29:13 wolfgang-pc kernel: [21976601.188000] usb 5-5: new high speed USB device using ehci_hcd and address 73

Sep 23 09:29:13 wolfgang-pc kernel: [21976601.324000] usb 5-5: new high speed USB device using ehci_hcd and address 74

When I plug in other mass storage devices I get messages about the scsi devices and they work correctly.

This works on a redhat machine so I’m thinking there’s a configuration issue or a bug somewhere?

Thanks,

John

---

