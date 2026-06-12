---
title: "[SOLVED] Unable to upgrade to Firefox 3 final in Ubuntu 8.04"
date: 2008-07-09
forum: General Help
---

### Post by Tomasthanes on 2008-07-09
I tried that command line ("sudo apt-get install firefox-3.0") as well as trying to upgrade from 3.0b5 using the Synaptic Package Manager and I'm still on b5.

I have 3 Ubuntu HH 8.04 systems and each of them seems to have a different set of repositories.  That's what I'm guessing my issue is.

The apt-get is going out and finding "firefox-3.0" but given the repositories on this particular system, the b5 is the only version still available.

Any suggestions on how to fix this?

---

### Post by Tomasthanes on 2008-07-09
> **stchman said:**
> What Ubuntu are you running?  In Ubuntu Hardy it is the default.  In Kubuntu it is in the repos.

I'm running HH 8.04.  Installed fresh from CD (not upgraded from the prior version).

When HH first came out, FF 3.0 (final) wasn't available so they put one of the pre-release versions.  That appears to be the one I'm stuck on.

Thank you.

---

### Post by aysiu on 2008-07-09
> **Tomasthanes said:**
> I tried that command line ("sudo apt-get install firefox-3.0") as well as trying to upgrade from 3.0b5 using the Synaptic Package Manager and I'm still on b5.

I have 3 Ubuntu HH 8.04 systems and each of them seems to have a different set of repositories.  That's what I'm guessing my issue is. So paste the output of ```
cat /etc/apt/sources.list
``` back here.

---

### Post by Tomasthanes on 2008-07-09
> **aysiu said:**
> So paste the output of ```
cat /etc/apt/sources.list
``` back here.

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security universe
# Line commented out by installer because it failed to verify:
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy main universe restricted
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security multiverse

---

### Post by aysiu on 2008-07-09
You seem to have a mix of Ubuntu 7.10 and Ubuntu 8.04 repositories. That's not good.

Can you post the output of this command as well? ```
cat /etc/lsb-release
```

---

### Post by Tomasthanes on 2008-07-09
> **aysiu said:**
> You seem to have a mix of Ubuntu 7.10 and Ubuntu 8.04 repositories. That's not good.

Can you post the output of this command as well? ```
cat /etc/lsb-release
```

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

---

### Post by Tomasthanes on 2008-07-09
> **aysiu said:**
> You seem to have a mix of Ubuntu 7.10 and Ubuntu 8.04 repositories. That's not good.

Can you post the output of this command as well? ```
cat /etc/lsb-release
```

You mentioned the mix of repositories.  Would you like me to comment out the "gutsy" repositories and only leave the "hardy" ones?

Thank you, by the way.  I really appreciate your help!

---

### Post by aysiu on 2008-07-09
> **Tomasthanes said:**
> You mentioned the mix of repositories.  Would you like me to comment out the "gutsy" repositories and only leave the "hardy" ones?

Thank you, by the way.  I really appreciate your help!
Since the Gutsy repositories should not be reactivated unless you want to break your system, you should delete them completely instead of just commenting them out. ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.broken
gksudo gedit /etc/apt/sources.list
``` Paste in ```
deb http://ftp.ucr.ac.cr/ubuntu/ hardy main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy main restricted universe multiverse
deb http://ftp.ucr.ac.cr/ubuntu/ hardy-security main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy-security main restricted universe multiverse
deb http://ftp.ucr.ac.cr/ubuntu/ hardy-updates main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy-updates main restricted universe multiverse
``` Save and exit. ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Tomasthanes on 2008-07-10
That worked!  I discovered that when I did an "install over" (7.10 --> 8.04), for some reason, it didn't reformat the root file system and just wrote the files on top of the others.

I did a clean re-install yesterday and am up and working.

THANK YOU for your assistance!

> **aysiu said:**
> Since the Gutsy repositories should not be reactivated unless you want to break your system, you should delete them completely instead of just commenting them out. ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.broken
gksudo gedit /etc/apt/sources.list
``` Paste in ```
deb http://ftp.ucr.ac.cr/ubuntu/ hardy main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy main restricted universe multiverse
deb http://ftp.ucr.ac.cr/ubuntu/ hardy-security main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy-security main restricted universe multiverse
deb http://ftp.ucr.ac.cr/ubuntu/ hardy-updates main restricted universe multiverse
#deb-src http://ftp.ucr.ac.cr/ubuntu/ hardy-updates main restricted universe multiverse
``` Save and exit. ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by stchman on 2008-07-10
> **Tomasthanes said:**
> I'm running HH 8.04.  Installed fresh from CD (not upgraded from the prior version).

When HH first came out, FF 3.0 (final) wasn't available so they put one of the pre-release versions.  That appears to be the one I'm stuck on.

Thank you.

In 8.04 you will be updated to Firefox 3.0 final.  No need to download and install.

---

