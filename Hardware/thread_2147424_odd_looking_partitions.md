---
title: "odd looking partitions"
date: 2013-05-21
forum: Hardware
---

### Post by GUZZLR on 2013-05-21
Hello all,
Does anybody find it odd that I have dev/sda5 inside my extended (attached)...Is that how it should be?
Thanks

---

### Post by deadflowr on 2013-05-21
Totally normal.
/dev/sda2 is an extended partition, which houses all the logical partitions, such as /dev/sda5.
Typically, the first four partitions are set for primary and any beyond that are logical.
An extended parttion is a primary partition.

If that makes sense.

---

### Post by GUZZLR on 2013-05-22
OK, Good.  This was a messed up install and I lost my XP Pro, but that is OK because it's an old computer that I'm using as a test... Thanks

---

