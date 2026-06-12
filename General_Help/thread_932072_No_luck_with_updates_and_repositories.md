---
title: "No luck with updates and repositories"
date: 2008-09-28
forum: General Help
---

### Post by elbow rub on 2008-09-28
I think I may be confused while adding new repositories. I followed what was listed under adding, removing and updating application [file:///usr/share/gnome/help/add-applications/C/add-applications.xml#extra-repositories-adding]("file:///usr/share/gnome/help/add-applications/C/add-applications.xml#extra-repositories-adding"). Doing the steps, I ended up with the following error:

> W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277 


Afterwards, it wanted me to do a partial, ecause of the procedure above, it said and then I got this error:

> It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
initscripts
libavc1394-0
sysv-rc
sysvinit-utils

> Out of curiosity I ran sudo apt-get update and got this:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Any help will be appreciated, 
Thanks

---

### Post by zvacet on 2008-09-28
In general it is not good idea to mix repos,but you can do this in terminal

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys A70DAF536070D3A1
gpg --export --armor A70DAF536070D3A1 | sudo apt-key add -
```

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  B5D0C804ADB11277
gpg --export --armor  B5D0C804ADB11277 | sudo apt-key add -
```

---

### Post by elbow rub on 2008-09-28
Well, that makes sense not to mix them, I didn't intend to. As I was trying to follow the guide, it also wanted me to do updates. Having said that, should I still follow your steps? I don't want to mix up and make it harder for myself. Or are your steps the correct way to accomplsh this now and in the future?


Thank you very much

---

### Post by zvacet on 2008-09-28
For how to add repos read [this.]("https://help.ubuntu.com/community/Repositories/Ubuntu") I don´t know what are you try to install from debian repos.Maybe same thing can be done other way then add debian repo.You can go to the erminal and 

```
gksudo gedit /etc/apt/sources.list
```

and delete all debian repos from your source list.After that save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

You can also 

```
cat /etc/apt/sources.list
```

and post it here.

---

### Post by elbow rub on 2008-09-29
I didn't find anything debian related to edit out of the source.lst. What I was just trying to accomplish was setting the system up, following the Ubuntu Help Center, starting with this link [file:///usr/share/gnome/help/add-applications/C/add-applications.xml]("file:///usr/share/gnome/help/add-applications/C/add-applications.xml"). I hadn't used Linux since Breezy and several things have happened, therefore I'm starting from square 1.

> gian@gian-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
gian@gian-desktop:~$ 

Thanks for your help
elbow rub:)

---

### Post by zvacet on 2008-09-29
I can not open link you posted to see what guide you used.Your source list looks good.Look in **/etc/apt/sources.list.d** and see if there is any debian.org etch line.If it is remove it.

```
sudo apt-get update
```

---

### Post by elbow rub on 2008-09-29
I looked in ***/etc/apt/sources.list.d ***, and under the third party tab there was an entry ***deb [http://ftp.debian.org](http://ftp.debian.org) etch main***, which was in the tutorial I was following. Apparently I misunderstood something, is there a proper way of adding repositories?

Thanks

---

### Post by zvacet on 2008-09-29
Remove that entry.For how to add repositories read [this.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by elbow rub on 2008-09-29
Thank you for all your help and patience.

:guitar:

---

