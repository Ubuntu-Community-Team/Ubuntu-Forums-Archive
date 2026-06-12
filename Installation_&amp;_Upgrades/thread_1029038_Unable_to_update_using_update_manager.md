---
title: "Unable to update using update manager"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Ionna on 2009-01-03
Running Intrepid Ibex, amd64, unable to update since about 2 weeks ago. Update Manager tells me that there are no updates, but my friend who's also running Ibex tells me he just updated a few hours ago. Help!

---

### Post by Partyboi2 on 2009-01-03
Have you got updates enabled in Software Sources under updates tab?

---

### Post by Ionna on 2009-01-03
Yes. I have Important Security Updates, Recommended Updates and Unsupported Updates ticked.

---

### Post by Partyboi2 on 2009-01-03
Have you tried to reload the package list first
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ionna on 2009-01-03
Yes. It tells me nothing was changed.

---

### Post by Ionna on 2009-01-03
Anyone? Help?

---

### Post by timking on 2009-01-03
I'm having the same problem and have gone through the steps as suggested above. Still no updates.

---

### Post by zvacet on 2009-01-03
```
cat /etc/apt/sources.list
```

and maybe your friend have backports enabled and you don´t.Just a guess.

---

### Post by Ionna on 2009-01-04
I actually do have backports enabled, so I don't think that's the answer. 

Weirdly enough, I just switched back to Ubuntu after using Windows XP last night and now my updates are happening as normal. @@

I'll do this later when the updates are done. ```
cat /etc/apt/sources.list
```

---

### Post by Ionna on 2009-01-05
This was what I got when I did cat. What does it mean, actually?

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
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
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by zvacet on 2009-01-05
```
gksudo gedit /etc/apt/sources.list
```

remove all lines after **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse** and put # sign in front of deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe

and add 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ionna on 2009-01-05
That seemed to have worked. Thank you!

---

