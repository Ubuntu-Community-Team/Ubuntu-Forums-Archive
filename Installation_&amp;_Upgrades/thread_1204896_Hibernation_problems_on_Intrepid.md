---
title: "Hibernation problems on Intrepid"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by guedesav on 2009-07-05
Once again, more post-upgrade problems...

In Gutsy, I could hibernate neatly just using s2disk. It'd take mostly one minute to save the state and turn off. Now on Intrepid, I'm overrun with problems...

Some scrips, such as /etc/acpi/hibernate.sh just turn off my monitor for a while, start writing on disk and then get back to the OS, having done apparently nothing at all.

But the worst case is with s2disk and pmi("pmi action hibernate"). Both seem to start all right, the screen gets black and the system starts writing to disk just as it should. Then, after a little while, it stops altogethere. There's no more writing to disk, no matter what I do, and the system just stands blank forever(I've waited mostly 5 minutes, it should not take that long...).

Any guesses on where the problem is, or what should I use instead?

---

