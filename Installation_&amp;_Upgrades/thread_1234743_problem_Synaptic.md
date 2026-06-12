---
title: "problem Synaptic"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2009-08-08
I have this message when I install the programs 

-----------------terminal-------------------------------------------------------------

E: Malformed line 5 in file source / etc / apt / sources.list (URI)

______________________________________________________________

---

### Post by slakkie on 2009-08-08
post the contents of your sources.list file please..

---

### Post by m3asmi on 2009-08-08
> **slakkie said:**
> post the contents of your sources.list file please..


this is the file 

------------------------------- cat /etc/apt/sources.list -------------------------------
```
XXX@XXX:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[U&#65533;U&#65533;EkD&#1611;&#65533;&#65533;G&#65533;&#65533;_    &#65533;2&#65533;&#65533;KN &#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;?&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;>:q:&#65533;a&#65533;&#65533;]/ jaunty main restricted
deb cdrom:[APTonCD for ubuntu gutsy - i386 (2007-11-22 14:21) CD1]/ /
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ma.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ma.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner





```

---

### Post by slakkie on 2009-08-08
Put a # in fron of all those cd rom entries, beginning on line 5.
Lines 5-7 and then rerun it.

---

