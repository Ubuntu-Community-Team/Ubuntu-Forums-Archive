---
title: "Utilize 32bit core duo processor?"
date: 2010-07-25
forum: Hardware
---

### Post by decomp on 2010-07-25
Hi all! 

I just a new (second hand) laptop and it has an Intel T2400 core duo processor. Some googling has yielded that while it is a dual core processor it is not 64 bit. I found some old forums (circa 2007) recommending a linux-686-smp kernel to make the best use of this processor. But the only reference in the repos is from Dapper drake.

Do I need to do anything special to take advantage of the second core, or has ubuntu got me all sorted out already?

cat /proc/cpuinfo

shows:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2

---

### Post by iponeverything on 2010-07-25
you don't have to anything special. The second core will be picked up. The smp kernel is installed by default.

---

### Post by decomp on 2010-07-30
Great thanks! :)

---

