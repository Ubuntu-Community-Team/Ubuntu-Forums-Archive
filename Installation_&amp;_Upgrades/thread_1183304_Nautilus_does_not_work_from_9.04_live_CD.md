---
title: "Nautilus does not work from 9.04 live CD"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-09
I have booted to the 9.04 live CD and cannot get Nautilus to open.  From the "Places" menu I choose a location, say Desktop, and a tab appears at the bottom of the screen, "opening Desktop" but that goes away after a few seconds and Nautilus never appears.

If I open a terminal window and type "nautilus" at the prompt, I get something that says "segmentation fault, core dumped".

Any suggestions?

---

### Post by Wiebelhaus on 2009-06-09
Either faulty optical drive , bad media or faulty ram.

Run [UBCD (A diagnostic tool disc)]("http://www.ultimatebootcd.com/") Memory diagnostics and also test read write ability of the optical drive.

---

### Post by raymondvillain on 2009-06-10
Ran the memory test, everything passed.  The disk test said everything was O. K.(the one that is an option at startup on the live CD), and the md5sum (before burning) was correct.

I can't believe it is the optical drive.  I booted to the Hardy (8.04) live CD and Nautilus works fine.

Any other ideas or suggestions?

---

