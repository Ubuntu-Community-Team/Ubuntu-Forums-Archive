---
title: "Resume from standby speed"
date: 2012-08-28
forum: Hardware
---

### Post by Nisuspi on 2012-08-28
I'm hoping someone can help me with a very minor hole in my technical knowledge...

I've been playing around with Ubuntu on several Ultrabooks as of late, and got most everything working as well as if not better than Windows, with the exception of one thing: standby/hibernate/resume speeds.

Obviously Intel has invested a lot into speeding up resume from standby/power use in suspended state on Windows, but other than Dell's Project Sputnik I can't find much info about where Linux is on this stuff. It's not that I'm desperate to use it (although it would be nice), rather that I'm curious about the state of play.

As far as I can tell, with Ubuntu we have a choice of two standby options: suspend - which is impractically high in terms of battery use for most, and hibernate - which takes about as long as a cold boot to return from, SSD notwithstanding.

Dell appears to have got the same 'suspend in a lower power state' on the XPS 13 under Ubuntu as it has in Linux - anyone know how?

---

### Post by Szor3n on 2012-08-28
I have a relatively new Samsung laptop, and the suspend for me actually (from what I can tell) shut's off the laptop.  All lights / fans etc are off, and I have left it for days and come back to a still nearly full battery.  Maybe this is related to the intel tech that you're talking about, because I know this laptop "supports" that for windows 8.

---

### Post by mikeymop on 2013-06-05
> **Szor3n said:**
> I have a relatively new Samsung laptop, and the suspend for me actually (from what I can tell) shut's off the laptop.  All lights / fans etc are off, and I have left it for days and come back to a still nearly full battery.  Maybe this is related to the intel tech that you're talking about, because I know this laptop "supports" that for windows 8.
I too am on a quest to maximize the ultrabook experience in Ubuntu Linux. Kernel 3.8 in raring really helped with battery life, a lot of the tweaks I had to enable are now on by default. However I get a few errors when X.org starts and suspend consumes a lot of power and doesn't have instant resume like Windows did.
There isn't much documentation on Sandy/Ivy Bridge ultrabooks for Linux outside of getting hardware support. Is this a driver issue or can a simple kernel config achieve these lower power fast resumes.

---

