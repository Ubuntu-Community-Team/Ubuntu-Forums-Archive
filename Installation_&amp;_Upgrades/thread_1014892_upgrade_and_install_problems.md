---
title: "upgrade and install problems"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Moonah on 2008-12-18
hi guys 
i'm trying to upgrade from 7.04 to 7.10. basically i was going to build up to 8.10. but i'm having a problem with upgrading or installing anything using the add remove GUI. it keeps coming up with the below error

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

and this in the little window

"http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]"

i'm sure it's something stupid like not pointing to the right place. can anyone give me the fix for this? Please?

---

### Post by pietjanjaap on 2008-12-18
This version is not supported anymore!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Moonah on 2008-12-18
so i can't upgrade from that now?

---

### Post by wahoobob on 2008-12-18
Best suggestion might be to backup your /home and any other information that you will need in the new install and then do a fresh install of 8.10.  Probably more stable and quicker than going through several upgrades.  I just went through this myself with a side trip to gOS.  the 8.10 started up in about 30 minutes with no problems... dumped the home info in and walaaa ... looking good.  If you have a dual boot system you need to stay away from the guided partitioning and choose to do a manual. on the screen that comes up, double click your ubuntu partition and mark it to be formatted and choose / as the mountpoint.

---

