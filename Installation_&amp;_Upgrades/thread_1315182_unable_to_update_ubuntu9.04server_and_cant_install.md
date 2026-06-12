---
title: "unable to update ubuntu9.04server and cant install another server on software sources"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by mady03sam on 2009-11-05
hi,
   buddies can any1 give reply for this im unable to resolve this issue .............. unable to upgrade ma ubuntu server and even i cant change ma server on software sources...........im gettin result as '**Failed to Fetch**' 
# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 693kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tzdata
Authentication warning overridden.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main tzdata 2009o+repack-0ubuntu0.9.04.2
  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009o+repack-0ubuntu0.9.04.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009o+repack-0ubuntu0.9.04.2_all.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

and i tried for fixing this with command

 # apt-get update --fix-missing

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  Connection failed
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mady03sam on 2009-11-06
hey i resolved this issue anybody have faced d same issue then try this goto sourcelist and edit every **http**'s into **ftp**'s
# gedit /etc/apt/source.list
 
then edit every http to ftp it should be like this:

# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty restricted main universe #Added by software-properties

# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main universe #Added by software-properties

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
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) jaunty-security restricted main universe #Added by software-properties





After changing like this u can update ur ubuntu with command 

# apt-get install update

---

