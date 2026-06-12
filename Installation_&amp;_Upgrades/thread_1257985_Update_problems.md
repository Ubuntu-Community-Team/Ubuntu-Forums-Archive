---
title: "Update problems"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by calvimm on 2009-09-04
Hello. I'm trying to install updates on Jaunty and i keep receiving this error message:

E: rt2860-dkms: subprocess post-installation script returned error exit status 2

and then there's a detailed error (it won't let me copy and paste)
but its along the lines of:

Error! Cannot locate /usr/src/rt2860-1.7.1.1.dkms.tar.gz.
File does not exist.

Thanks!

---

### Post by imhotep59 on 2009-09-04
It looks as if you have a problem with a repository.
Could you post the content of your /etc/apt/sources.list
```
cat /etc/apt/sources.list
```

---

### Post by calvimm on 2009-09-05
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by imhotep59 on 2009-09-06
Well, rt2860-dkms is a driver for your wifi. I think it can be located in the backports as suggested by this bug previously reported in launchapd.
([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891))

So, uncomment the following lines in your sources.list
```
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```

Then, after you just removed the # these lines should be as follow
```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

```

You can also do this with synaptic: Configuration->Repositories->Updates-> and select Jaunty-backports

Don't forget to reload your sources.list after these changes.

(This driver should be fully integrated with the next version, Karmic)

---

