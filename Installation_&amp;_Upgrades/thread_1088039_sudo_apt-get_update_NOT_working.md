---
title: "sudo apt-get update NOT working"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by jordanguyoflove on 2009-03-05
Hi

I am trying to build a new kernel by following some instructions.

One of them is: "sudo apt-get update",  to install all needed packages 

But I can't get the updates I get these error:
> 
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  404 Not Found

> 
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
> 
E: Some index files failed to download, they have been ignored, or old ones used instead.


That's all of it:

add@add-desktop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty Release.gpg
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/main Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/restricted Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/main Sources
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/restricted Sources
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  404 Not Found
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/universe Sources
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  404 Not Found
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://lb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
adam@adam-desktop:~$ make-kpkg clean
The program 'make-kpkg' is currently not installed.  You can install it by typing:
sudo apt-get install kernel-package
bash: make-kpkg: command not found


Help please! WHat should I do?

---

### Post by R33D3M33R on 2009-03-05
It seems you need to edit your sources.list file: try to reset it: [http://ubuntuforums.org/showthread.php?t=773137](http://ubuntuforums.org/showthread.php?t=773137)

---

### Post by jordanguyoflove on 2009-03-05
I typed: sudo gedit /etc/apt/sources.list

Then copy pasted the list in the thread you referenced, but I get the same stuff when I type: sudo apt-get update

---

### Post by avtolle on 2009-03-05
The Feisty repos have been taken down and moved due to its reaching EOL in October, 2008, and the packages moved to the old-release port. I don't have the link handy, but if you will look at the upgrade part at [www.ubuntu.com](www.ubuntu.com), and find the link to upgrading from older releases, you will eventually get the correct places to point your file to.

---

### Post by zvacet on 2009-03-05
[Here]("https://help.ubuntu.com/community/GutsyUpgrades") you will find explanation how to upgrade from Feisty to Gutsy.

---

### Post by jordanguyoflove on 2009-03-05
sudo gedit /etc/apt/sources.list



> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


sudo apt-get update

Thanks to [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1077898](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1077898)

Thanks guys. :D

---

