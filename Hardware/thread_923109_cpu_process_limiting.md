---
title: "cpu process limiting"
date: 2008-09-18
forum: Hardware
---

### Post by grungedoobie on 2008-09-18
Does anyone know a way to batch limit all processes so that no single process can be allowed to consume 100%?

I am sort of responsible for maintaining several older computers (one is on a mobo from 1995), and they are running just fine with linux (better than they did with the other other platforms 8-P to which I won't go back).

I'm not running into any serious problems with applications except for one DELL computer whose cpu goes "kerplunkt" when it reaches 100% for any length of time.  And another older laptop that gets super hot when running at 100% of the cpu.

All of the computers have linux of one type or another on them, and only one still has the other other on it.  (She paid for the programs to run on that OS, so she won't let it go)  However, even that one is dual bootable with linux because that other OS couldn't use the hard drive she got for her birthday.  Anyhow, that's not the question.

If anyone knows how to batch limit like that, I sure would love some pointers.

Thanks in advance,
The Grunge :guitar:

---

### Post by qstraza on 2008-09-18
cpulimit or nice? Check them out.

---

### Post by grungedoobie on 2009-03-23
Thank you for you help qstraza.  

This thread can be closed.

I've settled on just adding a toshset command to cron and every 5 minutes it sets the fan speed to high for the laptop.  That's probably the safest way to do it for the time being.  The desktop that crashes at 100% CPU seems to have a MoBo or CPU fault and is on its way out.

The computers are pretty old, and I doubt anybody else uses them for much more than an over-sized paperweight these days.  While I'll continue to use them to learn more about the way of the Penguin. 


The Grunge :-k

P.S.  Speaking of the Penguin, Anybody know if there are plans to put a couple Penguin emoticons up for use?

---

