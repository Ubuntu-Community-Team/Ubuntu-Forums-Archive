---
title: "system is all swapped after waking up from hibernate"
date: 2010-07-21
forum: Hardware
---

### Post by bazilio1 on 2010-07-21
Hi!

My system is Ubuntu 10.04 on Sony VPCS11X9R laptop (4GB RAM). When system wakes up from hibernate it appears that all memory pushed into swap (like 200M in memory and 1GB in swap), so after it woke up it becomes very laggy until I use all the applications to get them from swap(or simply do swapoff and swapon). I tried hibernating using s2disk and it wakes up fine (not so fine actually, where are other small problems, but at least it is not swapped). How can I fix this?

---

### Post by muedvedik on 2010-08-12
I have same problem, huge IO activity - system is swapping out and back after wake-up even from suspend to ram.

---

### Post by muedvedik on 2011-04-02
it's video driver problem - looks to dmesg

---

