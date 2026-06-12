---
title: "AMD Athlon XP 64 X2"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by brakmaren on 2005-12-30
Any one know where i can find info on if Ubuntu supports or have plans to support the functions of the 64-bit x2.
Thank's

---

### Post by reet on 2005-12-30
Yes, that processor will work with either the 32bit or 64 bit kernels. I recommend sticking with 32bit Ubuntu for the time being because there is a lack of software support for the 64bit platform. You need to install the SMP kernel to take advantage of the dual cores.

---

### Post by brakmaren on 2006-01-18
Thank's mate, i'll order one then :-)

---

### Post by WildTangent on 2006-01-18
You need to use the K7-SMP kernel for 32 bit multiprocessor support.
```
sudo apt-get install linux-k7-smp
```
Enter that in a terminal as soon as you get Ubuntu installed on your computer with the new CPU.

-Wild

---

### Post by brakmaren on 2006-01-19
I don't get the new comp until April. IF i'm lucky, it will time Dapper :-)
Thank's for the info. I'm convinced there will be more questions when it gets here :-p

---

