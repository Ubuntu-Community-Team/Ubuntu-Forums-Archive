---
title: "dvd never stops spinning: new in Gutsy"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by eeried on 2007-11-23
Hello,

I installed a recent DVD burner on a PIII, with Xubuntu. I seem to remember setting DMA on the burner and reading DVDs was very smooth.

Now I upgraded to Xubuntu Gusty, and  I watched a DVD: it never stopped spinning and DVD playback was a bit glitchy: a slight freeze now and then (this may be due to the TNT nvidia  graphic card not being good enough for the 15" screeen?).

Of course as you now all know Gutsy sees the burner as /dev/scd0 though it is an IDE device, just as it sees the old battered HDD as /dev/sda (what a laugh).

However udma2 is set on both the HDD and the burner according to hdparm -i.

Of course a spinning DVD may be an exception and I'm gooing to read other DVDs... So I tried another DVD and it spun silently in a normal way.

Cheers

---

### Post by eeried on 2007-11-23
How can I reduce the speed of the "bad" DVDs?


Is udma2 enough for a recent dvd-burner?

cheers

---

### Post by logos34 on 2007-11-23
I noticed this too after the upgrade (ubuntu here), but it seems to be limited to Totem movie player, and only with certain discs at that.  No problem with other players.

There are controls on some players for drive speed 'slowdown' with audio cds, but I can't find any to control dvd.  hmm

---

