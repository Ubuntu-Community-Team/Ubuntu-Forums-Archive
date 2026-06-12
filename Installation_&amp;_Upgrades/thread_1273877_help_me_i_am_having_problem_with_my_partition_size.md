---
title: "help me i am having problem with my partition size"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-09-23
hi All,
       I am having problem with my partition size, I am getting this error while running sql

ERROR:
ORA-09817: Write to audit file failed.
Linux Error: 28: No space left on device
ORA-09945: Unable to initialize the audit trail file
Linux Error: 28: No space left on device

when I have run folloing command then I have seen some partitions are very small 
$ du -sk *
0    proc
du: cannot read directory `root': Permission denied
4    root
9348    sbin
4    selinux
200    srv
0    sys
du: cannot read directory `tmp/pulse-PKdhtXMmr18n': Permission denied
12    tmp
9456740    u01
8    u02
2972684    usr
730028    var
0    vmlinuz
0    vmlinuz.old

please recomend any tool which is usefull for me to repartition without loss of my data either windows and ubuntu files, I am having dual boot.

---

### Post by gadolinio on 2009-09-24
Boot with a liveCD, and run system--administration--gparted partition editor. It's easy to use and lets you resize your current partitions, create, format, etc...

---

### Post by manojpawar on 2009-09-24
[_hi _gadolinio]("http://ubuntuforums.org/member.php?u=910735")
           Shoud I repartition my hard disk by using Ubuntu live cd.without using gparted.

---

### Post by gadolinio on 2009-09-24
> **manojpawar said:**
> [_hi _gadolinio]("http://ubuntuforums.org/member.php?u=910735")
           Shoud I repartition my hard disk by using Ubuntu live cd.without using gparted.

Use gparted, but do it from a liveCD session, instead of doing it from your normal user's account. Boot with the liveCD, and then open gparted (it's included in the liveCD).

---

