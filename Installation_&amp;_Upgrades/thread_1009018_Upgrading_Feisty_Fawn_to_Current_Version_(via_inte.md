---
title: "Upgrading Feisty Fawn to Current Version (via interim steps)"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by nycgadgetgeek on 2008-12-12
I am trying to update my computer to the current version of Ubuntu.  I am starting with version 7.04 so I realize that I need to upgrade to 7.10 before  I do the jump to 8.10.  

However, I have uncovered quite a bit of trouble with my upgrade.  When using  System >> Administration >> Update Manager I get the following error message: 


Failed to fetch [http://medibuntu.org/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.org/repo/dists/feisty/free/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://medibuntu.org/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.org/repo/dists/feisty/non-free/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://medibuntu.org/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.org/repo/dists/feisty/free/source/Sources.gz) 403 Forbidden
Failed to fetch [http://medibuntu.org/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.org/repo/dists/feisty/non-free/source/Sources.gz) 403 Forbidden
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]

This seems to be related in part to problems with medibuntu which has dropped the feisty fawn software sources.  I have tried to update my machine with these addresses as well as the original address in which the medibuntu sources ended in sos-sts.com.  Neither version has worked.  

I've also tried to update the machine using the Alternate CD method.  This has also failed to work.  The CD does not automatically mount.  I manually launch the upgrade process by pressing ALT-F2 and then running the following command: gksu "sh /media/Ubuntu 7.04 i386/cdromupgrade" to no avail.  On another note entering /media/cdrom doesn't work since it is set to device /dev/scd0 although I have an ide drive on the machine.  Regardless, the upgrade process never adjusts.  

Any direction you could provide on this issue is greatly appreciated.  

Thanks-in-advance

---

### Post by Gausian on 2008-12-12
its a pretty big jump from 7.04 to 8.10

you may be better off backing up your home directory and installing anew 

then simply insert your home backup into the new distro.

---

### Post by Pumalite on 2008-12-12
To attemp an upgrade; one should fully update the present OS and remove al third parties from /etc/apt/sources.list, including Medibuntu and it's Folder first.

---

### Post by zvacet on 2008-12-12
I is possible but in same time time consuming proces with chanses to something get wrong.But if you want to try hrere it is.First of all do what **Gausian** adiced.Even better make separate home partition(if you don't have one) following [this]("http://www.psychocats.net/ubuntu/separatehome") guide.When you are done with that read [this]("https://help.ubuntu.com/community/GutsyUpgrades") to upgrade to Gutsy.Make your Gutsy up to date and upgrade to Hardy following [this.]("https://help.ubuntu.com/community/HardyUpgrades") You will find Intrepid upgrades [here.]("https://help.ubuntu.com/community/IntrepidUpgrades")
 
It is easier to download CD of latest version and install it on tpo of old one.

---

