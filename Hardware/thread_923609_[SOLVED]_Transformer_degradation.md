---
title: "[SOLVED] Transformer degradation?"
date: 2008-09-18
forum: Hardware
---

### Post by KIAaze on 2008-09-18
I've been having a really strange hardware problem recently:
**When I plug in the power cord of my laptop after it's been off for a while, it takes about 1 minute before the light on the laptop goes on and I can push the power button!**

During all this "warming up" time, the transformer on the power cord and the PC make a slight humming noise.

Once the current gets to the laptop and the light goes on, the transformer makes clicking noises until I power on the laptop.

A few days ago, the "warm-up" time was about 10-15 seconds, now it's a bit more than a minute!

Has anyone else ever encountered such a problem?
Is there any way to fix this or is it irreversible hardware deterioration?

_Notes:_
-I've been using the laptop without battery for almost a year now. (battery dead)
-The clicking noise of the transformer when plugged in while the laptop is off has always been there.
However, the current transfer delay was fast enough. (1 second maybe)

_Hardware:_
Compaq Presario 2500
Pentium 4 at 2.4GHz
About 5 years old

_Other hardware issues I had:_
-I had an overheating issue last year which I fixed by opening up the laptop and cleaning it.
-CD player eject button stopped working some time ago (last year?). I have to use a paperclip to force eject.
-fsck failed today for the first time, but I managed to fix the disk by running "e2fsck -f -y -v /dev/sda5"

_Other:_
I tried this recently: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
```
sync; echo 1 > /sys/power/pm_trace; /etc/acpi/sleep.sh force
```
which failed.
I have no idea if the "RTC" got corrupted while doing that.

Just posting anything that comes to my mind which might have done something weird to my system...

---

### Post by KIAaze on 2008-10-17
Mmh, problem "partially solved".
I still don't know why it started to take longer to "warm up", but what I currently do is that I plug in the cable into the power outlet first (that's where a clicking noise starts) and then only into the PC.

(I forgot to mention this in my first post, but I always used to do it the other way around (PC and then power outlet) because I thought it was better.)

_Very late edit:_
I discovered that the problem was a contact problem inside the cable near the transformer. When playing around with the cable a bit, the computer tended to suddenly turn off.
It was propbably caused by wrapping the power cord around the hot transformer everytime I packed up my laptop.

In the end, I just bought a new power adapter, which wasn't that expensive. Now I'll make sure to not wrap the cable around the adpter. ;)

---

