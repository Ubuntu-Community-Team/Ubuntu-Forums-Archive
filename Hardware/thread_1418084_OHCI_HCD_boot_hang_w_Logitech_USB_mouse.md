---
title: "OHCI_HCD boot hang w/ Logitech USB mouse"
date: 2010-02-28
forum: Hardware
---

### Post by AtomicP on 2010-02-28
I've been trying to find a new distro that supports my (relatively old) laptop, a HP NX9105.  The trouble is that each and every one including Ubuntu/Kubuntu 9.10 and as far as I can tell anything based around the 2.6.31 kernel all hang at the same line on boot.

**ohci_hcd 0000:00:02.0: enabling device (0004 -> 0006)**

It pauses here for approx 30 seconds before resuming and all is fine.

I've narrowed it down to my Logitech MX1000 wireless mouse, which if I remove entirely during boot there is no delay and everything is fine.  Sounds like a petty thing to complain about, but I didn't see this problem in distros based on 2.6.30 and below.  

For instance, Puppy Linux 4.31 is based on 2.6.30 and boots fine.  I'm able to recompile a new kernel from source, but I'm wondering which part of the kernel doesn't like my mouse.

Like I said before, this is more of a quirk than a deal breaker, but it'd be nice if everything 'worked'.

Many thanks.

---

### Post by IcarusR on 2010-02-28
Rather than recompile kernel why not downgrade kernel to 2.26.30 ?

---

### Post by AtomicP on 2010-02-28
Is that possible?  I mean if I use say Ubuntu 9.10 with an older kernel, do I risk messing up some other aspect of the system or are most things written from a 2.6.xx perspective?

How would I get the 2.26.30 kernel besides using an older Ubuntu?  

Thanks for your input by the way.

---

