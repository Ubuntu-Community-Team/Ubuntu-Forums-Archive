---
title: "Booting issue on Dell Inspiron 1100"
date: 2008-07-16
forum: Hardware
---

### Post by halyihev on 2008-07-16
Hi all,

I have an odd one.  I have a Dell Inspiron 1100 laptop that has been running Gutsy for some time, quite happily.  I use it constantly as my primary machine.

About a month ago, after running some set of daily updates (unfortunately I don't remember exactly which one!) I began having the problem that when I boot, it gets to the point of apparently starting X and gdm, and just hangs.  I get no X cursor or login or spash.  Everything up to that point has looked normal.

Sounds like X - except that if I boot to recovery mode and do *nothing* but reboot, it comes up fine.

Upgraded to Hardy, thinking maybe that would replace whatever might have gotten corrupted.  The Hardy liveCD boots just fine, but I still have the problem.

Thought it might be my PCMCIA wifi card, since I'd read of there occasionally being issues if those were inserted at boot.  That worked a few times, but not other times.  Likewise I have *some* times where it boots just fine, but the vast majority I have to start in recovery and choose "reboot".

Tried taking the VGA= (frameset stuff?) off the kernel line, since that is not on the recovery mode boot in menu.lst.  No joy.

Anyone got any suggestions where else to look?  I could probably just format and rebuild, but I hate to do that since that's quite a time investment getting my setup back as it is now.

---

