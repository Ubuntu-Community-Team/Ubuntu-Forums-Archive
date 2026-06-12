---
title: "How to upgrade Firefox on 8.10"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by BuntuFirstTimer on 2009-01-21
Forgive my stupidity, but it seems that I don't have a slightest clue how to upgrade my Firefox (version 3.0.3) to 3.0.4 or 3.0.5.

Is there a way to upgrade it through a terminal?

---

### Post by Cheater87 on 2009-01-21
IIRC the update for Firefox came like all the other updates.

---

### Post by x33a on 2009-01-21
sudo apt-get install firefox

latest version in the repos is 3.0.5

---

### Post by BuntuFirstTimer on 2009-01-22
> **x33a said:**
> sudo apt-get install firefox

latest version in the repos is 3.0.5

Here's my response when I typed the sudo...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 217 not upgraded.
```

And rebooted and checked the firefox... still 3.0.3

Hmm... I wonder if I missed something.

---

### Post by Partyboi2 on 2009-01-22
Can you post your sources.list. From a terminal
```
cat /etc/apt/sources.list
```

---

### Post by BuntuFirstTimer on 2009-01-22
> **Partyboi2 said:**
> Can you post your sources.list. From a terminal

Here it is. It must be that I was doing something wrong.

```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://archive.ubuntulinux.jp/ubuntu-ja intrepid/
```

---

### Post by Partyboi2 on 2009-01-22
Your sources.list looks fine. I did notice though you have 217 packages that can be upgraded. I wonder if one of the upgrades is for firefox.
You can view and upgrade the packages from the terminal
```
sudo apt-get upgrade
``` Or you can go to update manager (System>Admin>Update Manager) and view and install the updates.
The Canada repo seems really slow at the moment so you might want to change you download server in Software Sources (System>Admin>Software Sources) on the first tab to "main" before upgrading packages.

---

### Post by walid97 on 2009-05-15
I had the exact same issue, solved it by:
```

sudo apt-get install firefox-3.0
```

---

