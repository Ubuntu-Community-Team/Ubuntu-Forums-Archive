---
title: "cannot upgrade to 7.10 from 7.04"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by FarmerReg on 2008-12-19
Every time I try to upgrade my Ubuntu to 7.10 , I get error messages stating that a whole list of things failed to be retrieved/fetched. In which case the upgrade does not start.
Has anyone else had this issue with ugprading their OS from 7.04 to 7.10??

---

### Post by taurus on 2008-12-19
Can you post your /etc/apt/sources.list?  Maybe you have added some third party repos that the upgrader doesn't like.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by FarmerReg on 2008-12-19
> **taurus said:**
> Can you post your /etc/apt/sources.list?  Maybe you have added some third party repos that the upgrader doesn't like.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

Here is what popped up:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START
deb http://wine.budgetdedicated.com/apt feisty main

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by taurus on 2008-12-19
> 
#AUTOMATIX REPOS START
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

May want to remove those lines from your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by FarmerReg on 2008-12-20
Thanks. I have deleted those items and will now try the upgrade again.
Will let you know how it goes.

---

### Post by FarmerReg on 2008-12-20
I tried running the upgrade again and am still getting the same error message.

The message reads:
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
(then there's all this in a box below the error message.)
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz 404 Not Found [IP: 91.189.88.40 80]

```

I am connected to the internet and do not understand this at all.

---

### Post by Endeavorin on 2009-01-04
As per the documentation [here]("https://help.ubuntu.com/community/GutsyUpgrades"), you're supposed to have the following lines in the /etc/apt/sources.list file:

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
``` 

I added the above and am able to get till almost the end of the list, after which it fails with the same message again (i.e. 404 Not Found). However it has detected 288 updates, and i'm installing them. Hopefully, I'll get the 'upgrade' button after i'm done with the updates.

---

### Post by applefat on 2009-01-30
FarmerReg: I came here from your earlier thread about not being able to install Apache. I've been trying to do the exact same thing as you, and I was afraid this version had been entirely abandoned. But after adding those extra sources which Endeavorin pointed out, apt-get update was able to find a good deal of updates, as you said. Then using apt-get to install apache2 after that worked fine, in case you had not attempted it.

---

