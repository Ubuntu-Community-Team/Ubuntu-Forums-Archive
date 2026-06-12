---
title: "Ubuntu 9.04 32Bit aptitude -f safe-upgrade wants to remove gnome"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by nevbear666 on 2009-05-11
```

root@darkh0st:/etc/apt# aptitude -f safe-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  gdk-imlib11{u} gnome-bin{u} gnome-libs-data{u} hildon-fm-l10n-engb{u} hildon-update-category-database{u} imlib-base{u} imlib11{u} libart2{u}
  libevent1{u} libgnome32{u} libgnomesupport0{u} libgnomeui32{u} libgnorba27{u} libgnorbagtk0{u} libhildon-1-0{u} libhildon-thumbnail0{u}
  libhildonmime0{u} liborbit0{u} libosso1{u} libpt-1.10.10{u} libpt-1.10.10-plugins-alsa{u} tsocks{u}
0 packages upgraded, 0 newly installed, 22 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 10.5MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

this does not look right, considering im actually using gnome;-)

My apt sources list looks like that:
```

root@darkh0st:/etc/apt# cat sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

#deb http://at.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://at.archive.ubuntu.com/ubuntu/ jaunty universe
#deb http://at.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://at.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://at.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

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
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse

#dvd css
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" Deaktiviert bei Systemaktualisierung zu jaunty
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free # Deaktiviert bei Systemaktualisierung zu jaunty
# deb http://le-web.org/repository/stable intrepid/

```

anyone any ideas why?

greetings nev.

---

