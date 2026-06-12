---
title: "HP Deskjet D1660 Print issues?"
date: 2010-07-23
forum: Hardware
---

### Post by bigkahuna on 2010-07-23
I'm running Ubuntu 9.04 on a Dell notebook and recently purchased an HP Deskjet D1660 Printer.  I downloaded and installed the latest HPLIP drivers from the HP site.  The printer prints, and all the settings seem to work, except it starts printing about 3/4" down the page rather than at the top.  I went through the settings, I did the driver self check (hp-check), and I rebooted both the computer and reset the printer numerous times.  Searched everywhere for a clue what might be the problem but nothing so far.  Anyone?

---

### Post by bigkahuna on 2010-07-23
Anyone?

I tried uninstalling the drivers and then re-installing them.  Then went to the HPLIP webpage and found that they've updated the drivers since just this morning.  I installed the new drivers and still no luck.  Every page prints at 3/4" down the sheet of paper, no matter what I try to do.  Gonna return this tomorrow and try a different printer.  It's stuff like this that makes sticking with Ubuntu kinda hard sometimes...

---

### Post by bigkahuna on 2010-07-24
This appears to be caused by a bug in the HPLIP drivers:

[https://bugs.launchpad.net/hplip/+bug/592006](https://bugs.launchpad.net/hplip/+bug/592006)

This is a workaround that may help, but you loose approx. 1" of the top of the page:

[https://bugs.launchpad.net/hplip/+bug/474811](https://bugs.launchpad.net/hplip/+bug/474811)

---

