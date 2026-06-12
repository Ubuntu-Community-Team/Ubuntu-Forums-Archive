---
title: "LIVE CD boot speed (5.10)"
date: 2005-12-06
forum: General Help
---

### Post by Maciek on 2005-12-06
Hello all,

I'm new to Ubuntu, although not new to Linux (currently using Debian).  I'm also fairly new to Linux LIVE CDs.  I'm planning on trying out Ubuntu on a future laptop.  I fired up the Ubuntu LIVE CD to get acquianted with it, but I was perplexed at the length of time it takes to come up (>15 minutes... well, it's still booting actually, just getting the GNOME desktop now...; most of it spent past the point where it switches to graphical mode/splash).  I realize that LIVE CDs will take much longer than HDD installations, but surely not this long!  As a point of comparison, I've tried Knoppix LIVE CD earlier, and it came up to usable point in under 10% of Ubuntu's boot speed!  Am I missing something? :confused:

EDIT: although the original boot attempt failed to finish (stuck at desktop constantly loading stuff from CD) and gave a bunch of errors about being unable to load an applet (e.g., clock), a subsequent boot attempt managed to finish, to the point where the CD stops spinning, and I can interact with the system.  Still, the process was a bit lengthy... any tips on speeding it up?  In particular the GNOME loading bit (after the graphical login) took the longest, by far.

---

### Post by aysiu on 2005-12-06
Sounds like a bum Ubuntu CD. I've heard of even the official ShipIt CDs being badly burned sometimes.

I prefer to download them myself, check the integrity of the ISO, and burn it at a slow speed (4x).

---

### Post by Maciek on 2005-12-06
That's what I did (DL my own, check integrity, burn slow @ x8  ).  The fact that it came up fine the second time around I think suggests it's not the burn.  Perhaps the fact that the reboot was "warm" between both attempts has helped...

---

### Post by devwild on 2005-12-06
[QUOTE=Maciek]That's what I did (DL my own, check integrity, burn slow @ x8  ).  The fact that it came up fine the second time around I think suggests it's not the burn.  Perhaps the fact that the reboot was "warm" between both attempts has helped...[/QUOTE]
It probably is the cd, it just happens to be marginal enough that your cd rom is reading it properly sometimes. It could even be the media itself that the cd rom doesn't quite like (very, very common with cd-r media, especially cheap stuff)

---

### Post by Maciek on 2005-12-06
[QUOTE=devwild]It probably is the cd, it just happens to be marginal enough that your cd rom is reading it properly sometimes. It could even be the media itself that the cd rom doesn't quite like (very, very common with cd-r media, especially cheap stuff)[/QUOTE]

Hmm, interesting.  Is there any test that would allow me to find/confirm such bad burns?  Naturally, if this is the case, I'd be very concerned, so for future reference I'd like to have a test which would give me a definitive statement as to whether I can rely on the burn.  Wolud a simple "dd if=/dev/cdrom of=/dev/null" be sufficient?  (i.e., lack of errors in the operation indicating a successful burn)  Presumably I'd do this test on a bunch of different CD reader drives; the drive that burned it is not likely to complain about it...

---

