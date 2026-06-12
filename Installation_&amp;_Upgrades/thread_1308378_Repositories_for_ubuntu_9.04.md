---
title: "Repositories for ubuntu 9.04"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by jackal_79 on 2009-10-31
I recently upgraded my ubuntu from 8.10 to 9.04.During my upgradation most of my 3rd party repositories were disabled.Please tell me what all repositories are required in ubuntu 9.04 (including 3rd party sources)

Attaching current source list:

**************************************************
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) intrepid main #blueman
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main #Pidgin disabled on upgrade to jaunty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe multiverse restricted
******************************************************

---

### Post by zvacet on 2009-10-31
Edit your source list with 

```
gksudo gedit /etc/apt/sources.lst
```

and replace

> deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) intrepid main #blueman
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main #Pidgin disabled on upgrade to jaunty

with 

> deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main 
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main 
 deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main 
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main 
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main 
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main 


save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by steevc on 2009-11-06
Should I remove PPAs from my sources.list before doing the upgrade? I've just got Gwibber and kubuntu-experimental.

---

