---
title: "[SOLVED] &amp;quot;Could not download all repository indexes&amp;quot;  when updating ubuntu 7.04"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by sadafrasheed on 2009-01-03
Hello,,

i have hp dv6000. my system is connected to internet all the time. i have just installed ubuntu 7.04 when i try to update my system to ubuntu 7.10 i get Failed status for many files that system is trying to download and then a window pops up saying 



The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]


i get this no matter which server i choose as software source..

here is my source.list



# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse


i have checked the links using firefox and [http://archive.ubuntu.com/ubuntu/dists/feisty/](http://archive.ubuntu.com/ubuntu/dists/feisty/) does not exist.. 

what should i do :confused:

---

### Post by gettinoriginal on 2009-01-03
7.04 is no longer supported, the latest LTS is 8.04 :P

---

### Post by sadafrasheed on 2009-01-03
thanks for the quick reply :)

so how do i upgrade it :s

i have googled a bit and found few servers that have these files.. i manually modified my source.list to specify these servers but then i was getting error for some other files :s

i have downloaded these four packages that the update manager cant find.. how do i install them???

---

### Post by Elfy on 2009-01-03
If you have just installed then I would be tempted to just get a 8.04 iso and reinstall, Gutsy will be out of support in April and you will need to update again. 

There was no direct upgrade path from Feisty to Hardy.

Hardy will be supported until 2011 at which point there will be another LTS to direct upgrade to.

---

### Post by sadafrasheed on 2009-01-03
my problem is that my cd writer is not working.. so i cannot write any cds..
i am downloading alternate cd and will follow this article

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

hope every thing works well.. 

Advices for installing ubuntu this way on dv6000 are more than welcome :)

---

