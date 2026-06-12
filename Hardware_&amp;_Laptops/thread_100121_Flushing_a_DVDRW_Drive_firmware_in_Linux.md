---
title: "Flushing a DVD/RW Drive firmware in Linux"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by mendieta on 2005-12-06
Guys/Gals

I have an LG  GSA-4120B DVD burner, which stopped working all at once (actually in another distro). And I have no other drive in the machine. I tried to flush de firmware, no luck at all. I tried by using wine and running the fimware binaries LG provides (they are for windows XP or similar)

Any ideas ?

Cheers
Mendieta

---

### Post by mendieta on 2005-12-07
Let me be more specific:

1) Is it possible to restore the original firmware of the DVD drive from the hardware ? (like setting a jumper, etc., I couldn't find anything in the manual, so it probably isn't -- but note that you can reset a Motherboard from the hardware by setting the proper jumper to the right position)

2) Is there a good place to look for help in these situations ? (alternative/generic firmware for linux, etc)

3) If everything else fails, could someone suggest a well supported (and not expensive) DVD burner for linux ? (and one that doesn't die so soon :D)

As you can see, I have a strong feeling it is the firmware. This thing is one year old and with little use, I really doubt it is a hardware issue. 

Thanks a lot in advance 
Mendieta

---

### Post by davidsrsb on 2005-12-07
I think that you mean flashing, not flushing.
I would not trust WINE to be run a Flash upgrade program, try to use another PC running XP.
Most likely it is hardware failure, why would the firmware have got corrupted in the first place?

---

### Post by mendieta on 2005-12-07
[QUOTE=davidsrsb]I think that you mean flashing, not flushing.
I would not trust WINE to be run a Flash upgrade program, try to use another PC running XP.
Most likely it is hardware failure, why would the firmware have got corrupted in the first place?[/QUOTE]

Thanks David

Who knows, some time ago a Mandriva release would render some LG drives unusable. It was a bug in the drives, but a certain kernel call would fry them. At that time, the solution was to upgrade the firmware. And I resuscitates a CD drive some time ago by running the flash program from wine. Also, I read several posts on the net of people having problems dvd burning under linux with different drives, and some times upgrading to a newer firmware helps.

Oh, and I have no winPC at hand, I am 100% free software here (should I put a smilie here or a sad face ??)

---

### Post by teaker1s on 2005-12-07
most firmware upgrades can be done with a dos boot disk and the firmware program

---

### Post by mendieta on 2005-12-07
[QUOTE=teaker1s]most firmware upgrades can be done with a dos boot disk and the firmware program[/QUOTE] true (thanks) - though all of the upgrades for my drive are GUI programs for win, they have NO dos executable for these (and most LG) drives :(

---

