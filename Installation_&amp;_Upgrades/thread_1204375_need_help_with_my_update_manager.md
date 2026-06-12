---
title: "need help with my update manager"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by charlie090790 on 2009-07-04
hi, im pretty new to ubuntu, but do know the basics.my update manager has always worked until i ran computer janitor and it told me that i can delete some stuff that was needed for an update but is no longer needed anymore, so i did. Since then when ever i try updating i get this message: 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAFailed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/deb-src/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/deb-src/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by wojox on 2009-07-04
Can you post the contents of your /etc/apt/sources.list file?

---

### Post by raymondh on 2009-07-04
> **charlie090790 said:**
> hi, im pretty new to ubuntu, but do know the basics.my update manager has always worked until i ran computer janitor and it told me that i can delete some stuff that was needed for an update but is no longer needed anymore, so i did. Since then when ever i try updating i get this message: 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAFailed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/deb-src/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/deb-src/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


Hello,

Let's get the pubkey first and see what happens.  Access a terminal and type or copy/paste one at a time .... (I will do the first pubkey, and you do the other).  Make sure you only have the terminal open.  Close synaptic or add/remove or update manager if open.

```
gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783GPG
gpg --export --armor 2EBC26B60C5A2783GPG | sudo apt-key add -
sudo apt-get update
```

This first command looks and sorts out the specific pubkey ... the second secures and adds it.

Now, you have do the second pubkey  ..... 7889D725DA6DEEAA ... same format

After, do your usual (one more time)

```
sudo apt-get update
sudo apt-get upgrade
```

Then, let's see if there are any more errors.

---

### Post by raymondh on 2009-07-04
This is what error 404 means ... for your reference

[http://en.wikipedia.org/wiki/HTTP_404](http://en.wikipedia.org/wiki/HTTP_404)

Also, when you post back if you still have errors, kindly post your /etc/apt/sources.list as well.

---

### Post by charlie090790 on 2009-07-04
> **wojox said:**
> Can you post the contents of your /etc/apt/sources.list file?

this is my source list:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main

---

### Post by charlie090790 on 2009-07-04
> **raymondhenson said:**
> Hello,

Let's get the pubkey first and see what happens.  Access a terminal and type or copy/paste one at a time .... (I will do the first pubkey, and you do the other).  Make sure you only have the terminal open.  Close synaptic or add/remove or update manager if open.

```
gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783GPG
gpg --export --armor 2EBC26B60C5A2783GPG | sudo apt-key add -
sudo apt-get update
```This first command looks and sorts out the specific pubkey ... the second secures and adds it.

Now, you have do the second pubkey  ..... 7889D725DA6DEEAA ... same format

After, do your usual (one more time)

```
sudo apt-get update
sudo apt-get upgrade
```Then, let's see if there are any more errors.


charlie@Optinus-Prime:~$ gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783GPG
gpg: "2EBC26B60C5A2783GPG" not a key ID: skipping
charlie@Optinus-Prime:~$ gpg --export --armor 2EBC26B60C5A2783GPG | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
charlie@Optinus-Prime:~$

---

