---
title: "Already running Karmic without upgrading"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by motorhead_1 on 2009-10-29
Since a week more or less I've noticed through the terminal that I'm already running Karmic 9.10 without ever having launched the Update Manager nor havaing used the termial on this purpose (never typed: gksudo update-manager -d)

```
daitarn@daitarn-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu karmic (development branch)
Release:    9.10
Codename:    karmic
```
How is that possible? I've launched now the Update Manager, a complete upgrade is not possible probably cause I'm using packages from repositories not controlled by Ubuntu, however the Upgrade Manager is now downloading 444 MB of something... (very slowly)

---

### Post by wilee-nilee on 2009-10-29
Maybe you sleep upgraded. ;)

---

### Post by motorhead_1 on 2009-10-29
> **wilee-nilee said:**
> Maybe you sleep upgraded. ;)
lol what's that

---

### Post by motorhead_1 on 2009-10-29
```
daitarn@daitarn-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
# deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main
deb http://security.ubuntu.com/ubuntu hardy-security main universe
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse universe main
daitarn@daitarn-laptop:~$ 
```

ideas?

---

### Post by Kinetic Being on 2009-10-29
```
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse universe main
```

notice the 'karmic' 

it has the packages with the highest version number, so thats what is actually being used. (aside from anything set in apt-preferences)

---

### Post by theozzlives on 2009-10-29
Well.... enjoy your new version, I guess.

---

### Post by motorhead_1 on 2009-10-29
> **Kinetic Being said:**
> ```
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse universe main
```notice the 'karmic' 

it has the packages with the highest version number, so thats what is actually being used. (aside from anything set in apt-preferences)
but I guess this is a RC version...

---

