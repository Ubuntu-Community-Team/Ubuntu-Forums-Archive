---
title: "Intermittent USB"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by sirsmilealot on 2008-01-29
Dear All,

I'm using Gutsy Gibbon and for some reason, having problems with both USB ports on my IBM R40 laptop. On a few occasions I can simply plug in my pen drive and have it automount like normal, without a problem. However, most of the time - when I plug my drive into either of the ports, the device flickers constantly (as if it were being accessed), but doesn't mount.

It would seem that the device is oscillating between mounting and unmounting, but so quickly that Ubuntu doesn't have time to recognise the drive. Here's a sample from '/var/log/messages':

Jan 29 21:10:38 Laptop-4 kernel: [  577.276000] usb 4-3: new high speed USB device using ehci_hcd and address 18
Jan 29 21:10:39 Laptop-4 kernel: [  577.764000] usb 4-3: new high speed USB device using ehci_hcd and address 20
Jan 29 21:10:40 Laptop-4 kernel: [  578.472000] usb 4-3: new high speed USB device using ehci_hcd and address 21
Jan 29 21:10:40 Laptop-4 kernel: [  578.772000] usb 4-3: new high speed USB device using ehci_hcd and address 22
Jan 29 21:10:40 Laptop-4 kernel: [  579.072000] usb 4-3: new high speed USB device using ehci_hcd and address 23
Jan 29 21:10:41 Laptop-4 kernel: [  579.984000] usb 4-3: new high speed USB device using ehci_hcd and address 24
Jan 29 21:10:42 Laptop-4 kernel: [  580.692000] usb 4-3: new high speed USB device using ehci_hcd and address 25
Jan 29 21:10:43 Laptop-4 kernel: [  581.572000] usb 4-3: new high speed USB device using ehci_hcd and address 28

Also, before I forget to mention, if the pen drive is plugged in while the system boots up, it appears to be operating normally - up until the point Ubuntu begins to load.

This is becoming more and more of a problem as I often need to transfer school work to and from the laptop. Has anyone any ideas?

Many thanks in advance for your help!

Kindest Regards,

Paul Smith,

---

