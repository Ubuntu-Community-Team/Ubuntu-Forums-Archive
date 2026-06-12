---
title: "Hard Disk too large problems"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by UKDragon on 2007-03-04
Trying to install ubuntu on an old HP E-Vectra I have (Model P2707A) to run as a file server/download box on my home network.  I whacked a 200gb drive in it for this purpose.

ubuntu installs, but when it tries to boot up I get error18 as the drive is too big.  Its a rubbish BIOS which wont let me change from LBA, Im told the max supported is 40gb - though it didnt have any problems with an XP install on the 200gb.

Is it going to be easiest just to partition the drive? and if so as long as main partition is under 40gb does it matter if other is larger? - I'd rather not have loads of partitions on it.

Sorry for noobish questions, and thanks in advance for any help/suggestions you can give.

---

### Post by lonce on 2007-03-04
Just a thought, but if its an older system with a newer hard drive, maybe the bios is having an issue and not the software.  If it installs with no issues then I would think its the bios or hardware.  I am probably wrong though.

---

### Post by UKDragon on 2007-03-05
Thanks for the reply but that was kinda my point.  Its the BIOS issue, but Im looking for a way to get around it.

---

### Post by UKDragon on 2007-03-05
For Reference, in case anyone else has same problem.

Solved by partitioning the hard drive 40gb "/" 1Gb "swap" and 159Gb "home"

---

