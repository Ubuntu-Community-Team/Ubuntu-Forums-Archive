---
title: "broken package wont fix"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by babujbf on 2008-12-16
tried to install a package, it failed because of dependency and I tryed to fix it in synaptic but it cause this error:
Screenshot of window
[[IMG]http://img201.imageshack.us/img201/9498/screenshotchangesappliejc5.png[/IMG]](http://imageshack.us)
[[IMG]http://img201.imageshack.us/img201/screenshotchangesappliejc5.png/1/w531.png[/IMG]](http://g.imageshack.us/img201/screenshotchangesappliejc5.png/1/)

---

### Post by taurus on 2008-12-16
Close synaptic.  Then, open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by babujbf on 2008-12-16
same error in terminal

---

### Post by doobiest on 2008-12-16
would an apt-get purge on the linux-backports package help?

---

### Post by taurus on 2008-12-16
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by babujbf on 2008-12-16
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-properties

---

### Post by babujbf on 2008-12-16
apt-get purge no go

---

### Post by taurus on 2008-12-16
Looks like you don't have a whole lot of repos on your machine.  Go in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check to all the options except the last one, Source code.  Click Close and Reload.

Now, look at your /etc/apt/sources.list again to see if there are more repos available in there.

---

