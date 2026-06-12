---
title: "ASrock i865GV+Celeron 3.06 GHZ shows 82 C CPU temp!"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by mister_p_1998 on 2006-07-10
Just built this with Dapper, has my board got a faulty CPU temp sensor? its showing 75 - 82 degrees C as average working temp!
feels a lot cooler than that, its even showing 50 C on a cold start when the mobo sensor is showing 21 C.
It works fine, just a bit scary!
Steve

---

### Post by bigken on 2006-07-10
I would go to the intel web site and what there charts say about your cpu

better safe than sorry

---

### Post by setakht on 2006-07-10
I'd be willing to be there's an it87 sensor chip on that board, because it's an asrock.  If so that's the problem, they always read wrong in linux, no matter what.  Your CPU is fine if reads okay in the bios.

---

### Post by mister_p_1998 on 2006-07-11
> **setakht said:**
> I'd be willing to be there's an it87 sensor chip on that board, because it's an asrock.  If so that's the problem, they always read wrong in linux, no matter what.  Your CPU is fine if reads okay in the bios.

No, thats just it! it reads 80 in the BIOS!

Im not too worried as from a totally cold start, powered down for 12 hours, motherboard=21 C and CPU=51 C. looks like the probe is reading +30 C to me, if so 50 C when running would be normal, as my WinXP box 2.4GHZ reads 50 C in normal use.
Are these a shitty board then? I built on a really tight budget it was the cheapest I could find.

---

### Post by mister_p_1998 on 2006-07-12
Hmm GkrellM shows the CPU temp as 54 even though the BIOS says 67 C?
Interesting eh?

---

