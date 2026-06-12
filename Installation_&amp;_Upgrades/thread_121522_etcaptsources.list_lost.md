---
title: "/etc/apt/sources.list lost"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by rowanparker on 2006-01-25
Hello, I'm new to ubuntu (and linux), I installed ubuntu last week
Didn't know where this should go and i thought here might be right, if wrong, sorry.
I was trying to change my /etc/apt/sources.list to better mirrors, and i backed it up before i changed it, but then i changed it again and backed that up therefore loosing the orginal. I have been looking around for what to do but to no avail.
Please can someone post what should be in the file, or what you use. Or put me in the right direction.

Thanks, Rowan.

---

### Post by dueY on 2006-01-25
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

---

### Post by rowanparker on 2006-01-25
thanks :D 
works great!

Rowan.

---

