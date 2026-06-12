---
title: "segmentation faults after installing 2GB RAM"
date: 2008-12-11
forum: Hardware
---

### Post by jkwon19 on 2008-12-11
I have a Dell e1405 laptop which originally came with 1GB of memory (2 x 512MB).  I've installed Hardy 8.04 and have been running with no problems.  I recently installed 2GB of crucial memory (2 x 1GB), and the system appeared to recognize the full 2GB, and memtest86 reported no errors, but I have been seeing various problems:

1) gdmsetup fails with a segmentation fault (e.g., 'sudo gdmsetup' or System->Administration->Login Window).
2) when logging out/shutting down, network manager reports a bunch of assertion failures (they appear too fast for me to record).

I removed one 1GB stick, and now everything is back to normal.

Is there an incompatibility with 2GB?  Do I need to reinstall/reconfigure my system in order to use 2GB?

Thanks,

Jason

---

### Post by iponeverything on 2008-12-11
try each gig stick separately. have to wonder if memtest is missing something. 

Nothing special needs to be done for 2G.

---

### Post by jkwon19 on 2008-12-11
Tried each stick individually, and it looks like one SODIMM is flaky.  I've requested an RMA.

Thanks!

---

