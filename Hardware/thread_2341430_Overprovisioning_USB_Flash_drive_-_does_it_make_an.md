---
title: "Overprovisioning USB Flash drive - does it make any difference?"
date: 2016-10-28
forum: Hardware
---

### Post by ultragamer2 on 2016-10-28
Ok

So you can over provision ssds by leaving some unformatted space so it wears more evenly.

But if you leave unformatted space at the end of a usb flash drive (used for lots of writing) will it last longer?

---

### Post by kurt18947 on 2016-10-28
The controller in flash drives  monitors flash cell condition and marks failing cells unusable then taps the overprovisioned cells as replacements. The controller in an SSD can do that,  I'm not sure about a USB flash drive controller. I doubt the controller in a $5  flash drive is as sophisticated as an SSD controller. I was reading reviews on high performance flash drives sometime ago and reviewers opened up a high end USB 3 device. It had a low end SSD controller in it so I assume it'd be possible to overprovision USB flash drives like SSDs. USB drives are pretty price sensitive though.

---

### Post by ultragamer2 on 2016-10-28
Thanks, so for a cheap brand flash drive it probably wouldn't use the unformatted space for wear levelling?

---

### Post by kpatz on 2016-10-28
The better name brand flash drives have wear leveling (Corsair for example).  In general they'll last longer if not kept full all the time, but I don't really know how that works since they don't support TRIM like a SSD would.

But even without, they'll last quite a while even when written to a lot.  Just keep backups in case it does go bad.  Flash drives usually fail for reasons other than flash wear (bad solder joints, shoddy construction, buggy controllers etc).

---

