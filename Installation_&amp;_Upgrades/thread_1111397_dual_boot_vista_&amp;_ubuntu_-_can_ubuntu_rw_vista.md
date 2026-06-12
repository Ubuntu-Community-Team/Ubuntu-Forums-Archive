---
title: "dual boot vista &amp; ubuntu - can ubuntu r/w vista partion?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by itinko on 2009-03-30
I'm contemplating installing dual boot Ubuntu on current Vista Ultimate. Will I be able to read and write Vista partition from Ubuntu boot?

Thanks much!

Michael

---

### Post by Mark Phelps on 2009-03-30
Yes -- but I would advise strongly against doing that.  It appears to be very easy to corrupt the Vista OS partition, and if that happens, unless you have a Vista DVD from which to run Startup Repair, your Vista is unbootable after that.

Also, if you get any filesystem anomalies messing with the Vista partition, and you have it mounted in fstab, the next time you boot, Ubuntu will refuse to finish booting until you run chkdsk in Vista.  If you then can't boot into Vista to run chkdsk, you will then have TWO OS's that don't work.

A better solution is to create a shared partition for use by both Vista and Ubuntu.  Both can read/write NTFS partitions, and if the filesystem does get corrupted, it's a simple matter to boot into Vista and run chkdsk to fix it.

---

