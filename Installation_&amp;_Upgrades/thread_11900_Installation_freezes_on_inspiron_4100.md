---
title: "Installation freezes on inspiron 4100"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by dstrebel on 2005-01-20
I get to the point on where to choose lanaguage and after choosing computer freezes. It's not the cd because I have installed it on another computer

---

### Post by coldcoldcold on 2005-01-20
i have an inspiron 8000.  ive seen in other posts that this will work (and has worked for me when mine locked up)

at the boot: prompt type:

linux noapic nolapic vga=771

you can also find those instructions by hitting f1, then f5

---

### Post by dstrebel on 2005-01-20
that worked great thanks!

---

### Post by mjcummins on 2008-02-20
Thanks for this information, had the same problem with Ubuntu 7.10 Desktop installation CD.
I just hit F6 added your "noapic nolapic vga=771" after the -- and hit return.
Now it's working on my Dell Inspiron 4100... well, so far.  I'm in the middle of my first installation of Linux for 7 years..  
Mick

Bowen QLD

---

### Post by mjcummins on 2008-02-20
OK...  See above post..  Didn't get too much futher...

Used the extra switches above, and at least I got past the Timezone maps.

Then very very slowly the Keyboard layout screen appeared..   But I didn't get a chance to select anything.. I didn't press "Next" and the machine (CD Drive) took off, and finally "Starting up the partitioner" screen appeared.  

After half an hour it got to 26%, an hour later it was still there..

But the whole time the CD-ROM is spinning like it's going to explode..

What the..  I thought Linux had got friendlier in the last seven years..

Help

Michael C in Bowen QLD Australia:confused:

---

