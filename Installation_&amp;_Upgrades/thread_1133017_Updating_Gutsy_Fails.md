---
title: "Updating Gutsy Fails"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by barieb on 2009-04-22
I tried running:

sudo apt-get update

And got this error:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

After googling, the consensus was to reset my sources.list to defaults, which I did, I get the same error.

When navigating to:

[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

in my web browser, I don't see any reference to gutsy at all - yikes!

Could it be that an ubuntu mirror is down or mis-configured?

---

### Post by snowpine on 2009-04-22
I hate to break it to you, but support for Gutsy has ended. You can certainly continue to use it if you like, but there will be no more updates.

[http://ubuntuforums.org/showthread.php?t=1104965](http://ubuntuforums.org/showthread.php?t=1104965)

---

### Post by slakkie on 2009-04-22
-wrong-

---

