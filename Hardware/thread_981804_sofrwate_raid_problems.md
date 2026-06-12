---
title: "sofrwate raid problems"
date: 2008-11-14
forum: Hardware
---

### Post by jure1873 on 2008-11-14
I've been getting errors on about md0 in my syslog recently.

kernel: [51633.138476] md0: rw=1, want=14422288384, limit=78123904

and

kernel: [51633.116359] Buffer I/O error on device md0, logical block 2534762332

and

kernel: [51633.116364] lost page write due to I/O error on md0

I don't know what is wrong and what to do?

It's a mirrored ext3 partition for backups. I've tried running fsck yesterday and it repaired the filesystem, but today I got new errors and now I'll have to retry to repair. 

mdadm now tells me everything is fine, but fsck gave me errors.

---

