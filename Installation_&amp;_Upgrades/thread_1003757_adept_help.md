---
title: "adept help"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by terrordrone on 2008-12-06
Hi,

I am new to kubuntu. Was using ubuntu all these days. Liked synaptic more than adept as of yet :P.

i enabled a few repositories..  
```

# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to                       
# newer versions of the distribution.                                                           

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```



But when i goto browse.. and search for perl or php5 or build-essential ..  it shows no matches found. Am i missing something?

please help me out.

---

### Post by taurus on 2008-12-06
Close down synaptic if you still have it open.  Then, open a terminal and see what happens when you run these commands.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by terrordrone on 2008-12-06
it installed from the command line. But why isnt adept showing it? 

It helps me manage software better.  Are there any repositories i am missing?

i tried apt-get mysql and it says no such package

I am not that good at linux.. so i prefer a GUI to get a better feel of whats heppening..

---

### Post by terrordrone on 2008-12-06
btw im on kubuntu .. so i have to use adept  3

---

