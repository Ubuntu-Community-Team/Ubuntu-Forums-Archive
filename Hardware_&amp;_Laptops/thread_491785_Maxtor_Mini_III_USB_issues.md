---
title: "Maxtor Mini III USB issues"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by enderak on 2007-07-04
I am having trouble with my new Maxtor Mini III USB drive.  When I plug it in, it seems to auto-mount just fine, and I can read/write to it (formatted as FAT32), however even when connected to a USB 2.0 port, the speed is very slow.

Looking at /var/log/messages, about every 31 seconds, give or take a second, I receive a message like the following: *Jul  3 21:30:31 jane kernel: [51460.164966] usb 5-3: reset high speed USB device using ehci_hcd and address 7*

In the Device Manager, it lists the Vendor as VIA Technologies, Inc. and the OEM Vendor as ASUSTeK Computer Inc. For Product/Device it just says "USB 2.0" but does not give any further information.

Has anyone had any experience with this problem, and/or is there anything I can try short of installing a new PCI USB 2.0 card? The current controller is built-in to the motherboard of an Athlon 1800+ system which is a few years old.

EDIT: Forgot to mention, this is on Ubuntu 7.04, with all updates applied.

---

### Post by enderak on 2007-07-04
I installed a new Belkin 5-port USB 2.0 card, and it works fine now going through the new card. I am going to chalk it up to a crappy on-board controller. IIRC, this motherboard was one of the first boards with USB 2.0 built-in.

---

