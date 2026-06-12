---
title: "T61p will not completely shutdown with 4Gb ram"
date: 2008-05-01
forum: Hardware
---

### Post by arsenix on 2008-05-01
My machine has been working flawlessly until recently when I upgraded to 4gb ram (had 3 before).  Now the machine does not completely turn off after shutdown or suspend.  The machine shuts down almost completely, but one of the lights stays on and the fans are still running.  I must power cycle it to bring it back.  Oddly enough it seems to be able to shutdown fine if I am using a small amount of memory, although I am unsure of the exact amount.  If I shutdown right after I boot up it works fine.  In any case this never happened before (even once).

I am running 32bit Gutsy.(kernel 2.6.22.9)  I built and installed a custom PAE enabled kernel (hoping this would fix it and to get my extra gig of ram available) but that did not seem to make a difference.  Downgrading the machine back to 3Gb makes it work again.

Nothing of note appears in the logs, and I tried using a serial console to watch the final stages of shutdown.  Nothing interesting came up there either.  (I repaired my windows install as well to test and sure enough windows can suspend/shutdown fine even with the 4gb installed)

Anyone see this before?


James

---

### Post by arsenix on 2008-05-03
I have solved the issue.  Apparently JFS filesystem + 4 Gb RAM equals unable to power off.  Very odd but fully repeatable.  It only occurs after I have used the machine for a while, but never happens now that I have ditched JFS.  The clue was that after hard powering the machine, the JFS filesystem would have errors on it and need to be manually FSCK'ed.

James

---

