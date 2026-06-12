---
title: "Help with HDD data recovery"
date: 2011-01-14
forum: Hardware
---

### Post by Statik on 2011-01-14
Before you say anything, yes I did search. In fact, I was using the guide here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

Here's my question: I was using ddrescue, and managed to recover about half of the partition I needed before I tried something else, before I restarted the ddrescue. I tried testdisk to rewrite the partition headers. This left me without any partitions. Now, the drive is failing and I can't seem to get the partitions back so I can resume the ddrescue.

As well, I cannot mount the image as it comes up as an unknown type.

So, I need some advice/help with both these issues. I have tried both scalpel and foremost but there are other datatypes I want to recover, mostly open office documents.

Any help appreciated.

Thanks!

Statik

---

### Post by pl@yer on 2011-01-14
dd doesn't need partition information afaik. I think you should be able to do something like this.
assuming /dev/hda1 is the failed drive and /dev/sdb1 is a spare.
```

dd if=/dev/hda1 of=/dev/sdb1/backup/image.iso conv=noerror,sync

```
when it finishes you could try mounting the image as loopback
```

mount -o loop /dev/sdb1/image.iso /mount/image

```

---

### Post by pl@yer on 2011-01-14
wtf

---

