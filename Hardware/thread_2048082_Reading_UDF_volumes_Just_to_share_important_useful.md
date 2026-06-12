---
title: "Reading UDF volumes: Just to share important useful information"
date: 2012-08-26
forum: Hardware
---

### Post by krishna.988 on 2012-08-26
Hi All,

Recently I had issues reading multisession UDF volumes in Ubuntu 12.04 which was burnt in Windows.  So I jumped across a solution which I thought I would share with you guys:

Just type this command in Terminal:


sudo mount -t udf /dev/sr0 /mnt -o ro,session=0,lastblock=1 

  Once you enter this command DVD contents become visible

Thanks

---

