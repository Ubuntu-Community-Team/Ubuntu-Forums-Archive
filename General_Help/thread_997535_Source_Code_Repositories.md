---
title: "Source Code Repositories"
date: 2008-11-29
forum: General Help
---

### Post by anotherdisciple on 2008-11-29
Do I really need the source code repos?

Could I make my sources.list look like this?...

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ intrepid main restricted
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates main restricted
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ intrepid universe
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates universe
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ intrepid multiverse
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates multiverse
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
[COLOR="Red"]#[/COLOR] deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
[COLOR="Red"]#[/COLOR] deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security main restricted
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security universe
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-security universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security multiverse
[COLOR="Red"]#[/COLOR] deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-security multiverse

# Open Office 3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

# Cairo Dock
deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
```

Do you forsee any problems with commenting out the source codes?

---

### Post by Washer on 2008-11-29
nope

---

### Post by damis648 on 2008-11-29
You could, but it wouldn't change much really.

---

