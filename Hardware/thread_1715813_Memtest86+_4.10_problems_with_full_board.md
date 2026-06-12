---
title: "Memtest86+ 4.10 problems with full board"
date: 2011-03-27
forum: Hardware
---

### Post by jage on 2011-03-27
Have P3 Micron S1854 which says this:

RAM  limit of 768 MB of PC 133 SDRAM, with three slots, and a maximum of 256  MB per chip, and pre-dated DDR RAM.

[http://www.ehow.com/list_7484855_micron-millennium-pc-motherboard-specs.html](http://www.ehow.com/list_7484855_micron-millennium-pc-motherboard-specs.html)

So I bought 3x 256MB chips to replace my 2x 128 MB.

When all three 256MB chips are in I get 100,000s of memtest errors.
Single chip 128 or 256, each one passed the memtest.  128 in each slot passes.
Three 256M back, 100,000s of errors.
Move each one slot over in the board: 100,000s of errors.
Remove one, passes.

Before I try any more combos (128+256+256/128+128+256), what the heck?  Anything I can do to get the max 768?  Since all single tests ran can I use max with ubuntu, despite what memtest throws, or is that going to cause problems?

---

### Post by dandnsmith on 2011-03-28
That's quite an informative link for your hardware!
I'm not familiar with the pre-dated DDR terminology, so have to comment from a less well informed position.
The fact that all 3 slots test out OK is interesting. I've had several samples of this sort of date hardware where you cannot get near what the manufacturer says is the maximum RAM.
I'd first check with Crucial to see what they recommend for the system - they sometimes know the limits rather better, and might suggest a memory type which isn't what you have.
Next, you may have to live with only 2 slots populated, but might be able to use the 256M modules (I'd try that on test, using the originally occupied slots)

If you get errors, you cannot expect to have a cleanly running system, error free - and even if you don't get errors, it may be that you haven't tested it well enough to find the errors.

Good luck

---

