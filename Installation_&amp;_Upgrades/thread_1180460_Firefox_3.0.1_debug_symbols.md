---
title: "Firefox 3.0.1 debug symbols"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by DanielPal on 2009-06-06
Firefox constantly crashes and I need the symbols to debug this.
I read:
[https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)

But the info there needs some sort of update. Packages like
firefox-3.0-dbgsym
firefox-3.0-dbg

Don't exist on Ubuntu 9.04 or at least I can't find them.
Here is my sources.list:

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty main restricted
deb-src http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-updates main restricted
deb-src http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty universe
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty multiverse
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-security main restricted
deb-src http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-security universe
deb http://ftp.unina.it/pub/linux/distributions/ubuntu/ jaunty-security multiverse




```

---

