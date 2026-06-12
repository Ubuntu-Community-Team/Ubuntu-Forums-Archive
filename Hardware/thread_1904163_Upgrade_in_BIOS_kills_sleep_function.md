---
title: "Upgrade in BIOS kills sleep function"
date: 2012-01-04
forum: Hardware
---

### Post by patman0623 on 2012-01-04
I am using an HP p6710f. I upgraded the BIOS version from 6.06 to 6.07 by restarting into Windows and executing the file provided. Oddly, since then, when the screen goes turns off in Ubuntu after a time of inactivity (as it is programmed to do), it doesn't come back when I jiggle the mouse or press a key. I have to hold down the power button or navigate blindly to the ctrl-alt-f1 screen and type in the sudo shutdown -r 0 command (yes, I was able to do this - after doing so, the display came back on, but only to show me the shutdown sequence).

Why is it doing this, and is there any fix? Is it something to do with the compiled kernel not knowing about the new BIOS?

---

### Post by carl4926 on 2012-01-04
I have to ask
Was a BIOS update necessary?

---

### Post by patman0623 on 2012-01-04
> **carl4926 said:**
> I have to ask
Was a BIOS update necessary?No. But really, hindsight is 20/20, now isn't it?

---

### Post by carl4926 on 2012-01-04
It should be easy enough to put the older BIOS version back.

BIOS is generally best left alone unless you are actually trying to solve a troublesome issue which might have it's solution in such a step.

---

### Post by Mark Phelps on 2012-01-05
> **patman0623 said:**
> No. But really, hindsight is 20/20, now isn't it?

Hey, don't feel alone in this ... I used to do BIOS upgrades all the time when I was using ASUS boards.  Never had a problem resulting from a single upgrade in YEARS.

Then, I switched over to a Gigabyte board.  I noticed the BIOS was really old, so I did a "routine" update -- and suddenly, it would not boot anymore.  I had to slow down my 1600-speed system memory to 1066 to get the board to boot again.  Not happy about this!

Reflashed back to the original BIOS version.  Able to set the memory back to 1600 again.

So, we all get caught with surprises when we do simple updates.

---

