---
title: "Ubuntu hangs with LiveCD??"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by Howitzer17 on 2005-12-30
I'm trying to boot with the liveCD (5.04), it boots fine until it gets to "preparing for live session", in the part where it states "creating user" (63%), the boot just hangs... any idea why?  I am trying to retrieve some data off the two hard drives.  I tried booting with Knoppix 3.3, it hangs too...

Intel 933 Mhz., PIII, 256 MB RAM, 2 10Gb HDD...

Howitzer

---

### Post by bikeboy on 2005-12-30
5.04 is the previous release. You could start by trying 5.10 Breezy and see if that does any better. A lot of work was done on hardware detection between the two releases.

---

### Post by mit on 2005-12-30
Hi,

I take it you are trying to recover data from a Windows install using the Live CD?
If so, what happens when you boot without the live CD?

---

### Post by Howitzer17 on 2005-12-30
I removed the two hard drives from my dinosaur PII, 450 Mhz. machine and installed them in my PIII, 933 machine.  I am trying to recover the data so i can install Windows XP (put the data I want on the slave drive).  When it tries to boot from the old install of Windows XP that is presently on the master drive, it just tries to boot ("Start Windows Normally"), then just keeps restarting... it it gives you the option of starting in safe mode, etc... (safe mode doesn't work either)... hmmm...

Howitzer

---

### Post by Howitzer17 on 2005-12-30
from this posting ([http://ubuntuforums.org/showthread.php?t=37067](http://ubuntuforums.org/showthread.php?t=37067)) I tried this:

**livecd nodma nocddma noapic nolapic verbose**

It gave me the error message: "could not find kernel image livecd"

???

---

### Post by Howitzer17 on 2005-12-31
anyone else have an idea what the problem could be?

---

