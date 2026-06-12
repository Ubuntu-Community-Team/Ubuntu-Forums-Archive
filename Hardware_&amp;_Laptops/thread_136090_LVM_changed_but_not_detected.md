---
title: "LVM changed but not detected"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by joelman on 2006-02-25
OK, I made a mistake in the first subject line.  Maybe the corrected subject line will attract a response.

I have an old Dell gx300 with a Maxtor one-touch partitioned using LVM When I first installed Ubuntu (Breezy Badger), it was detected on usb and set up very nicely, thank you very much. But I decided that usb 1.0 is way too slow, so I bought a firewire card, which was also detected very nicely.

The problem is that the drive is not found at boot anymore, and an error is raised because it can't be mounted. But if I do a vgscan, then a vgchage -ay, then mount -a, all is well and my volumes are mounted.

How do I tell LVM to look at the firewire card instead of the usb controller?

TIA
Joel

---

