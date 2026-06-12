---
title: "FYI - you can't rely on &quot;Check CD for Defects&quot;"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-12-11
There is clearly a bug in the test process used by the Alternate CD (and normal LiveCD, too?) for "Check CD for defects".  You can have a perfectly valid disc *but a flaky drive* and the test will Pass -- but your install will still fail!

I just experienced this firsthand and wanted to report it!

**MY TEST CASE**
I had an existing system with 8.04, everything was running beautifully.  I downloaded the 8.10 Alternate ISO and burned it to disc.  I shutdown, installed a brand-new hard-drive, then booted from the CD and tried to install it; the process failed after the "Checking APT sources" step.  I tried several times, changing various install (and BIOS) options each time, but it always failed in the same spot.  I suspected the disc and ran "Check CD for defects" -- it passed.  Mind you, this was all being done on the same PC and CD drive, start to finish.

**THE SOLUTION**
Ultimately, I realized the CD drive was about 3 years-old and I had another that was less than 1 year-old.  So I swapped them and now the install worked perfectly.

**CONCLUSION**
The Ubuntu installer seems to be very sensitive to minor problems in CD/DVD drives.  The "Check for CD defects" seems to be _less_ sensitive to those same problems and reports a false negative (for problems).

---

### Post by jenkinbr on 2008-12-11
Have you checked for a launchpad bug?

If there isn't one, you may want to post this as one.

---

### Post by bsmith1051 on 2009-03-06
So, I reported this via Launchpad but no one ever responded...
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/322873](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/322873)

---

