---
title: "Discrepancy between Sensors CPU temp and BIOS CPU temp?"
date: 2009-07-15
forum: Hardware
---

### Post by kwabena39 on 2009-07-15
Hello,

I have a Intel Q8200 Quad Core, running Ubuntu AMD64 bit version of Ubuntu 8.04.


My Sensors, at the top of the screen say 58 C, 51 C, 54 C, and 54 C, for each core at idle.

But when I go into my BIOS under PC Health status, it just gives one temperature: CPU temp of 26 C.  It gives another temp of 48 for System temp.

What does this all mean?  Why are BIOS temps and Sensors temps so different?

Also, are the temperature readings I'm getting in Sensors too high, for idle?

Note: It's been hot here lately in my room where the computer is.  It's been going back and forth between 70 F and 85 F.  So ambient temperature might have something to do with it.

If my temps are so high, why are they so high?  I looked in "Process" and everything was sleeping except for Gnome Desktop.

---

### Post by SuperSonic4 on 2009-07-15
I would be inclined to say it's because of load on the processors - running the BIOS is very simple for a computer but running a desktop isn't. You can look at load using the *top* command.

---

### Post by kwabena39 on 2009-07-16
are these temps high?  or normal?  should i worry?

---

