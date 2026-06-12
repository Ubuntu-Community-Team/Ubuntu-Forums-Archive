---
title: "Best kernel for Pentium M"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by raublekick on 2006-08-24
Hey guys

Is the 686 kernel suitable for Pentium M processors? Everything I've seen before mentions the 686 being suitable up to Pentium IV processors, but nothing about Pentium M.

Just want to make sure before I go installing things.

---

### Post by matthew on 2006-08-24
I found the default 386 kernel works best for me with my PentiumM.

---

### Post by tribaal on 2006-08-24
Same there: I use i386. 
I tried i686 several times, but on my machine it apprears to make the CPU run faster and hotter, which is pretty bad for the batterie's life expectancy.

So I stuck with the stock 386 kernel, which seems to work just fine for me...

- trib'

---

### Post by Tom Tiger on 2006-08-24
Yes, it will work without any problems (on toshiba anyways). I'm running the 686 on a Tecra M4 and at home on a Toshiba Satellite Pro A10 (Pentium M Celeron 2.4ghz)

The only problems you may encounter are with acpi or apm but with Toshiba you shouldn't have a problem (except with tablet notebooks).

What kind of notebook are you running?

---

### Post by matthew on 2006-08-24
> **tribaal said:**
> I tried i686 several times, but on my machine it apprears to make the CPU run faster and hotter, which is pretty bad for the batterie's life expectancy.That's precisely my problem...I should have mentioned it. Thanks, tribaal.

---

### Post by raublekick on 2006-08-24
I'm running a Dell Inspiron 9300.

Thanks for the info guys. I'll give the 686 kernel a shot, and if anything seems funky I'll go back to 386.

---

### Post by tribaal on 2006-08-24
Hehe I got a Dell Inspiron 9300 as well... 

If you manage to get everything working flawlessly (normal heat and CPU usage), please let me know how you did it :)

Cheers!

- trib'

---

### Post by matthew on 2006-08-26
I would like to update everyone...

I had switched back to the 386 kernel at version 2.6.15-23. Today I installed 2.6.15-26-686 and it is working well, no overheating, no weirdness, and quicker than the 386 kernel.

---

