---
title: "CanoScan Lide 120: always black scans"
date: 2016-09-10
forum: Hardware
---

### Post by Elmi77 on 2016-09-10
Hi,

I try to get a CanoScan Lide 120 working with some very different results:


[LIST=1]
[*]Ubuntu 14 and the sane-drivers that are available via ppa:rolfbensch/sane-git (as described at [http://askubuntu.com/questions/652769/running-canon-120-lide-scanner-on-ubuntu-14-04](http://askubuntu.com/questions/652769/running-canon-120-lide-scanner-on-ubuntu-14-04)) -> evwerything works well, scans are fast and have a good quality

[*]Ubuntu 15 which should support this scanner by default: scanner needs a long time until scan starts and the result is completely black

[*]latest Ubuntu 16 which should support this scanner by default and should have a lot of bugfixes: same result, scanner is slow and produces only black pages
[/LIST]

Since the sane-drivers that come with Ubuntu 15 and 16 should be newer than the ones I added from this third party repository, I would have expected the scanner works there. So any idea what could be wrong or what I could do to get it working? The "ppa:rolfbensch/sane-git" does not come with a newer sane, so it does not work with Ubuntu 15/16.

Any hint or idea is welcome!

---

### Post by pqwoerituytrueiwoq on 2016-09-10
that PPA has the latest drivers, it is updated daily assuming there is a change
16.04 has 1.0.25+git20150528-1ubuntu2, that ppa has 1.0.26-git20160803
based on the version number the ppa has a version about 1 year and 2 months newer

---

### Post by lordamit on 2016-12-19
> **pqwoerituytrueiwoq said:**
> that PPA has the latest drivers, it is updated daily assuming there is a change
16.04 has 1.0.25+git20150528-1ubuntu2, that ppa has 1.0.26-git20160803
based on the version number the ppa has a version about 1 year and 2 months newer


Hi,
Thank you! 

I can confirm that this worked.

---

### Post by Elmi77 on 2016-12-19
Finally I found the reason: it is a bug related to SimpleScan. When brightness is turned up in this program, the scans become darker (so this parameter works in the wrong direction). To make the scanner work, brightness has to be pulled down.

---

