---
title: "[SOLVED] Segmentation faulty tree... 50%"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by master5o1 on 2008-12-13
I get this 'Segmentation faulty tree... 50%' error when I try to upgrade/safe-upgrade in apt-get/aptitude, or when I try to open Synaptic or update-manager.

---

### Post by taurus on 2008-12-13
Can you post your /etc/apt/sources.list?  

```
cat /etc/apt/sources.list
```

---

### Post by master5o1 on 2008-12-14
It appears to be fixed...after a restart AND after a suspend/resume :S

---

### Post by ubersolid on 2009-01-02
I have this error now too, would be nice to know what is causing it.
```
 uptime
 09:24:17 up 1 day, 20:45,  3 users,  load average: 0.42, 0.41, 0.30

```

sources.list:
```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://fi.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fi.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fi.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fi.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb http://ppa.launchpad.net/usplash-smooth/ubuntu intrepid main
deb-src http://ppa.launchpad.net/usplash-smooth/ubuntu intrepid main

deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```

This is the second time this is happening.

---

### Post by ubersolid on 2009-01-02
I'm sorry, should have searched a bit better.
The solution seems to be
```
sudo rm /var/cache/apt/*.bin
```

as they figured out here:
[http://ubuntuforums.org/showthread.php?t=19563]("http://ubuntuforums.org/showthread.php?t=19563")
[http://ubuntuforums.org/showthread.php?t=527878highlight=Segmentation+faulty+tree...+50%25]("http://ubuntuforums.org/showthread.php?t=527878&highlight=Segmentation+faulty+tree...+50%25")
[http://lists.debian.org/debian-user/2000/03/msg00861.html]("http://lists.debian.org/debian-user/2000/03/msg00861.html")

Problem solved.

---

