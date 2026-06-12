---
title: "ThinkPad T40 - tirals, goods, bads"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by mperry on 2007-11-05
Judging from the similar threads, more than a few people are having issues.  I've read that it could be SLAB versus SLUB, that the ATI drivers may be at fault, and more than a few helpful suggestions to edit or add lines to menu.lst files.  I think I've tried a few combinations now on my T40 but Gutsy just will not successfully resume about 30% of the time even with the S3 bios thing appended in grub.  I have also changed /etc/default/acpi-support to standby instead of suspend and the laptop really suspends fast now but I think it takes a hit in power use.  I've also tried a few different methods of suspending and wanted to gather a few basic statistics from folks with T40s:

suspend using the lid close - does this work  for you guys?  Not so much suspend events but resume?  Most of the failures I see seem to occur with lid close/open events.

Fn-F4 suspends - what about this one? successes versus failures?

Hibernation - I could not use uswsusp because it really did not fix things at all so I went back.  Does hibernate work from the gnome menu option?

What grub/menu.lst hacks have you tried?  Successes there?  I'm using the S3 bios one.  Don't recall it all because I'm at work now and away from the laptop.

What bios are you using?  I'm using the latest one on IBM's website which is dated this year.

What about when its plugged in versus on battery?  Any differences there?

Finally, an issue perhaps only with my laptop and as someone points out the problems are consistently inconsistent.  What about the amount of time you leave your thinkpad suspended? Lets just say you leave it overnight for 7 hours.  Does it come back?

The whole thing is rather frustrating because when it works good, it just kicks.  But it always seems to fail when my wife wishes to use the laptop and she really has no idea what the deal is.

---

