---
title: "Low Copy Speed For SATA to SATA Transfer"
date: 2008-08-02
forum: Hardware
---

### Post by Brando569 on 2008-08-02
Ive always wondered this when im transferring data from one SATA2 drive to another SATA2 drive the copy speed is never above 25 MB/sec even though one is a WD second generation raptor and the other one has a 16mb cache. shouldnt it be higher then that considering the max transfer speed of SATA2 is 375MB/sec?

Im using the generic ubuntu kernel btw.

---

### Post by GreenN00b on 2008-08-02
Depends on hard drive speed too.

---

### Post by GreenN00b on 2008-08-02
You can use a command like this
```
sudo hdparm -t /dev/sda

```
to determine the read speed from the hard disk ...

---

### Post by Brando569 on 2008-08-02
> **GreenN00b said:**
> Depends on hard drive speed too.

the raptor is 10k rpm and the other drive is 7200 rpm

the reason was i was copying from an ntfs partition to an xfs partition. i finally decided to convert that partition from ntfs to xfs since i barely use windows anymore and once i did the transfer rate went from about 10-25 MB/sec to about 60-70 MB/sec :D

---

