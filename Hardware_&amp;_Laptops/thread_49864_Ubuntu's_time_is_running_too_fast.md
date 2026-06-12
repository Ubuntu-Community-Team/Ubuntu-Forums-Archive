---
title: "Ubuntu's time is running too fast"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by Data on 2005-07-18
Hi,

I have the strange problem, that the time is running much too fast on my Targa Traveller 826 with AMD 3000+ processor. So, the time is very soon after the start far ahead of the real time...

I have cpu frequency scaling on, also I ave configured the real time clock into the kernel. Processor runs most of the time with 800 MHz. Could that be the problem?

Have I to adjust something in the kernel. Any ideas?

Data

---

### Post by s_p_a_r_k_y on 2005-07-18
to temporarily have a fix, try using ntp to set the time. I usually have the problem where the computers are running behind real time...not ahead...

---

### Post by GuyveR800 on 2005-07-18
This question has been answered several times already...
use 'noapic nolapic noapictimer' boot options.

---

