---
title: "Adding optical drives (After installation)"
date: 2008-06-24
forum: Hardware
---

### Post by russellchamp on 2008-06-24
Hey everyone!  Recently my desktop computer (Compaq Presario 600Z, FYI) totally bit the dust (I think it was the motherboard) so I've been canabalizing the parts and putting them into my other computers.  I tried to stick the DVD drive into another desktop that my family owns (Dell Dimension 4100).  I ended up swapping some of the drives around such that it looked like so...
     OLD               NEW
[  CD Drive ]     [CD-RW Drive]
[CD-RW Drive]  -> [ DVD Drive ]
[Floppy]          [Floppy]

My only problem now is that the devices were not automatically recognized and I get some errors when booting up which makes it take a long time to boot.  For right now, I've removed both CD entries from the /etc/fstab file until I know what to do.  I haven't been able to find any info, really, on installing optical drives. :-(
Anyone have some suggestions?

---

### Post by russellchamp on 2008-06-24
Sigh... NEVER MIND.  It just so happens that I am incredibly RETARDED.  One of my friends came over and showed me that I forgot to switch one of the optical drives to "master" 'cuz both of them were on "slave."  I'm still not sure why that was the issue, but now both drives work.
:lolflag:
Close thread, please.

---

