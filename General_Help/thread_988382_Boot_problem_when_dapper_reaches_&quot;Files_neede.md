---
title: "Boot problem when dapper reaches &quot;Files needed to boot&quot;"
date: 2008-11-20
forum: General Help
---

### Post by KenSpeedie on 2008-11-20
I am running ubuntu dapper.  My motherboard recently went out and I had it replaced with an HP motherboard (HP d350, Pentium 4, 3000 Mhz).

Sometimes when it boots up and reaches "Files needed to boot", there is a long pause and then it completes the boot up sequence. I then get keyboard and video errors.  When I open a terminal it acts as if the F1 key is stuck.  When I try to enter anything into the terminal, the "File" menu drops down and won't allow me to make entries in the terminal.

When I open an excel file it gives me a strange looking cursor and excel has all kinds of strange behavior.

If the boot sequece does not hang up at "Files needed to boot" I don't have any problems.

Every time I boot up I have to wait to see if it's going to pause for more than a few seconds.  Every time it hangs, I turn it off and start over until it goes through normally. Problem is intermittent.  Sometimes it hangs once in very six trys and at other times it hangs every time or every other time. Does not seem to be any decerable pattern.

I tried to see if there was a boot log, but I did not find anything relevant in /var/log.

Possible GRUB problem?  I checked the /boot/grub/menu.lst file and discovered that the linux kernel was listed twice.  I commented out one set of entries.  It did not seem to make much difference (Yes I backed up the file before editing it!)

Is there somplace else that tells GRUB how to act?  It acts like it is trying to open something that is not there and gets confused.

Possible incompatibility issues between HP Motherboard and/or BIOS and Ubuntu?

Would an upgrade to Hardy help this problem?  I am reluctant to go messing with something I don't have to.  Everything runs great except the boot up problem (Don't fix something that ain't broke!)

Thanks for your help.

---

