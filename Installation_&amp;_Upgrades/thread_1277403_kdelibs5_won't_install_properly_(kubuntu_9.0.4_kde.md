---
title: "kdelibs5 won't install properly (kubuntu 9.0.4 kde 3.5.10)"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by thefarmer on 2009-09-28
okay, so i'm running the aforementioned kubuntu version from an 8GB flash drive (that was probably irrelevant, but i spare no details). When I installed, i discovered I could install kde4 applications (namely games) no problems installing whatsoever. Awhile back, i updated my packages, as usual. However, for reason I can't remember, it broke kdelibs5. I managed to remove kdelibs5, kdelibs5-data, the games packages, and libplasma3 (or soime sort of package involving plasma). Now, whenever I try to install kdelibs 5, kdelibs5-data can't install, thus breaking kdelibs5. This is the chunk of text after the initial error, all the way back to command input, I get from apt-get


dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.2.2-0ubuntu5.2_all.deb (--unpack):
 unable to make backup link of `./usr/share/kde4/apps/katepart/syntax/mips.xml' before installing new version: Operation not permitted
Selecting previously deselected package kdelibs5.
Preparing to replace kdelibs5 4:4.2.2-0ubuntu5.2 (using .../kdelibs5_4%3a4.2.2-0ubuntu5.2_i386.deb) ...
Unpacking replacement kdelibs5 ...
Preparing to replace kdelibs-bin 4:4.2.2-0ubuntu5.2 (using .../kdelibs-bin_4%3a4.2.2-0ubuntu5.2_i386.deb) ...
Unpacking replacement kdelibs-bin ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_4%3a4.2.2-0ubuntu5.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help

---

