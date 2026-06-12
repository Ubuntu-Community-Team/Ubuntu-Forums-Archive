---
title: "Update problem"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by vajeen on 2009-08-01
i use ubuntu 9.04 
when i try to update it i get........
> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message



plz help!!!!!!!!!!!!!!

---

### Post by Soul-Sing on 2009-08-01
I think you have to copy/paste your sources.list here.

---

### Post by Buce on 2009-08-01
Your /etc/apt/sources.list, to be precise. For good measure, type this from a terminal (Applications -> Accessories -> Terminal) and paste the results here.

```
cat /etc/apt/sources.list{,.d/*}
```

---

### Post by vajeen on 2009-08-01
i got this after cat /etc/apt/sources.list{,.d/*} in the terminal

> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty universe
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty multiverse
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-security main restricted
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-security universe
deb [http://ubuntu.indika.net.id/](http://ubuntu.indika.net.id/) jaunty-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # disabled on upgrade to jaunty
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # disabled on upgrade to jaunty
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb mirror://www.getdeb.net/playdeb-mirror/jaunty jaunty/
deb mirror://www.getdeb.net/playdeb-mirror/jaunty jaunty/


---

### Post by vajeen on 2009-08-15
vajeen@vajeen-desktop:~$ sudo apt-get update
E: Method gave invalid 400 URI Failure message

---

### Post by Partyboi2 on 2009-08-15
Hi, looks like you problem could be due to the
> deb mirror://www.getdeb.net/playdeb-mirror/jaunty jaunty/
Have a try at the possible solution mentioned [[COLOR=Blue]here[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/74488")

---

