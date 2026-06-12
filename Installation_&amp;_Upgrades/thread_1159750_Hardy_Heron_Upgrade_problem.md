---
title: "Hardy Heron Upgrade problem"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by sakthi on 2009-05-15
I am not able to upgrade Hardy Heron 8.04 for the past one week. I am getting 302 moved error.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  302 Moved
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  302 Moved
Some index files failed to download, they have been ignored, or old ones used instead.

Is it a server problem?

Can someone please help.....

---

### Post by zvacet on 2009-05-15
I click on links and they are O.K.Try with another  server and just in case post output of 

```
cat /etc/apt/sources.list
```

---

### Post by sakthi on 2009-05-15
Thanks for the reply. I have already tried with three servers. All of them giving the same error.

This is my cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
# deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu hardy main
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu hardy main
```

---

### Post by zvacet on 2009-05-15
If I didn´t overlooked something your source list look good,so I don´t know reason why you can not upgrade your system.

---

### Post by sakthi on 2009-05-18
I too do not know abt why this is happening. This is the same in my home also. In office I get 302 moved error, in home I just get network problem.

---

