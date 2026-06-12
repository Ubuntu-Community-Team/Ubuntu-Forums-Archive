---
title: "System update disabled CD-ROM drive"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by RickNak on 2007-05-30
The last automatically distributed update that required a system reboot ended up disabling my CD-ROM drive.

I had left my 7.04 CD in the drive, and would pick 'Boot from first drive' on reboots.  When logged in, I would have an icon on the desktop for my 7.04 CD that was in the drive.

After the reboot-required update, the icon was gone.  Trying to view the CD-ROM drive showed a 'CD-ROM drive' and a 'CD-ROM 1'.  The former said there was no media, and the latter said that special device /dev/scd0 did not exist.

The CD-ROM drive does work; I booted off the CD before starting up the system.  I also have not made any system changes in several weeks, and nothing ever to do with the devices.

How do I start to troubleshoot this problem?

Rick

---

### Post by merlinus on 2007-05-30
Your cd-rom may now be /dev/hdc.  That's what mine changed to after the kernel upgrade.

-merlin

---

