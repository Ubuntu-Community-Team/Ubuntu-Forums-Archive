---
title: "Xubuntu-desktop installition"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Intrepid Ibex on 2008-12-21
Hi,

I'm trying to install xubuntu-desktop but when I write:
```
sudo apt-get install xubuntu-desktop
```
and type "Y" to install, it gives error message:
[i]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis
sing?[/i]

```
sudo apt-get update
```
Gives the same error..

Little help? [-o<


**Edit: I currently have the alternate version of xubuntu..**

---

### Post by Elfy on 2008-12-21
Open software sources - in the system menu

Check the main, universe, multiverse, restricted repositories. On the 3rd party tab you can enable the partner repos, on the update tab make sure that proposed and backports are not enabled.

Close and reload when it's offered and then try again.

If you get errors please paste them here

---

### Post by Intrepid Ibex on 2008-12-21
check the edit

---

### Post by Elfy on 2008-12-21
wasn't there when I wrote the post :)

post your sources list then or edit it 

```
sudo nano /etc/apt/sources.list
```

This is mine - don't worry about the repos at the end - also I have the deb-src enabled you probably don't need them

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

##Amarok2
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

##Exaile
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main

##Banshee
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
kevin@kevin-desktop:~$ sources

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

##Amarok2
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

##Exaile
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main

##Banshee
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
```

Also make sure that cdrom is disabled

---

### Post by Intrepid Ibex on 2008-12-21
I got that I had to write:
```
sudo apt-get install xubuntu-desktop --fix-missing
```
Now it is insatlling it!

---

