---
title: "duplicate sources.list entry"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by miazma on 2009-01-10
Hello,

I get a lot of duplicate sources.list entry messages:

```

W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/restricted Translation-de (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_restricted_i18n_Translation-de)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/main Translation-de (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_main_i18n_Translation-de)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/multiverse Translation-de (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_multiverse_i18n_Translation-de)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com intrepid-updates/universe Translation-de (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_universe_i18n_Translation-de)
W: Probieren Sie »apt-get update«, um diese Probleme zu korrigieren.

```

but it seems I haven't got any duplicates:

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu intrepid partner
#deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

# Avant Window Navigator 
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe

# wicd
deb http://apt.wicd.net intrepid extras

deb http://ppa.launchpad.net/mvo/ubuntu intrepid main

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main

```

greetings,
Johannes

---

### Post by Partyboi2 on 2009-01-10
remove
```
deb http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe
```from your sources.list
```
gksu gedit /etc/apt/sources.list
```then 
```
sudo apt-get update
``````
# Avant Window Navigator 
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
[COLOR=Red]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates restricted main multiverse universe[/COLOR]
```

---

### Post by miazma on 2009-01-10
oh, thank you very much :-)

---

