---
title: "HP Officejet Pro L7590 Photo Printing"
date: 2009-06-16
forum: Hardware
---

### Post by Zelandeth on 2009-06-16
Only picked this up a couple of days ago, and thus far everything's been fine.

Using the HIPJS drivers the printer seems to behave flawlessly - except for when I try to print to a 4 by 6 photo - at which point the printer goes nuts, flashing all the panel lights and instructing me to switch it off an on again, then behaving as though it's been improprly shut down.

This appears to be unique to Ubuntu - as rebooting into Windows and printing from there results in prefectly sane behaviour when printing to 4 by 6's.

One of the main reasons for going for another HP printer was that this was listed on openprinting.org as "works perfectly" and that HP support is generally very good.

Any ideas?

---

### Post by Zelandeth on 2009-06-19
Solved.

This appears to be a documented bug in HPLIP which results certain printers crashing when photo paper is selected.

[Launchpad entry for bug #258487](https://bugs.launchpad.net/hplip/+bug/258487)

Upgrading to the current version of HPLIP directly has solved the problem.

---

