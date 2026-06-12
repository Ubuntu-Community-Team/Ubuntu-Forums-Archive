---
title: "Best current solution to hard drive load cycle count problem"
date: 2008-12-22
forum: Hardware
---

### Post by TeutonJon78 on 2008-12-22
So, I've been a good little forum user and searched and read around and read the Wiki about this problem, but basically, it just started to confuse me even more, and there is a lot of outdated info out there (and even worse, new posts using old info).

Solutions I've seen:
1) forum - Gutsy and below - add acpi scripts to set the hdparm and leave laptop mode disabled ([http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570))
2) forum - Hardy and above - use pm-utils scripts and leave laptop mode disabled ([http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570) and [http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management))
3) Wiki on PowerManagement ([https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)) - Hardy and below - use laptop_mode and lots of workarouns
4) Wiki on PowerManager - Intrepid - just enable laptop mode
5) various website (all usually from 2007) - use the ACPI scripts

It seems from my readings that ACPI is the old method and should really only be controlling button presses and feeding events of elsewhere.  Laptop mode seems logical (kernel?), and pm-utils (HAL?) seems logical.

Discussion in [Bug #244838]("https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/244838") seems to be pointing towards just using the laptop mode and configuring based on that.

So, in Intrepid (8.10) and going forward, what is the optimal method for solving this issue?

---

### Post by TeutonJon78 on 2009-01-02
Hmmm...no replies.  Anyway, thanks to whoever cleaned up the Community Doc on Power Management to make it clearer about just enabling laptop mode.

I hope this is resolved in 9.04, as this issue has been around long enough with enough misinformation.

---

