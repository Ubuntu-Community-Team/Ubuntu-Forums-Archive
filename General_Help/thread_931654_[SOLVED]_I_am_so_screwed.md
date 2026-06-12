---
title: "[SOLVED] I am so screwed"
date: 2008-09-27
forum: General Help
---

### Post by jobo1313 on 2008-09-27
Hello, recently i discovered the compiz-beryl desktop effects.
well it was awesome but my package manager said i had a broken package so i told it to fix the package. the package was compizconfig-settings-manager. Now i cant reinstall it and it removed all my effects and everything.
The error i get is:
compizconfig-settings-manager:
 Depends: python-compizconfig but it is not going to be installed


I cant install that either its tells me i cant.
Please help!!!!!!!!!!!!

---

### Post by jpeddicord on 2008-09-27
Could you post the complete output of the following three commands?

```
sudo apt-get install compizconfig-settings-manager
```
```
sudo apt-get install python-compizconfig
```
```
cat /etc/apt/sources.list
```

---

### Post by jobo1313 on 2008-09-27
Here is the read out:

john@JohnBoland-Laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-settings-manager: Depends: python-compizconfig (>= 0.7.2) but it is not going to be installed
E: Broken packages
john@JohnBoland-Laptop:~$ sudo apt-get install python-compizconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-compizconfig: Depends: libcompizconfig0 but it is not going to be installed
E: Broken packages
john@JohnBoland-Laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
john@JohnBoland-Laptop:~$

---

### Post by jpeddicord on 2008-09-27
**EDIT:** Ignore this, see the post below.

Hmm.. odd. It seems that some packages are missing from your local listing. Did you happen to cancel an update earlier?

Regardless, run

```
sudo apt-get update
```

Or click "Check" in Update Manager, "Reload" in Synaptic. That should at least omit that possibility if it doesn't fix the problem.

---

### Post by eapache on 2008-09-27
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main

Those two lines in your source.list file are the problems. Remove them, then```
sudo apt-get update
sudo apt-get upgrade
```

and installing compiz-config should now work.

You were trying to mix intrepid and hardy packages.

---

### Post by jpeddicord on 2008-09-27
> **eapache said:**
> deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main

Those two lines in your source.list file are the problems. Remove them, then```
sudo apt-get update
sudo apt-get upgrade
```

and installing compiz-config should now work.

You were trying to mix intrepid and hardy packages.

Ah - didn't see those, good catch.

---

### Post by jobo1313 on 2008-09-27
There are no words that can describe my happiness right now.
thank you:popcorn:

---

### Post by steveneddy on 2008-09-27
Please mark this as solved.

---

