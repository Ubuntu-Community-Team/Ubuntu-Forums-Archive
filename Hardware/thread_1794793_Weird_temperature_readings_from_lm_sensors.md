---
title: "Weird temperature readings from lm_sensors"
date: 2011-07-01
forum: Hardware
---

### Post by Ranko Kohime on 2011-07-01
I've got a Clevo W150HNQ, running Xubuntu Natty, with the Core i7-2720QM processor.

I'm letting GMusicBrowser do ReplayGain analysis on my music, and while it's doing that, I'm getting some weird temperature readings.

GMB is not multi-threading for the RG analysis, so it's showing 12.5% CPU time for GMB in Conky (which is correct, as Xubuntu sees 8 cores with hyper-threading)

The temperature is normally in the mid-40's with my normal processes, and is wavering between 50-60C with GMB doing analysis.  But then I get spikes up to 97C.  I can't figure that one out, because the air coming out is not any hotter than at 50C.  Plus I don't have OS-control of the fan yet, so the BIOS is still controlling the fan, and it's not speeding up.

It's also hitting that 97C level while having a large fan pointing straight at it.

lm_sensors gives me 5 different readings, which I assume to be each individual core, plus the discreet Nvidia card, and all of them are going over 90C when the overall reading (as provdided by byobu) reads 97C.

I've previously run the Mersenne torture test, and had all 4 cores plus the 4 hyper-threads maxed-out according to htop, and even the temps leveled out around 80C.

The laptop is obviously not getting that hot, so I'm left wondering where in the hell it's getting it's readings from.  :confused:

Anyone got any ideas?

---

### Post by trevelyon on 2012-02-09
Don't mean to necro this thread but I'm getting some pretty unbelievable readings for temps as well on a clevo 170whr (basically, same model with same proc).  When I launch anything in optirun the temps go up to high 80's or 90 even.  The fan spins up and the air is warm but the laptop is not hot to the touch nor is the air THAT hot.  Any other way to test temps like this?  I really am beginning to doubt them.  Thanks,

---

