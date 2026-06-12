---
title: "Failed Installation of KDE4, Synaptic No Work"
date: 2008-08-04
forum: General Help
---

### Post by CodyT07 on 2008-08-04
I tried to reinstall KDE4 on ubuntu 64 bit, however It ended up messing up the Add/Remove Programs program. 
Some screen shots to prevent a long thread of typing.
Look in top right
[http://codyt07.com/images/ubuntu/help1.png](http://codyt07.com/images/ubuntu/help1.png)
[http://codyt07.com/images/ubuntu/help2.png](http://codyt07.com/images/ubuntu/help2.png)
[http://codyt07.com/images/ubuntu/help3.png](http://codyt07.com/images/ubuntu/help3.png)

Anyone know what I can do to recover and reinstall kde4?

---

### Post by CodyT07 on 2008-08-05
Care If I bump?

---

### Post by gjoellee on 2008-08-05
you can uninstall *all* KDE applications with ```
sudo apt-get remove kde*
``` 
see this page to see how to install KDE 4 in Ubuntu: [http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

---

### Post by CodyT07 on 2008-08-05
Thanks for it didn't work.
```
  skim: Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
  strigi-applet: Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
  tapiir: Depends: jackd but it is not going to be installed
  timemachine: Depends: jackd (>= 0.80.0) but it is not going to be installed
  ubuntustudio-audio: Depends: jackd but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

If I run that code and replace * with 4 it returns
```
ackage kde4 is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kubuntu-kde4-desktop: Depends: kde-window-manager but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
But KDE 4 and 3 are installed...

---

### Post by LowSky on 2008-08-05
why not run the command it tells you

```
sudo apt-get -f install
```
if that dont work try
```
sudo dpkg --configure -a
```

---

### Post by CodyT07 on 2008-08-05
Using first command returned
```
After this operation, 5005kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 232605 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.cache.bz2', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Using the second command returned

```
dpkg: dependency problems prevent configuration of kubuntu-kde4-desktop:
 kubuntu-kde4-desktop depends on kde-window-manager; however:
  Package kde-window-manager is not installed.
dpkg: error processing kubuntu-kde4-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kubuntu-kde4-desktop

```

---

### Post by CodyT07 on 2008-08-05
Er bump, don't tell me I have to do a complete reinstall...

---

### Post by CodyT07 on 2008-08-06
One last bump before I do a reinstall :(

---

### Post by oldos2er on 2008-08-06
Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by CodyT07 on 2008-08-06
```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

## Wine, Ubuntu Hardy Heron (8.04):
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main 

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```
That last line I added from the guide posted above.

---

### Post by oldos2er on 2008-08-07
Try uncommenting the Canonical 'partner' repository; then run "sudo aptitude update && sudo aptitude upgrade" in a terminal.

---

