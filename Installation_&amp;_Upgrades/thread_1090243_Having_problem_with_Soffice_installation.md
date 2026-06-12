---
title: "Having problem with Soffice installation"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by idom on 2009-03-08
I was trying to upgrade soffice 2.4 to soffice by following instruction on
<http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml>

However, I messed up something and I do not remember  how. Now even soffice 2.4 is uninstalled and when I am trying to install openoffice-calc it is saying that openoffice -core is not marked for installation. When I try to install openoffice-core 
Error is \
openoffice.org-core:
 Depends: libdb4.7  but it is not installable
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu4 is to be installed
 Depends: libhunspell-1.2-0 (>=1.2.4) but it is not installable
 Depends: libhyphen0 but it is not going to be installed
  Depends: libneon27 (>=0.28.2) but 0.27.2-1 is to be installed
 Depends: libstlport4.6ldbl  but it is not installable
 Depends: ure but it is not going to be installed

Help is greatly appreciated. 
I am new to ubuntu.

Cheers
Idom

---

### Post by Partyboi2 on 2009-03-08
Can you post your sources.list please.
```
cat /etc/apt/sources.list
```

---

### Post by idom on 2009-03-08
> **Partyboi2 said:**
> Can you post your sources.list please.
```
cat /etc/apt/sources.list
```
Here it is 

cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy restricted main
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by Partyboi2 on 2009-03-08
Your problem is probably caused because of the 
```
 deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
```repo. Mixing repos can do funny things. I would suggest disabling or removing the above repo  by going to Software Source (System>Admin>Software Sources>3rd Party)  then try installing openoffice.org-core again.

Edit: You should be able to add
```
 deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main 
``` if you still want to install oo3 for hardy.

---

### Post by idom on 2009-03-14
Thanks mate

That worked. 

Idom

---

