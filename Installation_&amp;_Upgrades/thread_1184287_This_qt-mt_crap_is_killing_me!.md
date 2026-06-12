---
title: "This qt-mt crap is killing me!"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-06-11
Virtually every qt application requires these 'qt-mt' libraries...of qt 4.

Though they ARE installed, but still its says qt-mt not found.....

qt-mt-dev wont get installed cause of unresolvable dependencies.

I have libqt3-mt of version 3.3.8 installed...I think is is causing the problem.

The applications require 32 bit qt libraries...will installing them help?


And no...I wont use aptitude, it downgrades and removes many packages.

All packages are upgraded.

---

### Post by ad_267 on 2009-06-11
How are you installing your packages? Also what version of Ubuntu are you using and can you post your /etc/apt/sources.list

---

### Post by dE_logics on 2009-06-11
Not packages...compiling form source...mostly.

Ubuntu 8.10

apt.sources - 

```

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
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
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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
deb http://dl.google.com/linux/deb/ stable non-free
# deb-src ftp://ftp2.fr.debian.org/debian/ stable main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ sarge non-free
# deb ftp://ftp.debian.org/debian testing main contrib non-free
# deb http://security.debian.org/ sarge/updates main
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.debian.org/debian unstable main contrib non-free
# deb http://security.debian.org/ stable/updates main
# deb ftp://ftp.debian.org/debian testing main contrib non-free
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.tux.org/java/debian/ unstable non-free
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ testing non-free
# deb http://pkg-kde.alioth.debian.org/kde-3.4.0/ ./
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb http://ftp.debian.org/debian/ etch main
# deb http://security.debian.org/ etch/updates main contrib
# deb-src http://security.debian.org/ etch/updates main contrib
# deb http://debian.uchicago.edu/debian/ etch main contrib non-free
# deb-src http://debian.uchicago.edu/debian/ etch main contrib non-free
# deb http://www.debian-multimedia.org etch main
# deb http://www.debian-multimedia.org stable main
# deb-src http://www.debian-multimedia.org/ etch main
# deb http://ftp.us.debian.org/debian stable main contrib non-free
# deb-src http://ftp.us.debian.org/debian stable main contrib non-free
# deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
# deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
# deb http://ftp.debian-unofficial.org/debian stable main contrib non-free restricted
# deb-src http://ftp.debian-unofficial.org/debian stable main contrib non-free restricted
# deb http://ftp.us.debian.org/debian testing main contrib non-free
# deb-src http://ftp.us.debian.org/debian testing main contrib non-free
# deb http://security.debian.org testing/updates main contrib non-free
# deb-src http://security.debian.org testing/updates main contrib non-free
# deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free
# deb http://ftp.debian.org/debian/ sid main contrib non-free
# deb http://ftp.us.debian.org/debian/ experimental main contrib non-free
# deb http://www.debian-multimedia.org experimental main
# deb http://gulus.usherbrooke.ca/debian-unofficial/ etch main contrib non-free restricted
# deb-src http://mentors.debian.net/debian unstable main contrib non-free
# deb http://mirror.noreply.org/pub/tor etch main
# deb-src http://mirror.noreply.org/pub/tor etch main
# deb http://www.backports.org/debian etch-backports main
# deb http://www.kiberpipa.org/~minmax/cin...ilds/pentium4/ ./
# deb-src http://mentors.debian.net/debian unstable main contrib non-free

```

I did add many repos...but unchecked them.

---

### Post by dE_logics on 2009-06-11
No one?

---

### Post by ad_267 on 2009-06-11
My guess is you've messed things up pretty badly by installing packages from other repositories.

For compiling qt applications you definitely need the -dev package. You could try removing libqt3-mt then reinstalling the version from the Ubuntu repositories.

---

### Post by kerry_s on 2009-06-11
> Not packages...compiling form source...mostly.

then your not doing it the debian way. google it
basically you need to make debs and install with dpkg so that the package managers know about them.
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

if you want to do source there are better distros for that, arch for example or gentoo if you really want to get hard core.

---

### Post by dE_logics on 2009-06-12
> **ad_267 said:**
> My guess is you've messed things up pretty badly by installing packages from other repositories.

For compiling qt applications you definitely need the -dev package. You could try removing libqt3-mt then reinstalling the version from the Ubuntu repositories.

No, though those other repos are listed, but I didn't do anything with it...just listed it.

NO...I will not remove qt3-mt...that will remove half all the QT applications including amarok and smplayer. 

How bout force installing?

[QUOTE=kerry_s]then your not doing it the debian way. google it
basically you need to make debs and install with dpkg so that the package managers know about them.
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

if you want to do source there are better distros for that, arch for example or gentoo if you really want to get hard core. [/QUOTE]

Yeah...I AM trying to install gentoo on a pendrive.

And till now...I successfully logged in a as root after chrooting...all in commandline, cause xserver failed!...isn't that fantastic???

---

### Post by dE_logics on 2009-06-12
Yeah I know what's wrong...its that same hardy issue.

What ubuntu developers/people maintain the repos forget is about the PREVIOUS versions of ubuntu...that they need to maintain it too.

As a result many packages are not updated......like those new opesource ATI drivers.

---

### Post by ad_267 on 2009-06-12
> **dE_logics said:**
> NO...I will not remove qt3-mt...that will remove half all the QT applications including amarok and smplayer.

You can do "sudo apt-get -r --force-all qt3-mt" to remove it without removing packages that depend on it. Then do a "sudo apt-get install qt3-mt to install the version from the repositories.

---

### Post by dE_logics on 2009-06-12
Ok...I resolved the issues...as I said before, once a new version of ubuntu comes out, the developers forget about the old one.

Adding this repository - 

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

To your sources will clear the dependencies.

You can also upgrade to the new ATI drivers this way who's binaries were never launched for intrepid.

---

