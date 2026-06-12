---
title: "the acpi_cpufreq module"
date: 2009-07-08
forum: Hardware
---

### Post by rubenvb on 2009-07-08
Hi everybody,

how does the linux kernel cpu frequency scaling work? It seems to me it switches to lower power states quickly when *nothing* is going on and switches a lot to a higher power state when there are interrupt calls from eg the graphics driver. That's what I can deduce from y experience.

I know for a fact that Windows uses cpu load to determine the power state and multiplier, which I see as better, it allows you to run eg desktop effects while staying in a lower power state, while in Linux (with my assumption), the CPU continually switches to the higher power states, thus running hotter.

Is this correct, and if it is, is there a way to change cpu scaling to respect cpu load instead of interrupt calls, as to perhaps reduce responsiveness, but increase cpu time spent in lower power states?

Thanks

---

### Post by shatterblast on 2009-07-09
Usually, the CPU has optimizations built into it that doesn't read from the BIOS.  With this in scope, a CPU will go faster when it receives more electricity.  One of the concepts of "over-clocking" involves either slightly raising the electricity value or the clock speed multiplier.  (A single CPU core basically runs like an over-complicated clock with gadgets attached.)  In almost all cases, you should avoid over-clocking.  Some hardware vendors claim to support it, but remember that flirting with danger quickly translates to needing a purchase of computer parts.

Linux in its native state can run 10 times more efficiently on some notebook computers.  Some users have reported running a battery for 8 hours of continuous usage where it would only have lasted an hour or less under Vista.  Results vary of course.  The Remix version of Ubuntu may have a few extra settings enabled for power-saving, but I think the same can be done in the standard distribution.

I haven't checked the XFCE version of Ubuntu yet, which is Xubuntu.  I would assume that since XFCE has a performance advantage over other GUIs like Gnome and KDE in regards to its resource usage that it would consume less battery power, but it's only speculation.

---

### Post by rubenvb on 2009-07-09
Thanks for the answer, but you're talking about something else. I want to know how the kernel decides which power state is used, not how they work.

---

### Post by shatterblast on 2009-07-09
> **rubenvb said:**
> how does the linux kernel cpu frequency scaling work?
> **rubenvb said:**
> I want to know how the kernel decides which power state is used, not how they work.

My bad.

---

