---
title: "Synaptic Package Manager Hangs"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by psidre.felix on 2008-12-23
I wish I had a better idea of when this started happening, but here's the issue:

The past several times I have used the Synaptic Package Manager, the application goes grey and hangs for anywhere from 20secs to several minutes whenever Reloading or Marking a package with any option (Install/Remove/etc).

I notice that my memory usage at the times this is happening is not exceeding more than 20-25%, but my CPU is holding around 90-100%.

I've noticed the same thing happening with other applications lately as well, but not every time: Gnome Help, Rythmbox - seems to be programs that access large files or directories/sources where there are many files to read.

Is there something specific I can cross-reference in my logs to try and pinpoint what I may have installed that is causing this?

Here's my specs as best as I can relate right now:

Ubuntu 8.10 64-bit

AMD64 3800+
2GB DDR
NVidia (v1.77 Prop. Driver) 512MB 
100GB of partitions on the rear-end of WD 1TB ext. USB2.0 HD

(At first I thought it might be the external drive being where my system partitions are located, but I did not experience any read/write issues on the first installation of ubuntu - I had to re-install from scratch cause I rEALLy jacked up my x.)

I'm running with a basic desktop install with the following packages added:

Apache + Samba server dependencies
Ubuntu Studio (Complete)
Amaya
Wine (haven't used this yet)

I just today adjusted my swappiness to 8 and my cache pressure to 64 but I still have the same result. Everything else is just spiffy.

If by chance the Synaptic PM has gone corrupted, is it wise to reinstall it and see if that fixes the problem?

Thanx for the time - I don't wanna go acting like I know what I'm doing and end up having to do another scratch run this soon.

psidre

---

### Post by Pumalite on 2008-12-23
Post your /etc/apt/sources.list
Also: have you been able to install anything?

---

### Post by bayank on 2008-12-30
Hey ya'll,

I'm having the same exact issue as op, on ubuntu 8.10. I tried reinstalling ubuntu as well, and even then with the fresh install synaptic hangs for a few mins then comes back every time i mark a package for install/removal etc.. I am able to successfully install stuff with it though, i just have to wait a while before i can apply changes. then once it finishes installing whatever, it hangs again until it comes back to the package listing. This is somethign new btw, never had a problem wit synaptic until recently. May have been a new update? idk but at least it still works

here is my sources.list:

```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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
```

---

