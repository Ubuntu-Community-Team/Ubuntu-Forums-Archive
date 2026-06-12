---
title: "SoftwareSources  for Ubuntu and Kubuntu!"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by baskar007 on 2009-10-09
I am getting error while try to reload.

here is the error:

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


How to fix this error?

---

### Post by zvacet on 2009-10-09
**system>admin>software sources>change server** (you can try main or any other close to you).

---

### Post by baskar007 on 2009-10-09
> **zvacet said:**
> **system>admin>software sources>change server** (you can try main or any other close to you).
I just tried change india server form US and main. all those are same problem

No problem with my internet connection. i can browse download

---

### Post by baskar007 on 2009-10-09
this is my source list:

> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

# deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
# deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
# deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) hardy main
# deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main
tu-ppa/backports/ubuntu jaunty main


---

