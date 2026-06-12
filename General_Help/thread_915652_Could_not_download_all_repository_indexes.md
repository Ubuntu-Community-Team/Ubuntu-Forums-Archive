---
title: "Could not download all repository indexes"
date: 2008-09-10
forum: General Help
---

### Post by blazerqb11 on 2008-09-10
I keep getting this error when I try to check for new updates and am having all kinds of problems in Synaptic.  I was getting the error and so I tried replacing the source.lst file however,I did it a little too hastily and I accidentally replaced it with one for gutsy gibson and I have hardy heron.  Is there anyway that can revert to the original or fix this in some other way?

Also I was trying to build qt4(It won't install from synaptic), so that I can build another program that needs qmake and it got stuck in a loop and ran for about an hour.  Can anyone help me with that?

---

### Post by mb_webguy on 2008-09-10
Here's the standard sources.list file for Hardy.```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

---

### Post by blazerqb11 on 2008-09-10
I can't thank you enough, I will see if that works.  Did you just pull that out of your source.lst file or is it do they store it somewhere online i.e. where do they keep these things?

---

### Post by blazerqb11 on 2008-09-12
I replaced source.lst with the repositories above but am still getting the error when attempting to update, however it seems my problems with synaptic are solved.  Here it is in full.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz)  500 Internal Server Error
Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/source/Sources.gz](http://repository.akirad.net/dists/akirad-hardy/main/source/Sources.gz)  500 Internal Server Error
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cariboo on 2008-09-12
The medibuntu repositories have been up and down lately give it a while and it should be back up again.

JIm

---

### Post by blazerqb11 on 2008-09-12
> **cariboo907 said:**
> The medibuntu repositories have been up and down lately give it a while and it should be back up again.

JIm

As long as its not a problem on my end everything is cool, thanks for the info.

---

