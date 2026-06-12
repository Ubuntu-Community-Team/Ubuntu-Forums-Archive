---
title: "Cant install kde 4.2 in ubuntu 8.10"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Roosje on 2009-02-04
I am unable to install KDE 4.2 after following the steps to add the repo, and adding the key.
Selecting the kde packet gives the following error

kde:
 Depends: kdegraphics but it is not going to be installed
 Depends: kdeutils but it is not going to be installed

A shame i was very curious how KDE was developing.
Does anyone know how to fix this?

Wilco

---

### Post by taurus on 2009-02-04
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Roosje on 2009-02-04
> **taurus said:**
> Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid main restricted
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates main restricted
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid universe
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid universe
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates universe
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid multiverse
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid multiverse
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates multiverse
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security main restricted
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security main restricted
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security universe
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security universe
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security multiverse
deb-src [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main #OpenOffice.org
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main #Firefox
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main #Compiz Fusion
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main #GNOME Do
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #Wine
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free #Medibuntu
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
deb [http://ubuntu.tiscali.nl/](http://ubuntu.tiscali.nl/) intrepid-backports restricted main multiverse universe
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main

---

### Post by taurus on 2009-02-04
Did you have koffice-data-kde4 package installed because you have to remove it first before you can install KDE 4.2?

Otherwise, run

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by Roosje on 2009-02-04
> **taurus said:**
> Did you have koffice-data-kde4 package installed because you have to remove it first before you can install KDE 4.2?

Otherwise, run

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

No, i did not have that installed, but a note somewhere else set me on the right track, typing this from 4.2 right now ;-)

sudo aptitude install kubuntu-desktop

did it for me! It gave some warnings (about gwenview and such) but installed..

No idea why apt-get does not do it, but aptitude works.

---

