---
title: "Dapper To Hardy Upgrade Problems"
date: 2008-10-06
forum: General Help
---

### Post by Blairboy on 2008-10-06
Trying to figure out how to actually dist-upgrade, but ran into this:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  acpi-support: Depends: xset but it is not installable
  apache2: Depends: apache2-mpm-worker (>= 2.2.8-1ubuntu0.3) but it is not installed or
                    apache2-mpm-prefork (>= 2.2.8-1ubuntu0.3) but 2.0.55-4ubuntu2.3 is installed or
                    apache2-mpm-event (>= 2.2.8-1ubuntu0.3) but it is not installed
  gdm: Depends: xrdb but it is not installable
  java-gcj-compat: Depends: libgcj8-1-awt but it is not installed
  kdelibs4c2a: Depends: iceauth but it is not installable
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but it is not installable
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but it is not installable
  libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0.3-2 is installed
  libxrandr-dev: Depends: libxrandr2 (= 1:1.1.0.2-0ubuntu4) but 2:1.2.2-1 is installed
  php5-cli: Depends: php5-common (= 5.2.4-2ubuntu5.3) but 5.1.2-1ubuntu3.12 is installed
  ttf-arphic-ukai: Depends: xutils (>= 4.0.2) but it is not installed
  ttf-arphic-uming: Depends: xutils (>= 4.0.2) but it is not installed
  ttf-kochi-gothic: Depends: xutils (>= 4.0.2) but it is not installed
  ttf-kochi-mincho: Depends: xutils (>= 4.0.2) but it is not installed
  ubuntu-desktop: Depends: libgl1-mesa but it is not installable
  x-ttcidfont-conf: Depends: xutils but it is not installed
  x-window-system-core: Depends: xserver-xorg but it is not installed
                        Depends: libgl1-mesa but it is not installable
                        Depends: xutils but it is not installed
  xinit: Depends: xrdb but it is not installable
  xkeyboard-config: Depends: xkb-data (>= 1.1~cvs.20080104.1-1ubuntu6) but it is not installed
  xserver-xorg-core: Depends: xserver-xorg but it is not installed
E: Unmet dependencies. Try using -f.
```

I've seen similar problems, but nothing like this and no solution as of yet.

---

### Post by Therion on 2008-10-06
Going from Dapper to Hardy?  Four full releases??  

Maybe it's time to consider a fresh install?

---

### Post by Blairboy on 2008-10-06
I'm in a different state than the machine.  Even so, I shouldn't have to completely reinstall just to upgrade.

---

### Post by Therion on 2008-10-07
> **Blairboy said:**
> Even so, I shouldn't have to completely reinstall just to upgrade.
Funny word, "should".

And if you want to persist in trying doing a dist-upgrade I you wish fair winds and following seas!  

<snappy salute>

---

### Post by -Zeus- on 2008-10-08
you don't have to completely reinstall just to upgrade, and no one said that.  It's just about 10x easier. :-P

---

### Post by Blairboy on 2008-10-15
While I'm aware of that, its not really an option for me right now.  Any other ideas?

---

### Post by kostkon on 2008-10-15
> **Blairboy said:**
> While I'm aware of that, its not really an option for me right now.  Any other ideas?
An upgrade from 6.06 to 8.04 is officially supported, so, yes, you are not trying to do anything wrong.

First of all, check if you have all of your repositories enabled (i.e. *main*, *universe*, *multiverse*, *restricted*). 

Then, make sure that you are up-to-date, so check for any updates and install them:
```
sudo apt-get update && sudo apt-get upgrade
```
after doing the above, try to *dist-upgrade* again.

---

### Post by Blairboy on 2008-10-15
I managed to download a few packages and manually install them with dpkg, but I'm stuck here (I have all repositories enabled).

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (>= 2.2.8-1) but it is not installed or
                    apache2-mpm-prefork (>= 2.2.8-1) but 2.0.55-4ubuntu2.3 is installed or
                    apache2-mpm-event (>= 2.2.8-1) but it is not installed
  gdm: Depends: xrdb but it is not installable
  kdelibs4c2a: Depends: iceauth but it is not installable
  libgcj8-1-awt: Depends: libgtk2.0-0 (>= 2.12.0) but 2.8.20-0ubuntu1.1 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but it is not installable
  libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0.3-2 is installed
  libxrandr-dev: Depends: libxrandr2 (= 1:1.1.0.2-0ubuntu4) but 2:1.2.2-1 is installed
  php5-cgi: Depends: php5-common (= 5.1.2-1ubuntu3.12) but 5.2.4-2ubuntu5.3 is installed
  php5-gd: Depends: php5-common (= 5.1.2-1ubuntu3.12) but 5.2.4-2ubuntu5.3 is installed
  ubuntu-desktop: Depends: libgl1-mesa but it is not installable
  x-window-system-core: Depends: libgl1-mesa but it is not installable
  xinit: Depends: xrdb but it is not installable
  xkeyboard-config: Depends: xkb-data (>= 1.1~cvs.20080104.1-1ubuntu6) but it is not installed
  xserver-xorg: Depends: xkb-data but it is not installed or
                         xkb-data-legacy but it is not installed
                Depends: xserver-xorg-video-all but it is not installed or
                         xserver-xorg-video-2
E: Unmet dependencies. Try using -f.
```

Still trying to get this crapola fixed.

---

### Post by Yellow Pasque on 2008-10-15
> apache2-mpm-prefork (>= 2.2.8-1) but 2.0.55-4ubuntu2.3 is installed
From this clue, I think your repos might be incorrect and might have a combo of hardy dapper and/or 3rd-party repos. What does your /etc/apt/sources.list look like?

---

### Post by fgrtr on 2008-10-15
come on    [http://www.internetgameservice.com/](http://www.internetgameservice.com/) .   and when you have time you can have a look on it , and i think it can help you

---

### Post by Blairboy on 2008-10-16
This is what it looks like currently.
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://download.tuxfamily.org/swiftweasel hardy multiverse
# deb http://www.getautomatix.com/apt gutsy main
deb http://www.virtualbox.org/debian hardy non-free

deb http://repository.akirad.net akirad-hardy main

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info hardy all

deb http://repoubuntusoftware.info hardy all
#ULTAMATIX REPOS END
deb http://packages.medibuntu.org/ hardy free non-free
```

I just tried with this sources.list as well and still no dice.
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
## Major bug fix updates produced after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

```

---

### Post by Sef on 2008-10-16
> Trying to figure out how to actually dist-upgrade, ....

dist-upgrade is not longer supported.   To upgrade properly from Dapper to Hardy, read [this sticky]("http://ubuntuforums.org/showthread.php?t=849915").

---

