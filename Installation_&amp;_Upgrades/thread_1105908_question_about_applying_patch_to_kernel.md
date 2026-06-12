---
title: "question about applying patch to kernel"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by a.dehqan on 2009-03-25
In The Name Of God

I'll be thankfull if you guide ;
this patch code has been saved as 2.patch  in root folder .
and with this command applied to kernel : patch -p2 -l < 2.patch
after that it asked this > "File to patch:"
what should be answered to this question ?

debian:~# patch -p2 -l < 2.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urN linux-2.6.18.3.original/block/ll_rw_blk.c linux-2.6.18.3.hdaps/block/ll_rw_blk.c
|--- linux-2.6.18.3.original/block/ll_rw_blk.c    2006-11-19 03:28:22.000000000 +0000
|+++ linux-2.6.18.3.hdaps/block/ll_rw_blk.c    2006-11-26 11:29:55.000000000 +0000
--------------------------
File to patch:

regards dehqan

---

