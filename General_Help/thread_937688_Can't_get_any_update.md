---
title: "Can't get any update"
date: 2008-10-04
forum: General Help
---

### Post by PacoCrespo on 2008-10-04
Hello

I've just installed ubuntu 8.10 and I can't get any update although my network connections work properly

Any help please????

I'm becoming crazy

---

### Post by Perfect Storm on 2008-10-04
Try, first;

```
sudo apt-get update && sudo apt-get upgrade
```

any dice?

Lets check your Source list;
```
cat /etc/apt/sources.list
```

---

### Post by PacoCrespo on 2008-10-04
Hi Artificial Intelligence first I've tried 

[I]sudo apt-get update && sudo apt-get upgrade
[/I]
as you suggested me, but it didn't work so I tried the second

*cat /etc/apt/sources.list*

and then: (but I have no idea of what it means)

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20080930.4)]/ intrepid main restricted

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20080930.4)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
elisa@ubuntu:~$

---

### Post by geirha on 2008-10-04
Could you paste what **sudo apt-get update && sudo apt-get upgrade** writes when you run it?

---

### Post by PacoCrespo on 2008-10-04
This is what I get

elisa@ubuntu:~$ sudo apt-get upgrade && sudo apt-get upgrade
[sudo] password for elisa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elisa@ubuntu:~$

---

### Post by geirha on 2008-10-04
You ran apt-get upgrade twice, could you also paste the output of ```
sudo apt-get **update**
```

Though the output of apt-get upgrade is good. It means there are currently no updates available, though after running apt-get update there may be some.

---

### Post by PacoCrespo on 2008-10-04
elisa@ubuntu:~$ sudo apt-get update
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Sources
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Packages
  403 Forbidden
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Sources
  403 Forbidden
W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
elisa@ubuntu:~$ BB

---

### Post by geirha on 2008-10-04
Seems like the spanish archive is having problems. Untill it is fixed, you could try the main archive. You can switch by going to « System -> Administration -> Software Sources » and choose the main server instead of the spanish.

---

### Post by PacoCrespo on 2008-10-04
IT WORKS¡¡¡¡ thank you very much¡¡¡¡¡

---

### Post by madhurima on 2009-03-27
> **geirha said:**
> Seems like the spanish archive is having problems. Untill it is fixed, you could try the main archive. You can switch by going to « System -> Administration -> Software Sources » and choose the main server instead of the spanish.

hiii
even i have the same problem...even after changing to main server option its not working.I didnt hav spanish option in mine...
so please help me what i should do

---

