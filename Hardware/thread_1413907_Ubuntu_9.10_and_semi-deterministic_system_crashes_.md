---
title: "Ubuntu 9.10 and semi-deterministic system crashes when X starts up"
date: 2010-02-23
forum: Hardware
---

### Post by rpoko on 2010-02-23
Hi everybody,

I put this in the hardware forums as it sounds like being related to hardware.

Not a long ago I stumbled into a rather weird problem while upgrading my moms desktop from 7.04 to 9.10 (well clean install from CD actually). The new install went otherwise nice but I had to re-create Grub as there was no boot menu.

The actual problem is something I have never seen before and haven't really found any clues to, maybe because of not being able to find the right words for it.

The system almost always crashes when X attempts to start up. Crash symptoms are, no signal to the monitor, keyboard ceases working (no reaction to caps/number lock).

I did about a hundred reboots in order to find a pattern and this is all I've found out:
- When I do a normal system startup, after Grub I get to see the Ubuntu logo for a few seconds, then the system crashes.
- When I do a system recovery startup, I can get the terminal and log in. But when I say 'startx', the system crashes.
- If I leave a CD in (this part is what I really don't understand), the system manages to start up about 75% of the times. About 25%, it still crashes.

I dug around a little bit and found that xorg.conf no longer exists but 'is created on the fly', this has made me suspect that something goes wrong with hardware recognition and a 'faulty' xorg.conf gets often written. However I could be wrong.

Any ideas on how to debug this one?

---

### Post by rpoko on 2010-03-01
Anyone?

I need to get this solved somehow..

---

