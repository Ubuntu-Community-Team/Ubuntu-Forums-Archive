---
title: "[SOLVED] ACPI problem - causing pagefaults?"
date: 2008-08-04
forum: General Help
---

### Post by porchrat on 2008-08-04
Hi all

I don't know if this is the right place to post this.  If it isn't please let me know or let the forum staff know so that it can be moved.

Anyway I'm running a new Ubuntu 8.04.1 system and I've been experiencing a problem involving pagefaults.  At first I thought it was a java problem as seen in this thread: [http://ubuntuforums.org/showthread.php?t=867216]("http://ubuntuforums.org/showthread.php?t=867216") however now I'm not so sure.

I was looking through dmesg just to see if there was anything out of the ordinary and I got a few errors that are of concern:

```
[   40.288938] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  DA, should be D1 [20070126]
```

I'm running a MSI K9A2 platinum motherboard with an AMI BIOS v02.61 and I have seen threads on this forum regarding problems with the AMI BIOS on foxconn, MSI and ASUS boards.  However the threads are closed now and so I feel I need to ask in a new thread.

I've seen a few more errors in the dmesg that I have researched and they also seem like they are potentially related to ACPI problems.

```
[    0.000000] TSC calibrated against HPET
[   39.463975] Marking TSC unstable due to TSCs unsynchronized
```

Although this one I'm not so sure about:
```
[    0.000000] ATI board detected. Disabling timer routing over 8254.
```

Can anyone shed some light on the problem?  I desperately need some clarity on this.

---

### Post by porchrat on 2008-08-05
bump

---

### Post by porchrat on 2008-08-06
OK, so for those of you viewing this (hopefully at least a few people) I have an update.

I updated my BIOS (was version 1.2 now version 1.5) and that didn't eliminate anything, merely changed some lettering in the checksum.

I then turned off ACPI in the BIOS and that has removed the checksum error at least.  The other errors still persists unfortunately.  That and you have to manually turn off the PC after ubuntu has halted, but it's a small sacrifice to make for a more stable and error-free environment.

By the way the pagefaults still occur in case anyone was wondering.

Does anyone know of a package that can monitor pagefaults?  It would be helpful to know when these pagefaults are occurring.

Any comments would be helpful everybody.  I'm new to linux so you'll probably find I haven't tried the things you suggest.

---

