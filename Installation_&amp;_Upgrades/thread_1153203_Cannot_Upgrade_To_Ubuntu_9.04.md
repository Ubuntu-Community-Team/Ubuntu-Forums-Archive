---
title: "Cannot Upgrade To Ubuntu 9.04"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by loweehahn on 2009-05-08
Hi! I'm quite a beginner in Ubuntu. Lately I tried to upgrade my Ubuntu 8.10 to 9.04. Firstly I installed all the updates in 8.10 but during the installation my laptop froze and after restarting it I couldn't continue to install because of the error dpkg - a something like this but I resolved it. After installing all the updates I clicked on the upgrade to Ubuntu 9.04 but a 2nd problem arose. Now during the fetching of updates or something like that it stated that certain information from a certain respiratories couldn't be fetched and the upgrading couldn't be continued. I tried changing to another download server located in the Software Sources but still coulen't resolve it. Please help me. Thanks.

---

### Post by aysiu on 2009-05-08
Can you paste these command in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
cat /etc/lsb-release
cat /etc/issue
```

---

### Post by loweehahn on 2009-05-08
ren@ren-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid main restricted
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates main restricted
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid universe
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid universe
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates universe
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid multiverse
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid multiverse
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates multiverse
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security main restricted
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security main
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security universe
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security universe
deb [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security multiverse
deb-src [http://ubuntu.utalca.cl/](http://ubuntu.utalca.cl/) intrepid-security multiverse
ren@ren-laptop:~$ sudo apt-get update
[sudo] password for ren: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_SG
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_SG
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid Release.gpg
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/main Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/restricted Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/universe Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/multiverse Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates Release.gpg
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/main Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/restricted Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/universe Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/multiverse Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security Release.gpg
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/main Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/restricted Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/universe Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/multiverse Translation-en_SG
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid Release
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates Release
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security Release
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/main Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/restricted Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/main Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/universe Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/universe Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/multiverse Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/multiverse Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/main Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/restricted Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/main Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/universe Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/universe Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/multiverse Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/multiverse Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/main Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/restricted Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/main Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/universe Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/universe Sources
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/multiverse Packages
Ign [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/multiverse Sources
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/main Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/restricted Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/main Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/universe Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/universe Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/multiverse Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid/multiverse Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/main Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/restricted Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/main Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/universe Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/universe Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/multiverse Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-updates/multiverse Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/main Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/restricted Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/main Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/universe Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/universe Sources
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/multiverse Packages
  404 Not Found
Err [http://ubuntu.utalca.cl](http://ubuntu.utalca.cl) intrepid-security/multiverse Sources
  404 Not Found
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/main/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/restricted/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/main/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/universe/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/universe/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/multiverse/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid/multiverse/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/main/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/main/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/universe/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-updates/multiverse/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/main/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/main/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-security/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/universe/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/universe/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://ubuntu.utalca.cl/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.utalca.cl/dists/intrepid-security/multiverse/source/Sources.gz](http://ubuntu.utalca.cl/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
ren@ren-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
ren@ren-laptop:~$ cat /etc/issue
Ubuntu 8.10 \n \l

This is what I got. So what next?

---

### Post by connorh123 on 2009-05-08
Here try
```
alt f2
```
Then type
```
update-manager -d
```
Then upgrade :)

---

### Post by Sef on 2009-05-08
> Here try
 	Code:
 	alt f2 
Then type
 	Code:
 	update-manager -d 
Then upgrade :smile:

That is not the first thing to do.  


> deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

The problem lies with the top line being uncommented.   To comment it out, put a # before deb.   Thus is should look like this:

> #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 # newer versions of the distribution.

---

### Post by loweehahn on 2009-05-08
By the way this is another problem after I restarted my laptop as a result of it froze during the installation I mentioned earlier.

---

### Post by loweehahn on 2009-05-08
I tried with alt f2 and update-manager  -d but this is what I got.

ren@ren-laptop:~$ alt f2
bash: alt: command not found
ren@ren-laptop:~$ update-manager -d
ren@ren-laptop:~$

---

### Post by connorh123 on 2009-05-08
No don't type it into terminal just press those keys on your desktop.

---

### Post by loweehahn on 2009-05-08
I pressed alt and f2 on my keyboard but no response.

---

### Post by connorh123 on 2009-05-08
Press them at the same time together.

---

