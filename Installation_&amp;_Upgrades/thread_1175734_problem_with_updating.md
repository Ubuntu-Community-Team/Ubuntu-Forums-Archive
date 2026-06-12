---
title: "problem with updating"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by themacedonian on 2009-06-01
I sow message like this :
if you dont update and upgrade your system you may have problems with your network connestion.

i cant update my ubuntu :

PG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513Failed to fetch [http://download.tuxfamily.org/screenlets/dists/edgy/screenlets/binary-i386/Packages.gz](http://download.tuxfamily.org/screenlets/dists/edgy/screenlets/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/screenlets/dists/feisty/screenlets/binary-i386/Packages.gz](http://download.tuxfamily.org/screenlets/dists/feisty/screenlets/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


what i need to do ?

---

### Post by _Purple_ on 2009-06-01
Are you using Gutsy?

---

### Post by themacedonian on 2009-06-01
i dont know what it is :D:D

what do you think, what is my problem ?
any idea ?

---

### Post by MichaelSammels on 2009-06-01
Do you know the version number? Gutsy is 8.04

---

### Post by _Purple_ on 2009-06-01
> **themacedonian said:**
> i dont know what it is :D:D

what do you think, what is my problem ?
any idea ?

Open a terminal (Applications> Accessories > Terminal) and type the following and post the output here. This will show which version you are using.
```
lsb_release -a

```

---

### Post by themacedonian on 2009-06-01
> **_Purple_ said:**
> Open a terminal (Applications> Accessories > Terminal) and type the following and post the output here. This will show which version you are using.
```
lsb_release -a

```


```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

```

any idea ? 
original message: 

the update information is outdated. this may caused by network problems. please updade manually by clicking on this icon and then selecting chek.

when i click "check" i see message like first post on this threat :S



help ?
idea ?

---

### Post by _Purple_ on 2009-06-01
You are using Hardy(8.04) but one of your sources entires is for Gutsy(7.10). Can you please post the content of 
```
gedit /etc/apt/sources.list
```

---

### Post by themacedonian on 2009-06-02
i asked my brother, but he dont know how solve uor problem


here is output .... i write gedit /etc/apt/sources.list
in terminal


```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://mk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://mk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse


# za anjuta and stuff. By Aleks

deb http://ppa.launchpad.net/robster/ubuntu gutsy main
deb http://download.tuxfamily.org/screenlets edgy screenlets
deb http://download.tuxfamily.org/screenlets feisty screenlets
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use
```


any idea ?

---

### Post by sumitc on 2009-06-02
Type this command in a terminal
> gksudo gedit /etc/apt/sources.list

Then delete the last 7 lines from the file so that the last entry in the file reads

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Then save and exit the terminal. Now upgrade should work.

---

### Post by themacedonian on 2009-06-02
> **sumitc said:**
> Type this command in a terminal


Then delete the last 7 lines from the file so that the last entry in the file reads



Then save and exit the terminal. Now upgrade should work.

i did it and then reload sinaptik package manager, on my screen i view this message :
```

W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_gilir_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/universe Packages (/var/lib/apt/lists/ppa.launchpad.net_gilir_ubuntu_dists_hardy_universe_binary-i386_Packages)

```

Now ? what i need to do for solving my problem ?

thanks in advance

---

### Post by _Purple_ on 2009-06-02
From terminal run
```
sudo apt-get update
```

If you still get any error, post it here.

---

### Post by themacedonian on 2009-06-06
> **sumitc said:**
> Type this command in a terminal


Then delete the last 7 lines from the file so that the last entry in the file reads



Then save and exit the terminal. Now upgrade should work.

this worked for me.
my problem has solved.
thank you so much

---

