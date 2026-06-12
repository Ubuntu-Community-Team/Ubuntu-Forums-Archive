---
title: "apt broken"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by ashvala on 2008-12-04
My apt is broken!

I tried upgrading wine & see this:
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  wine-dev
The following packages will be upgraded:
  wine-dev
1 upgraded, 0 newly installed, 0 to remove and 285 not upgraded.
Need to get 0B/1334kB of archives.
After this operation, 1221kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Segmentation fault

Any help guys??

--
Ashvala

---

### Post by taurus on 2008-12-04
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by ashvala on 2008-12-05
sure,

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
# Line commented out by installer because it failed to verify:

# deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
# deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy main
deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

```

There, My /etc/apt/sources.list

Any help?

I also went to this webpage which said i have to clear all the apt caches @ /vat/cache/apt. But turned out to be of no use.

Ty
Ashvala

(extra info: this is hardy ;))

---

### Post by littlebat on 2008-12-05
I have ever run into this question, and fix it just type some commands like "sudo apt-get clean" "sudo apt-get autoclean" "sudo apt-get update". You can try.

---

### Post by ashvala on 2008-12-05
this is what happens: 
root@shakti:/var/cache/apt# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  wine-dev
The following packages will be upgraded:
  wine-dev
1 upgraded, 0 newly installed, 0 to remove and 285 not upgraded.
Need to get 1334kB of archives.
After this operation, 1221kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main wine-dev 1.1.9~winehq0~ubuntu~8.04-0ubuntu1 [1334kB]
Fetched 1334kB in 13s (101kB/s)                                                
Segmentation fault

i did apt-get clean... Seemed to help for a while but it failed me :(

---

### Post by inobe on 2008-12-05
```
sudo dpkg --configure -a 
```

a shot in the dark


```
sudo apt-get update
```



```
sudo apt-get upgrade
```

edit: in synaptic also try fixing broken packages

---

### Post by ashvala on 2008-12-05
I dont have a problem with apt-get update... it is only with apt-get install...

---

### Post by ashvala on 2008-12-05
Now, my apt-get upgrade segfaulted :( what do i do??

---

