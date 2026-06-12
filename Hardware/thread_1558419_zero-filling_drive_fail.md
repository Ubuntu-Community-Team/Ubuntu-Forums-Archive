---
title: "zero-filling drive fail"
date: 2010-08-22
forum: Hardware
---

### Post by Dreen on 2010-08-22
Hello.

I have a drive with some bad sectors. I want to zero-fill it so that the sectors get remapped to spare ones. Here is a screenshot from ubuntu livecd disk util:
```
http://img806.imageshack.us/img806/2648/screenshot1j.png
```This is what happens when I try to run dd (using livecd; it runs ok for a few minutes):
```
root@ubuntu:/# dd if=/dev/zero of=/dev/sdb
dd: writing to `/dev/sdb': Input/output error
6162633+0 records in
6162632+0 records out
3155267584 bytes (3.2 GB) copied, 315.073 s, 10.0 MB/s
```It fails. What can I do?

---

### Post by IcarusR on 2010-08-22
Should the of not be /dev/sdb1 the NTFS partition with the test errors.
Or delete the partition then run original command.

---

