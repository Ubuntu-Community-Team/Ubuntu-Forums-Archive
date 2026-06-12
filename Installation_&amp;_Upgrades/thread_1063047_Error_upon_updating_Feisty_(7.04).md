---
title: "Error upon updating Feisty (7.04)"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Eax.exe on 2009-02-07
Hi :)

I just re-formatted my laptop due to some problems (not important).
I installed Feisty (because I know that my wireless/wired internet works in feisty) and through that I would upgrade to 7,10 Gutsy, (Upgrading beyond that point breaks my wired internet).

However, after the first updates (and a reboot) I now get this error when I try to update:

```
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 404 Not Found
http://dk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: 404 Not Found

```

What can I do about this? 

Thanks in advance :)

---

### Post by avtolle on 2009-02-07
Feisty reached EOL in October; the repositories were taken down, and moved. I don't have the link, but go to [www.ubuntu.com](www.ubuntu.com), check the upgrade selection, follow the links, and eventually you will get to a web page discussing upgrading from 7.04 to 7.10; there, you will find the URLs to which to edit the /etc/apt/sources.list file to use. Good luck.

---

### Post by Eax.exe on 2009-02-07
> **avtolle said:**
> Feisty reached EOL in October; the repositories were taken down, and moved. I don't have the link, but go to [www.ubuntu.com](www.ubuntu.com), check the upgrade selection, follow the links, and eventually you will get to a web page discussing upgrading from 7.04 to 7.10; there, you will find the URLs to which to edit the /etc/apt/sources.list file to use. Good luck.

Thank you very much :)

---

### Post by Eax.exe on 2009-02-07
Upon trying to upgrade according to:
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

It get these errors:
```
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz 404 Not Found

```

Even though I have added:
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 
```
to /etc/apt/sources.list 

So now my sources.list file looks like this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://dk.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 
```

Any ideas?

---

### Post by avtolle on 2009-02-07
Take  a look at [http://ubuntuforums.org/showthread.php?t=1063043](http://ubuntuforums.org/showthread.php?t=1063043) where the OP had a similar problem.

---

