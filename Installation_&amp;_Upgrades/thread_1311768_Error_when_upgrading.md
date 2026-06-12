---
title: "Error when upgrading"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Nater43 on 2009-11-02
When updating from 9.04 to 9.10, everything goes well until a certain point, when I get the following message:

Invalid package information

After your package information was updated the essential package 'ubuntu-minimal' can not be found anymore.
This indicates a serious error, please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

What can be done to fix this? I've attached the files in the designated location so maybe one of you can figure it out. Thanks.

---

### Post by Nater43 on 2009-11-02
Anyone want to give this problem a shot?

---

### Post by Nater43 on 2009-11-02
Also, when trying to update repository index, I get this message:

GPG error: [http://snert.mi.hs-heilbronn.de](http://snert.mi.hs-heilbronn.de) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://snert.mi.hs-heilbronn.de](http://snert.mi.hs-heilbronn.de) karmic-updates Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://snert.mi.hs-heilbronn.de](http://snert.mi.hs-heilbronn.de) karmic-security Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages)  404 Not Found [IP: 81.171.111.247 80]
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/main/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/restricted/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/universe/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/multiverse/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/main/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/universe/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/main/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/restricted/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/universe/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2](http://snert.mi.hs-heilbronn.de/pub/ubuntu/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Nater43 on 2009-11-03
Anybody?

---

### Post by Nater43 on 2009-11-03
Bump

---

### Post by Nater43 on 2009-11-03
Still can't update repositories, or do an upgrade. I've tried changing servers, but no luck. Anyone have any ideas?

---

### Post by Nater43 on 2009-11-03
I take it no one has any ideas on how to fix this?

---

### Post by Nater43 on 2009-11-03
Again, bump.....

---

### Post by Nater43 on 2009-11-04
...

---

### Post by Nater43 on 2009-11-05
?

---

### Post by Nater43 on 2009-11-06
Bump

---

### Post by Nater43 on 2009-11-07
Bump

---

### Post by Nater43 on 2009-11-07
Is anyone going to even look at this?

---

### Post by Nater43 on 2009-11-10
Bump

---

