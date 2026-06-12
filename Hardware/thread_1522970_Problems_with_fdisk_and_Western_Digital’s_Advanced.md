---
title: "Problems with fdisk and Western Digital’s Advanced Format"
date: 2010-07-02
forum: Hardware
---

### Post by egarim on 2010-07-02
Hi,
I read a lot of similar thread about the problem of unalignment partitions.

I create a small partition fdisk -H 224 -S 56 /dev/sdb:
Device Boot Start End Blocks Id System
/dev/sdb1 2048 1048576 523264+ 83 Linux

but I still have bad performance:
410025984 byte (410 MB) copied, 52,2462 s, 7,8 MB/s

I'm running a Ubuntu 8.04.4 LTS 2.6.24-19 with util-linux-ng 2.13.1. The disk is a wd green WDC WD6400AARS-00Y5B1. Thanks for help.

---

