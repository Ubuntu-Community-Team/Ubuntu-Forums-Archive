---
title: "general ram question"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-06-08
which is a more reliable set up for a 533mhz machine?

one strip of 533mhz of higher quality (more expensive) OCZ ram. 1024mb
or one strip 633mhz of less quality (cheap) Corsair ram. 1024mb

Im not overclocking or anything like that, but i am removing one strip and donating to sisters machine, but i don't want to get shafted by my generosity.  both machines have a bus speed of 533.

thanks.

(it would be really great if logical arguments could be made)

---

### Post by xzero1 on 2007-06-08
All else being equal, I would go for the 633 ram since running it at 533 is essentially underclocking the ram. In the same way Opterons are underclocked in the server market for increased reliability and robustness.

---

### Post by 444 on 2007-06-08
Well, either way, you might be loosing dual-channel. Stick-by-stick, what matters is memory timings. Lower timings are better. Give the one with high timings at 533 to her. Personally I'd test each manually instead of going with what's on the label, though that might be too much trouble for you, I am currently running some no-name ram at fast cl3 timing even though it says cl5 on the label...

---

### Post by CrispyFried on 2007-06-08
run each stick by itself under memtest86 from the grub menu. keep the one with the lowest CAS timing (the 1st digit is the most important). if theyre the same Id keep the OCZ ram but thats just my preference for that company.

edit: memtest also gives a Mb/s number, you can also use that number to see which is faster.. higher is better.

---

