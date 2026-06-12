---
title: "How long should hibernate take?"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by jerwarren on 2006-06-23
Since having suspend problems, I decided to try out hibernate, and have found that it takes absolutely forever to hibernate, and then forever and a half to resume from hibernation.  I assume this isn't normal

When I tell it to hibernate, the screensaver comes on for a few seconds, then the screen turns off, but power stays on for a good several minutes (I waited 3 and then left.  WHen I came back a half hour later or so I found that it had turned off at some point.)  Powering back on took another 3-5 minutes, but it did in fact resume to the same point it was at before hibernation.

How long should hibernate actually be taking, and any idea what I need to tweak to make it go that fast?

I'm on a Compaq Presario V4000.

---

### Post by shof2k on 2006-06-26
Do you know if the hibernate is based on suspend2?  There was a post on including this into Breezy and i'm unsure if this made it into dapper.

If so, then a fast hibernate is dependent on having the correct IDE driver module built into the kernel.

In short, you might need a kernel recompile :(.

---

### Post by jerwarren on 2006-06-30
That's the other thing.  After deciding to try to fix th eproblem myself, I learned of the various ways to hibernate, and have been unable to determine which ubuntu is using :(

---

### Post by wrtrdood on 2006-06-30
Monitor the /var/log/acpid logs to see if there's any wierdness going on there.  Depending on the system, it can take a few minutes to close everything out.  Could be some applications or hardware taking it's sweet time to shut down.  My laptop hibernates in around 3 minutes and resumes in less than 2 minutes on the current kernel.  I've not had the time to build a new kernel but I'm sure I can get better times if I did.

---

