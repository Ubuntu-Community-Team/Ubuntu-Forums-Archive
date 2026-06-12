---
title: "Kernel 2.6.28 crashes on startup"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by mic159 on 2009-05-05
Hey all,

I upgraded from 8.10 to 9.04, and it updated the kernel to 2.6.28 from 2.6.27, and now it crashes when starting up under the :Loading Hardware Drivers" part.
It spits out loads of text, but none of it seems usefull (well the end dosnt seem to be usefull). Where does it dump this info to? I looked under syslog and that boot isnt there, so im guessing syslog dosnt start till later in the bootup phase.

2.6.27 still boots fine, and 2.6.28 recovery mode works fine too.


So where does it dump all its info to?

PS, this is an old laptop, and it dosnt have X installed.

---

### Post by mic159 on 2009-05-10
BUMP???
I tried it on another identical laptop and this one gets stuck in a infinite loop dumping text to the screen and you have no hope of reading it because it scrolls so fast.

HOW CAN I READ THE OUTPUT TO FIND OUT WHATS GOING ON?
Is there a debug flag i can set in the kernel boot flags?

---

