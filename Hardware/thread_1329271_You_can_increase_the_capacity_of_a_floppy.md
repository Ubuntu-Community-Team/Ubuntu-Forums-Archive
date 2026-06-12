---
title: "You can increase the capacity of a floppy?"
date: 2009-11-17
forum: Hardware
---

### Post by argos3016 on 2009-11-17
Well, I writed a lot of times, imgs to a floppy with dd comand. And i remember that with some images the floppy capacity increased.
It maybe help: something about ¿(minus bytes for cylinder)?
So, anyone knows how to make "bigger" a floppy?

---

### Post by i.r.id10t on 2009-11-17
Well, the old floppy floppies we used a hole punch to make 'em double sided :)

But yes, you can cram about 1.7mb onto a 1.44mb floppy by doing weird things - your drive has to support writing to it in that fashion.

Also, if you go to old hardware again (but newer than floppy floppies) IBM used to offer a 2.88mb 3.5" floppy drive and disks, it could also read the 1.44s.

---

### Post by argos3016 on 2009-11-19
Thanks

---

### Post by dandnsmith on 2009-11-19
I'm working with a fading memory but:
- the mode the floppy is written depends (or used to) on the precise device name (so look in /dev for fdxxxx)
- a lot of the newer, and mass-produced, cheaper floppy drives just aren't built to allow the higher density to be written and read without error. I have a program under Windows which can, effectively, test the drive by formatting it for higher density writing (and testing it at the same time).

HTH

---

