---
title: "SATA drive while not detected by BIOS, reset issues?"
date: 2008-09-06
forum: Hardware
---

### Post by Hellkeepa on 2008-09-06
HELLo!

To make a long story short: I had a mainboard that fried its southbridge, due to "heavy" HDD-load. Since then, my Seagate Barracuda ST3750640AS has been acting up on cold starts. Causing the SATA controller to time out when trying to detect it, and the kernel to give "errno=-16/-19 SRST/COMRESET failed". After this message it'd wait for about 2 minutes, for trying again, with the same error, until it'd give up after 10 minutes or so. (Never bothered with timing it..)
However, by turning the PC off again and moving the SATA cable, the HDD would work flawlessly. At least until the next cold start.

This behaviour is the same on other PCs as well, so it's confirmed to be the disk itself.

The nature of the problem, as well as some articles/threads I've read on this sort of issue, seems to indicate that the SATA drive isn't shutting down properly. Which is why I want to try and *manually* send the proper commands to shut the HDD down, via manipulating the SATA controller, before restarting the PC. I've been looking at [cfgadm](http://docs.sun.com/app/docs/doc/816-5166/cfgadm-sata-1m?a=view) for a solution on how to do this, but I'm afraid my knowledge of how to use this is rather limited.

My error message is the same as this one, except for the fact that my SATA drive doesn't contain my boot partition:
[http://lkml.org/lkml/2008/8/29/221](http://lkml.org/lkml/2008/8/29/221)
It does, however, dump me to the error console. Since it can't communicate with the drive, and it is listed in fstab.

My lspci: [http://rafb.net/p/vYePm852.html](http://rafb.net/p/vYePm852.html)
Motherboard is a Gigabyte GA-MA770-DS3, with 1 500 GB SATA HDD and 1 SATA DVD-burner attached to it as well; Both working regardless of the 750 disk failing.

Let me know if any more info is needed. Currently I'm waiting for the replacement drive to arrive, before reconnecting the HDD, but I'd sure like to be able to save the 400-500 GB of data I have on it.

Thanks in advance. :-)

Happy surfin'!

---

### Post by Hellkeepa on 2008-09-08
HELLo!

Since it's been two days without a reply: *Bump*
Hope someone can offer me some advice and/or assistance on this one.

*Edit, added (15. sep. 2008 ):*
As the drive was detected properly, after a couple of days of "cooling down", and I was able to move the data from it, this thread isn't needed anymore. Though, if anyone stumbles across this later on; The knowledge would certainly be appreciated, at least by me. ;-)

Happy surfin'!

---

