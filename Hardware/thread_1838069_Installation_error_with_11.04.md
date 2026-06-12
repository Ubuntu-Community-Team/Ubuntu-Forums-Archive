---
title: "Installation error with 11.04"
date: 2011-09-02
forum: Hardware
---

### Post by sandesh.sboa on 2011-09-02
Hi all, 

could you please look at the error which i get every time i try to install Ubuntu 11.04 on my HP DV6 , i7, 8gb ram, windows 7, ATI HD 6730 ddr5 .

---

### Post by 2F4U on 2011-09-03
Can you also post the mentioned log file since it seems to contain additional information?

---

### Post by grahammechanical on 2011-09-03
This is the command that is producing the error

[http://msdn.microsoft.com/en-us/library/ff542202(v=vs.85).aspx]("http://msdn.microsoft.com/en-us/library/ff542202(v=vs.85).aspx")

I have two suggestions.

1) You check out the Wubi mega thread on this forum and search for similar posts.

2) Confirm that you have assigned enough disk space for the device partition G for Ubuntu to install into it. This is just a wild guess. I have no experience with using Wubi to install Ubuntu inside Windows.

Regards.

---

### Post by bcbc on 2011-09-03
You're attempting to install Ubuntu on a computer with dynamic drives. This is not supported (either with Wubi or normal install).

(Ubuntu will use whatever partition info is in the MBR partition table and ignore the dynamic drives). So even if you manage to install it (e.g. on C: ) or through dual booting, it could lead to data loss/corruption.

---

### Post by sandesh.sboa on 2012-03-15
@bcbc - So does it mean that i cannot install this version on my laptop ? what would i have to do to install?

Pls suggest !

---

### Post by bcbc on 2012-03-15
You shouldn't install linux on a computer with dynamic drives. If there are partitions that are hidden from linux then - if you mount them and try to use them - there is a danger you could destroy data. I don't know this for a fact, but not all dynamic partitions show up in the MBR partition table, so it seems logical.

The particular error you got was from windows (bcdedit command rejecting the G: drive) - which would indicate that G: is one of those partitions not in the partition table.

The only solution I am aware of is to convert back from dynamic drives. Microsoft doesn't provide an easy way - they recommend deleting all partitions and recreating. But some people have been able to do it with Easeus - I assume by first merging back any partitions that are not in MBR: [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

---

