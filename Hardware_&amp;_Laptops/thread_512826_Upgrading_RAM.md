---
title: "Upgrading RAM"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by skrribble on 2007-07-29
Hey...

The relevant specs of my machine are:
HP xt963 (about 5 years old)
Asus TUW-AM motherboard

Anyway, I'm running Feisty and decided to get some more RAM for the system since it only came with 128MB originally... The motherboard runs PC133 SDRAM  and I got another 256 and put it in.... the mobo can support 256MB in each DIMM so I dont know what the problem is.... Do I have to do something to get it working?
BTW the RAM is Samsung, if that makes any difference

---

### Post by mgmiller on 2007-07-29
Memory upgrades should "just work".  Things to try:

Put the new 256 meg stick in the first memory slot and remove the old 128 meg stick.  See if it boots with just the new stick.

Are both sticks the same CAS ratings?  Check your BIOS and set the memory timings to a lowest common denominator, like 3,3,3.

Make sure the memory voltages in BIOS are correct and that both memory sticks use the same voltage.

Is one stick buffered and one unbuffered?

Ideally, when you add memory, you should try to add memory with identical specs.  It doesn't have to be the same brand, but the specs should be the same.

Sometimes 2 sticks just won't play well together.

Try booting off a feisty live CD and run the memtest utility.

Good luck..

---

