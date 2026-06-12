---
title: "e6600 cores reporting higher temps in linux"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by rockman2 on 2008-03-07
So in Linux it is reporting that my cores are 5-10 degrees warmer while idle and load with same fan speeds. I use coretemp in windows. Any advice?

---

### Post by tgalati4 on 2008-03-07
What version of Linux are you using?  If you use Hardy, you will get a "tickless" kernel that will allow your processors to be interrupted less, thereby going into a deeper sleep state, saving power, and running cooler.

Try it and let us know your running temperatures.

Otherwise, count up the processes running under both systems.  More processes generally means more interrupts and thus, less chance to go into low-power modes which allow the cores to cool.

---

