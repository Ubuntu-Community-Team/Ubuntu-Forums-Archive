---
title: "Broken packages when trying to install Filezilla"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Jshaw on 2009-03-07
Hey everyone,

I tried to install Filezilla today, but when I used the terminal I was met with "Broken packages." I then tried Synaptic but I was met with a similar error, I took a capture below.

if someone could help me that would be appreciated. I'm running Ubuntu 8.04

---

### Post by taurus on 2009-03-07
Make sure you close down synaptic first.  Then, post the outputs of these two commands, running one at a time, from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install filezilla
```

---

### Post by Jshaw on 2009-03-08
ok, Since there were no errors with the apt-get update command I won't post it, but there was the same error when I tried to install filezilla.

>  sudo apt-get install filezilla
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  filezilla: Depends: libgnutls26 (>= 2.4.0-0) but it is not installable
             Depends: libwxbase2.8-0 (>= 2.8.8.0) but it is not going to be installed
             Depends: libwxgtk2.8-0 (>= 2.8.8.0) but it is not going to be installed
E: Broken packages


Thanks for replying! I was wondering if anyone would lol.

---

### Post by taurus on 2009-03-08
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Neo_The_User on 2009-03-08
```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install -f

```

---

### Post by zvacet on 2009-03-08
In system>admin>software sources check that you have universe repo enabled.If you don´t enable it and reload.After that try again to install.

---

### Post by Jshaw on 2009-03-08
> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```


Here it is:

>  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main
deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) stable non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
# deb [http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/) ./
# deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) gutsy main restricted universe multiverse
# deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

# deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

# Eternity Screensaver
deb [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main
deb-src [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main
deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main



And to zvacet, I can't seem to see the repository you were talking about. I wonder how it could've been removed. *shrugs*

---

### Post by taurus on 2009-03-08
```
deb http://archive.canonical.com/ubuntu gutsy partner
```

You have one repo from gutsy.  You need to edit /etc/apt/sources.list and remove that repo.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Neo_The_User on 2009-03-08
> **taurus said:**
> ```
deb http://archive.canonical.com/ubuntu gutsy partner
```

You have one repo from gutsy.  You need to edit /etc/apt/sources.list and remove that repo.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

It's sudo apt-get dist-upgrade

Don't forget to do sudo apt-get install -f

---

### Post by Jshaw on 2009-03-09
I'm afraid it's still not working.

---

### Post by taurus on 2009-03-09
What are the outputs of these commands?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bashar &quot; on 2009-03-22
```
aptitude install filezilla
``` worked for me

---

