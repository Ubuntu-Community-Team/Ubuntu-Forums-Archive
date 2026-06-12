---
title: "Add/Remove Missing...Synaptic is Gone Bad!"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by esafwan on 2008-12-28
Hi,
I had some problem with the syanptic...even after we add any repository it was not showing(after reloading also).
[COLOR="Red"]**So i Uninstalled and Re-installed it.**[/COLOR]
I used terminal for that!
_________________________________________

Now after Re-Installation i have the following problem:
> 1.Add/Remove is missing.(Not in the Edit Menu also)
2.Synaptic search is not functioning well. I mean if i'm searching _softwares in the official channel like VLC its not there...but it doesn't _mean its empty...it has many thing we rarely need.
3.Synaptic is mainly showing the installed ones.
___________________________________________
[SIZE="6"][COLOR="DarkOliveGreen"]
I'm using Ubuntu 8.10 Intrepid 32 bit[/COLOR][/SIZE]

---

### Post by taurus on 2008-12-28
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by esafwan on 2008-12-28
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://apt.linex.org/linex/gambas/stable/ ./
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://apt.linex.org/linex/gtk-2.10/ ./
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb http://www.kiberpipa.org/~minmax/cinelerra/builds/athlonxp/ ./

```

---

