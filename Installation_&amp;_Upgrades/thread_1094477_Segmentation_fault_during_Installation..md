---
title: "Segmentation fault during Installation."
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Goth Crayon on 2009-03-12
I'm am trying to install Ubuntu 8.10.
I have already:

Attempted to install after a total HDD format.
Attempted to install from boot after installing WinXP.
Attempted to install in "safe mode"
Attempted to install via Wubi.
Attempted the "Alternate Install".
Attempted to install earlier versions of Ubuntu.
Removed the video card.
I used an Ubuntu distribution copy.
Downloaded a new .iso, burned to cd at x4 speed.
Disc-checked BOTH copies, both passed.
Ran Memory Checker.
Used several command line parameters (nolapic, acpi=off, pci=noapci, irqpoll, splash, quiet, etc).

Every time I initialize any function (install, try without install, etc), the installer hangs and eventually displays the following:

[B]Segmentation fault
/etc/init.d/rc: 372: sh: Permission denied
init: Unable to execute "/bin/sh" for rc-default: Permission denied
init: rc-default main process (####)* terminated with status 255
[/B]

I've scoured the boards, but there's been no fix... mostly replies of "Didya burn the CD reeeeeal slow?"

As a test, I made a copy of Linux Mint. Interestingly enough, it had the same result -hangs at install, due to rc-default main process terminating with status 255.

*Meh?*[COLOR="DarkRed"][COLOR="#8b0000"]****[/COLOR][/COLOR]

---

### Post by wpshooter on 2009-03-12
When you say that you disc-checked both copies, are you talking about the integrity check that is found on the initial Ubuntu boot screen menu ?

If you did the above check and still can not get to install, here is what I would do.

First I would make sure that my CD drive firmware is at the latest and greatest version.  After doing that I would then attempt to install again.  If it still fails to install, I would get [www.killdisk.com](www.killdisk.com) and WIPE my hard drive completely clean and then try the installation again, from the ALTERNATE CD version of Ubuntu.

Good luck.

---

### Post by Goth Crayon on 2009-03-12
I am speaking of the Ubuntu boot's integrity check.

I hadn't thought about the disc drive's firmware, I'll give that a shot.

Also, thanks for the link.

Here's to hoping it works.

---

### Post by Goth Crayon on 2009-03-12
That's a negative.

Updated drivers to latest, formatted the crap out of the HDD, and I'm still getting SegV.

Poopy.

---

### Post by wpshooter on 2009-03-13
Was it the firmware that you updated (not same as drivers) ?

Did you WIPE the hard drive or did you just do some type of formatting ?

Have you tested the integrity of your hard drive with the hard drive manufacturers hard drive diagnostic software ?

---

