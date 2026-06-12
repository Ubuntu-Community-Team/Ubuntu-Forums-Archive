---
title: "Hiberate and Frequency Scaling"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by hpklett on 2006-08-07
Hi all, after a hibernate, the second cpu on my dual core gets switched to the "Perfomance" governor.  The first CPU is fine, so I'm thinking that there's a script somewhere that "reinitializes", and isn't aware of multiple processors.  Has anybody else experienced this, or have an idea where to look?

Also, does anyone prefer "conservative"?  Is there a way to switch governors when I go to battery?

Thanks, and sorry for the n00b stuff; I've never owned a laptop before :).

---

### Post by elwood_j_blues on 2006-08-15
Yes, you can. You could for example deactivate the powernowd daemon and put two scripts into /etc/acpi/battery.d and .../ac.d respectively that look like this:

[INDENT]#!/bin/sh
/usr/bin/cpufreq-selector -c 0 -g powersave
[/INDENT]

With the governor you want to choose in there.

I didn't test that, but I think that should work.

---

### Post by hpklett on 2006-08-15
Thank you for your reply; apparently my problems are a little more complex.  I tried your suggestion, but I now realize that switching governors renders my keyboard useless and doesn't allow me to shutdown.  I guess some things are still a little voodoo on the Dell D620's.  Hibernate and suspend usually work fine, but sometimes all sorts of things go awry.  I guess I can't really complain about anything in the hibernate department until I resize my swap (:oops:), but suspend shows the same stuff occasionally.

Thanks again

---

### Post by wasteed on 2006-08-16
I had the same problem once after a suspend on my Toshiba Tecra M5 ([http://www.ubuntuforums.org/showthread.php?t=222921#6](http://www.ubuntuforums.org/showthread.php?t=222921#6)). Using the CPU frequency monitor applet to try and force it back into userspace, rather than performance, had no effect. In the end I had to reboot...

---

### Post by hpklett on 2006-08-17
If only the time and knowledge, I'd be debugging the crap out of it now :(.

---

