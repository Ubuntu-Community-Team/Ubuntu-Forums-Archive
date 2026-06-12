---
title: "hellllllppppppp...i am stupid"
date: 2008-10-30
forum: General Help
---

### Post by unnati on 2008-10-30
ok

i was getting a lot of dependency problems for libc6...umm so i kinda got irritated and did
dpkg -i --force-depends -r libc6

NOW NOTHING WORKS
it keeps on saying /usr/bin/apt-get : no such file or directory
the file manager, control panel, internet...nothing opens up

how do i geteverything to work again?? or did i mess up bigtime??
plz..plz help

panicky unnati:confused:

---

### Post by snova on 2008-10-30
You're screwed. libc is as important as it gets, except for Grub and Linux (and possibly a few other things).

Reinstall.

---

### Post by unnati on 2008-10-30
how do i reinstall it??

i tried dpkg -i /var/cache/apt/archives/apt*
but it keeps on saying /usr/bin/dpkg: no such file or directory

even simple commands like ls, mkdir, sudo etc don't work
and this was all on my nokia n810...did i turn it into a paper weight???

*tears*

---

### Post by adaptr on 2008-10-30
Where on earth did you get that command to even run ?
Oh well, this was your first big lesson: DO NOT run commands you don't understand, or know what the outcome will be.

---

### Post by unnati on 2008-10-30
people...i feel bad enough...can any1 please figure out a solution????

---

### Post by jocko on 2008-10-30
> **unnati said:**
> how do i reinstall it??

Back up your home directory, boot from a live cd and reinstall the entire system.
That's probably the only way to turn your computer into anything else than a paper weight.

---

### Post by Balinus on 2008-10-30
Download (from another computer) Ubuntu 8.10 on a USB drive.  Then boot on your screwed computer with the USB drive.  Back-up everything you need, then install from USB drive?

Verify you can install from USB drive as I'm not sure you can.

You could also borrow (or buy since your CD/DVD doesn't work anymore) an external DVD drive.  Most computer can boot from the external drive.  

As it was said, don'T use command you don't understand on a "production" computer.  If you want to test commands, use another computer!

Good luck!

---

### Post by snova on 2008-10-30
> **unnati said:**
> how do i reinstall it??

You can't. libc is extremely core to the system. I'd be shocked if you could even turn your computer on, it's that important. Virtually every program and library on the system depends on it in one way or another. And now it's gone.

Download 8.10 however you can, boot to it, backup, and reinstall. And never --force anything again! It doesn't usually help anyway.

> **unnati said:**
> *tears*

Sorry. :(

What were these dependency issues, anyway?

---

### Post by unnati on 2008-10-30
woooooohooooo...i was able to get the software for n810 from nokia website...so my n810 is no longer just a paper weight!!
yippeeeeeeeeee...*gonna eat a cake* :-)

anyways as far as the dependency issues were concerned...here is the link

[http://ubuntuforums.org/showthread.php?p=6054258#post6054258](http://ubuntuforums.org/showthread.php?p=6054258#post6054258)

i still haven't been able to solve them

but thanx a lot all u guys!!

cheers and happy halloween
unnati

---

