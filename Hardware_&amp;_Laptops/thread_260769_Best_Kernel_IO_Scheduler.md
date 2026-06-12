---
title: "Best Kernel I/O Scheduler"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by zgornel on 2006-09-19
I was wondering which is the best I/O Scheduler for a tipical laptop configuration (512 MB DDR2, 60GB SATA1, Pentium-M 1.73). Tested out CFQ, Deadline and AS schedulers, the only difference noted so far was that Deadline generated a bit higher disk performance (using hdparm -tT /dev/sda) than CFQ and AS (from 31 to 32 MB/s). Saw some threads on the forum recommending CFQ for improved multi-tasking performance and responsiveness. Other documents on the net suggested that for small desktop configuration (uniprocessor or dual, no RAID) the default AS scheduler should be employed. Nonetheless, AS generates process starvation in some instances. If anyone tested them or has any suggestions, I'd appreciate them. Thx.

---

### Post by ankara on 2007-11-23
as a desktop user, you wont notice the difference, is the short answer.
if your running intense I/O apps then this will be different obviously. 
i use ubuntu studio and notice some (not loads) of performance gain while using deadline scheduling during multi-traack recording sessions. 
hth

---

