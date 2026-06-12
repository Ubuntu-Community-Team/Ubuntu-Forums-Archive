---
title: "Nothing installs"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by arcticgoldfish on 2009-03-06
Hi,

I installed Kino the other day using the Add/Remove applications tool without any issues.  I also installed some of the updates the OS flagged, again with no issues.  I have since tried to install DeVeDee and another 44 updates that are flagged at the moment - and they won't installed.

In the case of DeVeDee, I get a request for admin password, followed by a % bar which starts upwards and gets to check dependencies before it bombs out to *Application Installation Failed*.  

In the case of the updates, I click install updates, a % bar reaches full and just bombs back to update manager where it offers me the same install updates window.

I have also tried the DeVeDee website and the Appnr website - all of which just don't do anything.

Any suggestions would be gratefully recieved - I really want some software to create a DVD movie!!  Thanks.

---

### Post by oldos2er on 2009-03-06
Can you run the following command in a terminal, and post the output here?
```
sudo apt-get update && sudo apt-get safe-upgrade
```

---

### Post by arcticgoldfish on 2009-03-06
Hi - nothing happens.

james@james-laptop:~$ sudo apt-get update && sudo apt-get safe-upgrade
[sudo] password for james: 
james@james-laptop:~$

---

### Post by taurus on 2009-03-06
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by arcticgoldfish on 2009-03-06
> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by taurus on 2009-03-06
Post the outputs of these two commands, running one at a time.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by arcticgoldfish on 2009-03-06
> **taurus said:**
> Post the outputs of these two commands, running one at a time.

```
sudo apt-get update
sudo apt-get upgrade
```
james@james-laptop:~$ sudo apt-get update
[sudo] password for james: 
james@james-laptop:~$ 

james@james-laptop:~$ sudo apt-get upgrade
[sudo] password for james: 
james@james-laptop:~$ 

Password problem??

---

### Post by taurus on 2009-03-06
What's the output of this command?

```
id
```

---

### Post by arcticgoldfish on 2009-03-06
> **taurus said:**
> What's the output of this command?

```
id
```
uid=1000(james) gid=1000(james) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(james)

---

