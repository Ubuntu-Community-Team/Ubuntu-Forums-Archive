---
title: "Quad Core = HOW MANY processors???"
date: 2010-09-27
forum: Hardware
---

### Post by r_avital on 2010-09-27
Brand new laptop, HP Pavillion DV8T with  i7-740QM Quad Core processor.

Am I correct that I should see 4 processors in gnome's "System Monitor" on the resources tab?

I'm looking at 8, really, eight of them, each with its own graph in its own color.  And the first tab (System) lists CPUs 0 through 7.

Is that correct, or is this a bug in System Monitor?  What am I missing?

TIA

---

### Post by psusi on 2010-09-27
Maybe you have 4 cores that are each hyperthreaded into two?  See if you can turn off hyperthreading in the bios.

---

### Post by Yellow Pasque on 2010-09-27
> **psusi said:**
> Maybe you have 4 cores that are each hyperthreaded into two?  See if you can turn off hyperthreading in the bios.
No reason to turn off hyperthreading (except maybe to conserve power).
So yes, it is "correct."

---

### Post by psusi on 2010-09-27
> **Temüjin said:**
> No reason to turn off hyperthreading (except maybe to conserve power).
So yes, it is "correct."

That, and under certain workloads, it slows things down, and under most workloads, fails to speed it up any, at least when you already have more than 1 core.

---

### Post by Yellow Pasque on 2010-09-27
Ah, I see. I guess it depends on the user's workload then...

---

### Post by PresenceofMind on 2010-09-27
> Am I correct that I should see 4 processors in gnome's "System Monitor" on the resources tab?

Not if Hyperthreading is enabled. Core i7 laptops come with hyperthreading enabled (in the BIOS) by default. 

> I'm looking at 8, really, eight of them, each with its own graph in its  own color.  And the first tab (System) lists CPUs 0 through 7

Due to hyperthreading, the Linux OS sees 8 logical cores that can carry out instructions.

> Is that correct, or is this a bug in System Monitor?  What am I missing?

Yes, that is correct. Nope, no bug. You are missing nothing. :P

---

### Post by Gadget Wizard on 2010-09-27
Am jealous, i got an old ibook mac g3 with 900 mhz,

---

### Post by r_avital on 2010-09-27
Thanks for the education and the great replies, all of you :)

And I've also learned I have no reason to turn off multithreading.

---

