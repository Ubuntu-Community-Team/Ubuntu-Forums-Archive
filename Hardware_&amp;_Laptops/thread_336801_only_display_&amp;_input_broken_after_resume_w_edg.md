---
title: "only display &amp; input broken after resume w/ edgy &amp; beryl, ssh works"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by greg.hagen on 2007-01-12
Okay, so...

I recently reloaded Edgy on my Thinkpad x24. Everything works well out of the box besides Hibernate, which I don't use anyway. The thinkpad buttons, cpu scaling, suspend to ram, and even the little keyboard LED all work. If you are thinking of buying a cheap Ubuntu laptop, they are going for like $300 on craigslist. It even runs beryl surprisingly well, considering the antiquated Radeon M6 card.

The Problem:

The one thing that DOESN'T work is suspend to ram after beryl has been loaded. It would sometimes work (maybe 1/5 of the time) before I reloaded, but it doesn't work at all now.

After resuming, my network card turns on and blinks, my backlight turns on and everything seems to function normally, except the screen is blank and no combination of keys seems to do anything (except for the brightness buttons). I can still even ssh to the machine and shut it down remotely.

What I have tried:

-Shutting down beryl and loading metacity before suspend does not fix the problem
-Removing the new entries in xorg.conf does not fix the problem. However, I did not try removing "dbe" because beryl simply hangs without it. I want them BOTH working.
-"echo 3 > /proc/acpi/sleep" as root will suspend the machine without shutting off the backlight. on resume, everything seems to function normally except no form of input seems to do anything.

Any help, suggestions or ideas that anyone has would be welcome, even if it doesn't fix it. At least I'll have a larger list of what DOESN'T work.

If you can find a solution, there will be a 6-pack of Sierra Nevada Pale Ale waiting for you in Santa Cruz, CA. :D

---

