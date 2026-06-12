---
title: "Order to disable mttr entries?"
date: 2008-08-10
forum: Hardware
---

### Post by stinkinrich88 on 2008-08-10
Hello, 

I have the problem stated in this guide: [http://ohioloco.ubuntuforums.org/showthread.php?t=743472]("http://ohioloco.ubuntuforums.org/showthread.php?t=743472") so I have been trying to follow the instructions to solve it.

One of the first instructions tells me to disable all entries of my mttr by using the following command:

```
echo "disable=*" >| /proc/mtrr
```

Where * is a value from 0-4. Trouble is, the order I disable the entries matters, otherwise x freezes. I've tried loads of different combinations but can't do it without x freezing! How do I find out what the proper combination is?

Thanks! Here's my mttr:

```
reg00: base=0xcff00000 (3327MB), size=   1MB: uncachable, count=1
reg01: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
reg02: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg03: base=0xcfea6000 (3326MB), size=   4KB: write-back, count=1
reg04: base=0xd0000000 (3328MB), size= 256MB: write-combining, count=1

```

---

### Post by stinkinrich88 on 2008-08-10
please? :roll:

---

### Post by jocko on 2008-08-10
> **stinkinrich88 said:**
> Trouble is, the order I disable the entries matters, otherwise x freezes. I've tried loads of different combinations but can't do it without x freezing! How do I find out what the proper combination is?

Can't help you with the order, but can't you do it without running X?
Try to go into single user mode by typing "sudo init 1" in a terminal, then set up the new values and type "init 2" to start normal mode.

---

