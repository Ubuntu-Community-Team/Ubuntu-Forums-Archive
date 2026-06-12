---
title: "noob help just recently upgraded to 9.10"
date: 2010-01-13
forum: Hardware
---

### Post by deangamblin on 2010-01-13
So I upgraded from 9.04 to the 9.10 Karmic Koala this afternoon, basically graphics card not working, I have no sound either and my mouse pad isn't working either. only problems I've found so far.
Dell Inspiron 9400
ATI Technologies Inc Radeon Mobility X1400 (graphics card)

Any help is greatly appreciated, oh yeah and the quicker response too as well.

---

### Post by adam814 on 2010-01-13
Hmm...off the top of my head I'm guessing the graphics issue could be that you're trying to use fglrx, which hasn't supported r500 series ATI cards like that since around March of last year.  If so just remove it and use the "ati" driver from the repos (probably installed anyway).

Run alsamixer in a terminal to see if any of your sound channels are muted.  I've been fooled by that before.

I've never had touchpad issues.  Most of them are sufficiently Synaptics-like to work with the same drivers.  Just as a thought I know some laptops have either a button or BIOS option to disable the touchpad.

---

