---
title: "Is it possible for Memtest86+ to not detect bad RAM?"
date: 2011-08-03
forum: Hardware
---

### Post by 3602 on 2011-08-03
I was having all kinds of strange problems.
Last night I removed a RAM module and everything went back to normal.
So I shut down, re-inserted that RAM and ran Memtest86+ from a burnt CD all night long.
Fourteen hours, six passes. No errors.

So that's my question. Do I need to do more passes or is there something that Memtest86+ cannot detect?

Or was it just a seating (contact) issue?

Thank you very much.

---

### Post by Manyette on 2011-08-03
Almost certainly is was a seating issue.  While at least one complete pass is a very good idea, I've found it usually will turn up bad memory in half and hour or less.  But I don't believe it would fail you.

---

### Post by 3602 on 2011-08-03
Well then I am relieved. Won't be needing to call Lexar.
Thank you!

EDIT: Semper Fi, Marine.

---

### Post by Manyette on 2011-08-03
I can certainly conceive of situations where it might miss a bad memory location, such as not failing until a certain temperature was reached, but that didn't seem to describe what you were dealing with. I've had bad memory on several occasions, once on a brand new OOB machine, and it always found it un under 20 minutes.

---

### Post by 3602 on 2011-08-03
Yeah if it was temperature-related then a whole night of cooking would certainly bring it up.
Besides, those problems can happen right after a boot...

---

### Post by 3602 on 2011-08-04
OK the problems are coming back.
Screw this, I am running ten passes.

---

### Post by Grenage on 2011-08-04
It would seem more likely that the problem is not memory-related; what are you doing when the problems occur?

---

### Post by Manyette on 2011-08-04
> **3602 said:**
> OK the problems are coming back.
Screw this, I am running ten passes.

Before you do that, gently clean the edge connectors of both of your memory sticks (gently) with an eraser, or perhaps with alcohol.  And blow out the connector slots.

---

### Post by 3602 on 2011-08-04
OK. I might be dealing with two separate fires here.

The first one was most probably RAM related. *make* errors, kernel oops. When I boot Live and try to install, I get File Copying errors, I/O errors, and kernel panics in the Live session. Removing one RAM module instantly solved all that and Maverick installed without one single problem.

Also my hard drive suddenly decided to develop 65000 bad sectors for no reason during that period, so a bunch of bad things all happened together.

The thing is that I was using Firefox 5 before, right, and I got myself that new RAM bar. Then Firefox 5 started to crash. A lot. And led to kernel panics. I thought this was the fault of that RAM since it started after the RAM installation so I ran that six passes, no errors.

 After some analysis it was apparently *xulrunner* causing these crashes. I have just removed that (along with some other stuff that depends on it, including *ubuntu-desktop*) and I shall see what happens.

So either *xulrunner* is triggering something that fourteen hours of Memtest86+ cannot or this Firefox crashing has nothing to do with RAM.

---

### Post by psusi on 2011-08-04
It is not uncommon for intermittent problems to be caused by heat or insufficient power, but only when the entire system is stressed.  Since memtest only tests the memory, it doesn't see the problem, but when you get a bunch of IO going on and load up all your CPU cores and the GPU good and hard, things fall down.

---

