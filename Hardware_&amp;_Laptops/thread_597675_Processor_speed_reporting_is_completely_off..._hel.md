---
title: "Processor speed reporting is completely off... help?"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by shaggy999 on 2007-10-30
Ok, this happens in BOTH Windows and Ubuntu. Basically when the computer reports the speed of my processor I know for a fact that the reported speed is incorrect. My processor is a Pentium M 2.13 Ghz, which can step down to as low as 787 MHz. The problem is that it reports my max possible speed as 600 MHz and my lowest speed as 75 MHz. What's going on here?

 Strangely enough it was reported fine in Feisty, but after I wiped Feisty and installed Gutsy I now have the same problem that Windows has.

Here's what is in /proc/cpuinfo

brandon@gutsy-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.13GHz
stepping        : 8
cpu MHz         : 600.000

---

### Post by shaggy999 on 2007-10-31
Can anybody help? It's really annoying to see my laptop think it's running at 75 MHz when it's really not. I laughed when windows did it but ubuntu didn't, and now I'm sad. :(

---

