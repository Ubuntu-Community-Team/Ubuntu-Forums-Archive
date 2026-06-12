---
title: "update error"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by bzarnsy on 2009-04-19
i am running ibex and would like to upgrade to jaunty rc so i checked
software sources and that's ok but when i reload in update manager or
synaptic i get this failed to fetch indexes error.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cariboo on 2009-04-19
I would suggest you try a different server.

Jim

---

### Post by bzarnsy on 2009-04-20
i have tried other servers but get same error.

---

### Post by Partyboi2 on 2009-04-20
Hi bzarnsy, could you open up a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by bzarnsy on 2009-04-20
bz@ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates restricted main main'.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-backports restricted main multiverse universe
# deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid main'.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-proposed restricted main multiverse main'. universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse main'. universe
bz@ubuntu:~$

---

### Post by Partyboi2 on 2009-04-20
You need to fix up your sources.list. Open a terminal and type
```
gksu gedit /etc/apt/sources.list
``` then remove the parts that I have marked in red from your sources.list.
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates restricted main [COLOR=Red]main'.[/COLOR]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-backports restricted main multiverse universe
# deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid [COLOR=Red][COLOR=black]main[/COLOR]'.[/COLOR]
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-proposed restricted main multiverse [COLOR=Red]main'. [/COLOR]universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse [COLOR=Red]main'.[/COLOR] universe
```
Then save the changes and back in the terminal type
```
sudo apt-get update
```

---

