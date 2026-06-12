---
title: "HDD takes too long to spin up"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by katoodifaas on 2007-10-11
Hi,

This is not strictly a question pertaining to Ubuntu, but I was wondering if someone could help me nevertheless. Now, I have two identical SATA HDD's on my system. The problem is that when turning on the computer, the secondary drive (where I keep my data - films, pictures etc.) spins up first and the primary (system) drive spins up only after the first one is going at full speed.

The trouble is that BIOS doesn't detect the system drive in time, attempts to boot from the wrong drive, I have to reboot and manually change the boot priority in BIOS settings every time when switching on the machine.

These are Hitachi drives, I found no software to correct the problem on their website and tech support just didn't answer my e-mail. So if anyone knows a solution to this annoyance, it would be highly appreciated.

---

### Post by tgalati4 on 2007-10-12
They're called Hitachi DeathStars for a reason.

Perhaps your power supply is not providing enough current.  Once the first drive spins up, the current recovers enough to allow the second drive to spin up.

There may be a firmware upgrade from Hitachi available.  There may be an hdparm parameter that controls spin-up. (man hdparm for details)

I assume that you have bootable partitions (and operating systems on both drives).  Put some more devices in your boot chain:  Zip drives, floppy drives, CDROMs.  Give the machine something to do until the DeathStars spin up.  Put a music CD (preferably heavy metal) in the CDROM to give the machine some motivation.

---

