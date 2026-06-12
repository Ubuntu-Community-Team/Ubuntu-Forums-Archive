---
title: "Epson R220 stops working"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Mark Phelps on 2007-06-01
Good news is that I was able to install my Epson R220 printer using Feisty simply by using the Add Printer dialogue.  Having read forum posts about others not being able to detect their Epson R220, I was pleasantly surprised.  But after printing three sets of web pages (from Firefox), when I tried to print a fourth set, nothing came off the printer.  When I checked the printer, Feisty claimed that there was one pending job.  It also asked if the printer was paused.  I paused and un-paused it, with no effect.

So, again following what I had read in the forums, I removed the printer and attempted to re-add it, but this time, Feisty did not detect any printers.  The Epson is connected through a USB port directly to the PC.  Feisty had no problem detecting it the first time.

Being brand new to Linux, I wasn't prepared to have my printer "vanish". Also, I expected that re-adding it would work.  I read lots of material about the huge assortment of Linux drivers available for lots of hardware.  My sound card doesn't work at all (Bluegears b-enspirer using the CMI8788 chip). And now, I can't print anymore.  I guess I should be thankful that I get a working display using my ATI card.

So, is this printer "vanishing" stuff a routine problem -- and easily fixed?:(

---

### Post by hummingbird59 on 2007-06-01
I suggest that you check out launchpad [https://bugs.launchpad.net/](https://bugs.launchpad.net/).  There may be a bug (look at 104166 for instance, not exactly the same but....).  Also, go to [http://localhost:631/](http://localhost:631/) to see if you can manage your printer from there.  Good luck!

---

