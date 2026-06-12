---
title: "Modem is Busy"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by Jerryonimo on 2007-09-10
Well, I tried to make a modem connection in KUbuntu Gutsy Gibbon.  I used KPPP to try to connect.  At first, I got the error message that said that "modem" could not be found.  I soon figured that out and fixed that error message, but then  when I tried to connect again, I got the error message that said "Modem is Busy."  Is it a compatiblity issue?  I looked on other forums, but the only solution I saw was to create a new ttyS device, but that didn't quite work, because MAKEDEV is lame.
Oh, and thanks in avance.

---

### Post by geraldm on 2007-09-11
Some applications create a lock file prior to dialing.
That lock file might not get removed, and the next attempt might find the stale lock
and give up without checking whether the process that has the lock is still active.
Check under directory /var/lock/ for possible locks.  
Such information should be found in the man page for the dialer you are using.

Gerald

---

### Post by Jerryonimo on 2007-09-11
Actually, I don't know what my modem is.  When I check lsmod, I can barely pick out my sound card.  (I did, though).

---

### Post by Jerryonimo on 2007-09-22
Auughrrrh! I'm frustrated!](*,)
Well, I know without a shadow of a doubt that my modem is compatible with Ubuntu, but I keep getting that "Modem is busy" window every time I query the modem in KPPP.  Please help![-o<

---

