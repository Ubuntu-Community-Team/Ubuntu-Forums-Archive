---
title: "SQUASHFS error:"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by MalcolmGNAR on 2009-09-27
I was restoring my dell mini 9 to factory setting and this error shows up constantly


[478.1231241] SQUASHFS error: Unable to read something block ex51f98

it keeps on going how do I fix it?

help!

---

### Post by roadrash on 2009-10-03
first check the MD5SUM & if its OK then try burning at a lower speed or I sometimes find burning to a CDRW does the trick.  Finally you ccould try puting it on a USB stick using a util called Unetbootin which should work. I really wish Ubuntu would stop using SquashFS as its always causing me problems as welland must put off a lot of other people.

---

### Post by plougher on 2009-10-03
[B]I really wish Ubuntu would stop using SquashFS as its always causing me problems as well and must put off a lot of other people.

[/B]I wish people would stop blaming Squashfs, you're confusing symptom and cause.  The cause of these errors is corrupted data read off disk, the symptom is Squashfs reports error because it cannot do anything useful with corrupt data.

The cause of the data corruption is typically a bad burn, dirty disk (in the case of CDROM), memory errors, other hardware faults or a buggy I/O driver in descending order of probability,

---

