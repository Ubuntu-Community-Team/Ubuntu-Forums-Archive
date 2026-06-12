---
title: "Jaunty sources.list edit proceedure"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2009-04-24
I installed Jaunty and then, instead of building the sources.list one source at a time (referring to adding sources for extra packages not included in release download such as packages installed in the multimedia How-To), I intend to just use my Intrepid sources.list and edit all of the "intrepid" to "jaunty".

Is this a legit method or will this result in many errors?

O, what the heck. Here is my Intrepid sources.list which I intend to use after editing it, if you all say it is OK.

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
##===========================================================================

## The following items were added by me.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team. deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security restricted
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free

#The following added by me for "wine" repositories
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

```

---

### Post by dino99 on 2009-04-24
hi, 

i don't really understand what you are doing : if you want to replace Intrepid with jaunty, it's called a dist-upgrade, 

so use: sudo update manager -d -c in the console and your sources.list is automatically update, or go to system administration softwares source and choose highiest distro

Instead, the other solution is , like your idea, to modify your sources.list by changing every intrepid by jaunty (don't forget some lines because the system be confused)

it's up to you :P:P

---

### Post by Ronin_301 on 2009-04-24
I think he's referring to changing any repositories he's added himself to Jaunty ones.

This thread had some good information on how to go about this.

[http://ubuntuforums.org/showthread.php?t=1134431](http://ubuntuforums.org/showthread.php?t=1134431)

---

### Post by mntokman on 2009-05-16
> **dino99 said:**
> hi, 

i don't really understand what you are doing : if you want to replace Intrepid with jaunty, it's called a dist-upgrade, 

so use: sudo update manager -d -c in the console and your sources.list is automatically update, or go to system administration softwares source and choose highiest distro

Instead, the other solution is , like your idea, to modify your sources.list by changing every intrepid by jaunty (don't forget some lines because the system be confused)

it's up to you :P:P

it did not work...

```
mntokman@greenworld:~$ sudo update manager -d -c
[sudo] password for mntokman:
sudo: update: command not found

```

---

