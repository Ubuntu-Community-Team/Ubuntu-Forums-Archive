---
title: "Could not download all repositories"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by blakemcclaren on 2009-06-21
I am using 7.10 gutsy and I have broken my repositories.

I am trying to install g++, but I am unable to download or update repositories.

I mark g++ for installation [**WARNING; You are about to install software that can't be authenticated**], select OK >> Apply, download starts and ERROR:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/cpp-4.2_4.2.1-5ubuntu4_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgomp1_4.2.1-5ubuntu4_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/gcc-4.2_4.2.1-5ubuntu4_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.1-5ubuntu4_i386.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/g++-4.2_4.2.1-5ubuntu4_i386.deb
  404 Not Found [IP: 91.189.88.46 80]

```

This is the error I get when reloading repositories:
**Could not download all repository indexes**
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.140 80]
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.140 80]
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 404 Not Found
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]

``` 

I would appreciate any help!

---

### Post by Soul-Sing on 2009-06-21
I think, buts it is very early in the morning here, the 7.10 desktop version of ubuntu is not longer updated, for it is no longer supported. Try 8.04 or a newer version.

---

