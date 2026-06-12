---
title: "C3 Processor running too slow.."
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by Swab on 2006-01-29
I've just built a mini-itx box with an Epia MII-6000 motherboard... the processor is supposed to run at 600MHz however cpuinfo is reporting it's only at 400MHz.  I've even compiled my own kernel for the C3 chip but still it's the same.  I don't have this problem is other distros, or even with a hoary install.   Any ideas?

---

### Post by mo_x on 2006-01-29
Does the C3 have any form of frequency scaling?

---

### Post by Swab on 2006-01-29
Well it's supposed to run at 4.5x 133MHz if that's what you mean... but obviously it's running at 3x 133Mhz right now... is there some way to change this from the OS?

---

### Post by Swab on 2006-01-29
Ah... I'm guessing it has something to do with this powernow daemon..

powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 399Mhz - 598Mhz (4 steps)

---

### Post by az on 2006-01-29
Did you just build the box?  Is there a jumper for frequency on the motherboard?

(I know it may be an obvious question, but first things first....)

---

### Post by Swab on 2006-01-29
[QUOTE=azz]Did you just build the box?  Is there a jumper for frequency on the motherboard?

(I know it may be an obvious question, but first things first....)[/QUOTE]

No, there's no jumper on the board... it was the powernow daemon.. killed it and I'm up to 600MHz :)

---

