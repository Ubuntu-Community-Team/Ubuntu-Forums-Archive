---
title: "Should I use internal or external drive for Ubuntu?"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by RogerGT on 2009-10-20
I have a 250 gig hard drive with heaps of space and a 250 gig external USB drive also with a lot of room on it.  Currently running Windows XP but would like to dual boot with Ubuntu (at least until I can give Bill the flick entirely!).

Simple question as a Linux newbie  and a bit apprehensive about partitioning my internal drive  -  can I easily install Ubuntu to the external drive and boot from there or should I take a deep breath and partition the internal drive?

Would the external drive need to be partitioned before installing Ubuntu?

:confused:

---

### Post by mikewhatever on 2009-10-20
> **RogerGT said:**
> ....

Would the external drive need to be partitioned before installing Ubuntu?

:confused:

Yes, any drive would. Installing to the external hdd is ok, but you need to know where to install GRUB, the boot loader. The default option is the first hdd, which is not perfect in case of an external hhd.

---

### Post by louieb on 2009-10-20
Just to add to mikewhatever. Either drive will probably need partition changes. The installer in most cases  make it simple to do.

if you install  on the external and you want to boot the computer without the external plugged in. You will have to use the advanced install option to change Grubs default install location.

:biggrin:Now my two cents. All things being equal Internal drive install is the way to go.  I don't use external drives. :evil:Took the one I got for Christmas last year apart and installed the drive internally.

---

### Post by mikewhatever on 2009-10-20
I also think an internal hdd is a better option. If you are intimidated by partitioning, practice first in a virtual machine.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by RogerGT on 2009-10-20
OK, thanks for the suggestions.  Time to take a deep breath (well, I'll wait for 29 October first)!  But I'll look at Virtual Box before I do.

*Linux is Not Windows* _is_ a good read, by the way.

Cheers,

Roger

---

