---
title: "packages don't seem to upgrade"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by sport9155 on 2009-07-02
when I sign into the system I'm told, "5 packages can be updated.
8 updates are security updates."  I do a "sudo apt-get update" then "sudo apt-get upgrade", but says,
"The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."
 
doesn't really match up to 5 packages to be updated or the 8 updates are security ... 
 
should I be doing something different?  Also, I had configured the auto updates, but when I check the log file, it looks as though it has not been working, even though there have been security updates.
 
any idea's.
 
thanks.

---

### Post by Sef on 2009-07-03
The packages are being held back for some reason.  When they are ready to be released, they will be.

---

### Post by sport9155 on 2009-07-03
ah .. ok .. I thought I was doing something incorrectly.

---

