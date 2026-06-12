---
title: "Errors when upgrading : Malformed Release FIle?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by clancymf on 2009-08-16
Trying to upgrade from Ibex and I receive the following errors:
```
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  Unable to find expected entry  deb/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any ideas how to fix?

Thanks in advance for all the help!!!
Cheers,
Mick

---

### Post by Partyboi2 on 2009-08-16
Hi, can you post your sources.list please
```
cat /etc/apt/sources.list
```> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680For these you need to add the key, you can do this by typing or pasting

```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor  2EBC26B60C5A2783 | sudo apt-key add -
``````
gpg --keyserver keyserver.ubuntu.com --recv 43C0AFF0D7FAE680
gpg --export --armor 43C0AFF0D7FAE680  | sudo apt-key add -
```then```
 sudo apt-get update
```

---

### Post by clancymf on 2009-08-16
```
clancymf@htpc:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-backports restricted main multiverse universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-backports restricted main multiverse universe #Added by software-properties

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates restricted main multiverse universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted deb main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security restricted deb main multiverse universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu/ intrepid-security main
deb http://apt.boxee.tv intrepid main

```

Again thanks so so much for the help

---

### Post by clancymf on 2009-08-16
Figured it out.  I had an extra "deb" in the sources list down at the line that was broken.  Thanks for your help!

---

