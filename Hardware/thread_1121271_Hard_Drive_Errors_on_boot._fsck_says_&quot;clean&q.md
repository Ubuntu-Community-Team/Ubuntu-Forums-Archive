---
title: "Hard Drive Errors on boot. fsck says &quot;clean&quot;"
date: 2009-04-09
forum: Hardware
---

### Post by R2LL2R on 2009-04-09
Hi all, 

Been having a few issues with my ubuntu box. about 2 weeks ago it started showing the old "[3402.000034595] <insert repeatable error here>, sdb, sector 23455623566" (warnng, not a real quote, I'll edit in exact error asap)

I did a quick search on the other computer and came up with hard drive (unlikely, only 8 months old, connected to clean power) or RAM. Ram is expensive lifetime warranty stuff, but I tested with memtest86 2.1 (?) from grub, and 3.3 from bootable cd, both run all-night passes without errors.

next stem was fsck from recovery, then atempted 'init 1' to fsck manually, but no luck, so I booted live CD and su'd then fsck'd (with correct type arguments) and it reported:
"
ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb1: clean, 191800/29786112 files, 14804482/119125983 blocks
"
(this tooc sseconds, not minutes like when I'd done it from recovery mode, but result was the same...

anyone have any ideas? RAM seems fine, drive thinks it is clean?

---

