---
title: "[SOLVED] Added RAM, shows LESS?"
date: 2008-08-21
forum: Hardware
---

### Post by EvilMarshmallow on 2008-08-21
I had 2x1 GB RAM in my laptop, a Dell Vostro 1500.

I replaced it with 2x2 GB.  Now when I look in System Monitor it shows 1000 MiB!  I know that 32-bit won't see more than 3 GB, but what gives?

---

### Post by sdennie on 2008-08-21
I would check the BIOS and see if it's seeing all 4GB.  If not, you may have seated the RAM improperly.  Also, you can get all 4GB to work with a 32bit version of Ubuntu.  See: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by EvilMarshmallow on 2008-08-21
Yeah, I knew about the 4 GB thing.  I'm going there next.

The BIOS didn't recognize it.  I reseated, nothing happened.  I ended up trying the diagnostics in the BIOS, you know how Dell says "the amount of memory in your machine changed, press F1 to continue", etc... and I pressed F5 for diagnostics.  They all checked out ok... and then magically it started recognizing it properly.  So the problem is solved!  Thanks!

---

