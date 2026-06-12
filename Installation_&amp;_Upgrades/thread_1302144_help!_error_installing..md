---
title: "help! error installing."
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by newasyouth on 2009-10-26
a friend gave me a toshiba laptop..satellite pro m15-s405...pretty sweet..it was giving him some problems..so i tried installing ubuntu on it, hoping it would work. alas it did not. an error message comes up..after alot of DOS (i think, im pretty wet behind the ears with computers) and the final line is (something like this):

[         0.0320821    Kernel panic - not syncing: Attempting to kill the idle task!



could someone lead me in the right direction please.

thanks alot
s

---

### Post by lemming465 on 2009-10-27
Some things to check, in this order

0) best bet CD is the "i386" (32-bit) live desktop CD

1) see if the CD passes the integrity self-test

2) run memtest86+ overnight (or at least 4 hours) and see if you have any memory errors

3) try booting the live desktop again

---

### Post by GGreen on 2009-11-08
I have the same problem.  I am trying to do a fresh install of Ubuntu 9.10 64 bit.  I am running 9.04 64 bit now.  The disk will not install or run as live cd.  I did the integrity test and said 1 error.  Unsure of what to do.

---

### Post by lemming465 on 2009-11-12
> I did the integrity test and said 1 error.Throw that CD-R away and burn a new one, maybe at a lower speed.  Preferably after [verifying the correctness of the .iso download using its md5 checksum]("https://help.ubuntu.com/community/HowToMD5SUM").
> The disk will not install or run as live cd
This is almost certainly due to that error.  This is a common enough problem with burned CD's that nearly everyone (Ubuntu, Debian, Fedora, Redhat, SuSE, ...) has a CD self-check boot option of some kind.  

Even if you manage to get through an install from an erroneous CD, the on-disk OS that results will be equally damaged, and will have subtle bugs that will tend to corrupt your files or break some programs.  Troubleshooting that sort of thing is a horrid nuisance, and you can avoid much future pain by getting a good CD burn to start with.

---

