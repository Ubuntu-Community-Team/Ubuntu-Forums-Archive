---
title: "How did this happen?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by Russ_H on 2009-09-21
I lost the kernel in my system as well as networking and Grub after an automatic upgrade. Luckily my neighbor is a guru in such matters and managed to restore the system for me, twice. The second time he traced the problem to this in the sources list. Does anyone know how it could get like this? Apparently it was the Debian stuff at the bottom causing problems. Hopefully this may help someone else with the same problem.

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) etch main
deb [http://unicap-imaging.org/packages](http://unicap-imaging.org/packages) hardy main contrib

---

### Post by tommcd on 2009-09-22
You should not be using Debian sources in Ubuntu. Debian Etch is way older than Ubuntu 9.04 and uses an older kernel and packages. This explains why your system got screwed up while using those sources.
 Also, the Ubuntu packages are custom patched by the Ubuntu devs. Debian and Ubuntu packages are not interchangeable.

---

### Post by Russ_H on 2009-09-26
Thanks. How could the debian sources get there?, I am not aware of downloading any debian packages. Would a simple application have manged to do that?, I am not aware of any debian apps installed.

---

### Post by wojox on 2009-09-26
Did you ever download anything like this:

[http://unicap-imaging.org/](http://unicap-imaging.org/)

---

### Post by tommcd on 2009-09-26
> **wojox said:**
> Did you ever download anything like this:

[http://unicap-imaging.org/](http://unicap-imaging.org/)
Unicap is in his sources.list. I did not notice that at first. 

Russ_H,
Did you add the unicap repo to your sources.list as it says on the Unicap site?
[http://unicap-imaging.org/using_repositories.htm](http://unicap-imaging.org/using_repositories.htm)
And did you ever add anything to your sources.list

Wojox,
I am not familiar with Unicap. Do you know if Unicap would have added the Debian repos to Russ's sources.list?

Anyway, this illustrates the danger of adding 3rd party repos to your sources.list.

---

### Post by Russ_H on 2009-09-27
> **wojox said:**
> Did you ever download anything like this:

[http://unicap-imaging.org/](http://unicap-imaging.org/)


Guilty I am afraid. I thought it would be OK as it was Ubuntu installation, oh how naive!. 


One question, how does a camera application manage to get to delete the kernel? it should have no business doing anything with it.

---

