---
title: "Two cores never goes 100%/100%? Why?"
date: 2008-04-24
forum: Hardware
---

### Post by andrebrait on 2008-04-24
Hi there..

I have an E2140 and noticed that, even when compiling kernel and other heavy stuff, the two cores never goes 100%/100%
Thet always share the load... ex.: 30%/70%... why?

Ubuntu 8.04 x86-64 here

---

### Post by scragar on 2008-04-24
it tries to even out the loads as best it can given that a single program can never use both cores(which is why you'll find that there is never a perfect balance across your cores). You'll find that input/output wait will most likely account for the lack of full potential from your CPU.

---

### Post by camino262 on 2008-04-24
It will go 100/100 with software that takes advantage of multiple processors. Otherwise the software assumes you have 1 processor and  the os balances processes between cpu's.

---

