---
title: "Confirmation appreciated"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by AlanRogers on 2007-06-01
I have been asked to replace the hard drive in a business critical machine running Windows XP. My plan is this:[LIST=1]
[*]Install secondary, larger, unformatted hard drive as slave
[*]Boot using Knoppix Live CD and confirm both drives visible, writable and unmounted
[*]Use ```
dd if=/dev/hda of=/dev/hdb
``` to physically copy the entire contents of one disc to the other
[*]Remove the primary drive
[*]Reset jumpers to make secondary drive replacement primary
[*]Reboot and pray[/LIST]Have I missed anything? Is there any glaring flaw in my plan?

---

### Post by AlanRogers on 2007-06-08
Bump [-o<

---

