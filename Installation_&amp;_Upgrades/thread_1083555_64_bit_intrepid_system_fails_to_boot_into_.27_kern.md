---
title: "64 bit intrepid system fails to boot into .27 kernel"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by TheSilverHornet on 2009-03-01
Title's pretty much the issue, in a nutshell.  It'll work with 2.6.24-21-generic without issue, but 2.6.27-7-generic hangs.  It drops me into busybox briefly, but then carries on with normal booting, rattles some stuff past too fast to read about raid, then hangs later after 'Attached scsi generic sg4 type 0', or very similar.

If you need more information please ask and I'll do my best to dig it up. Thanks in advance. :)

---

### Post by TheSilverHornet on 2009-03-02
I'm not one for bumping, but this is a pretty important issue - I can't use wifi in the older kernel due to a bug with rt61pci ... I'm effectively without internet access in linux until I can resolve this. :( Does anyone have any pointers as to how to go about diagnosing the issue?

---

### Post by TheSilverHornet on 2009-03-04
Thank you for the support, it's much appreciated.

I've since solved it, it's due to the DVD drive spitting back nonsense when the kernel pokes it, which delayed my raid array starting just long enough to miss when it was needed; a DVD drive firmware update fixed it. Might file a bug report later.

---

