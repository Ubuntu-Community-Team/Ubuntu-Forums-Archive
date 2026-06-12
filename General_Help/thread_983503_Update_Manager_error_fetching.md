---
title: "Update Manager error fetching"
date: 2008-11-15
forum: General Help
---

### Post by C-free on 2008-11-15
Hi All,

Enjoying Ubuntu immensely. Been reading forum for a while, first post, unfortunately with some issues which wasn't able to resolve on my own.

Last succsessful update was 14 days back, since then getting this:

**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

ailed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/maindeb/binary-amd64/Packages.gz](http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/maindeb/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/http://ppa.launchpad.net/compiz/ubuntu/binary-amd64/Packages.gz](http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/http://ppa.launchpad.net/compiz/ubuntu/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/intrepid/binary-amd64/Packages.gz](http://ppa.launchpad.net/compiz/ubuntu/dists/intrepid/intrepid/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/main/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/universe/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/main/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/restricted/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/universe/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/main/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/restricted/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/universe/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/multiverse/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/restricted/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/main/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/multiverse/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/universe/binary-amd64/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/intrepid-proposed/universe/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

**cfree@cfree-ubuntu:~$ cat /etc/apt/sources.list**

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid main restricted
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates main restricted
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid universe
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid universe
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates universe
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid multiverse
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid multiverse
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates multiverse
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security main restricted
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security main restricted
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security universe
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security universe
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security multiverse
deb-src [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-security multiverse
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-backports restricted main multiverse universe
deb [http://ftp.netspace.net.au/pub/ubuntu/](http://ftp.netspace.net.au/pub/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid maindeb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main

Tried playing with Software Sources(chaged servers from Main Server to Select Best Server), Synaptic (reinstalling some of the packages, which seemed to fix an issue at one point) and sudo apt-get update

Any help will be greatly appreciated.

Thank you

---

### Post by |Porsche on 2008-11-15
It seems like those resources have been moved. They are not there anymore. Whoever maintains those repositories has moved them. You can contact them and see where they moved them too, or you can switch to repositories that are still standing. I hope it helps. Let me know if you have more questions.

This is what I am getting when clicking on one of those repositories
[HTML]
Object not found!

The requested URL was not found on this server. The link on the referring page seems to be wrong or outdated. Please inform the author of that page about the error.

If you think this is a server error, please contact the webmaster.
Error 404
ftp.netspace.net.au
Sun Nov 16 11:25:26 2008
Apache/2.2.6 (Unix) PHP/4.4.7[/HTML]

---

### Post by C-free on 2008-11-15
Thank you! Removed all Third-party software sources from the list, changed server to Main and got a Successful update.

---

### Post by dcstar on 2008-11-15
> **|Porsche said:**
> It seems like those resources have been moved. They are not there anymore.
.......

Not necessarily. When updates are made available, the repository owner is *supposed* to fetch them in a manner that ensure that the packages are actually on their server before they advertise them in the new package list file - this does not always happen. Wait a day or two for the repository to actually "catch up" and get all the updated files and you will probably find that all the errors go away.

People who experience this problem should contact the repository owner and ask them to follow the specific instructions on how to update correctly (which are provided by Ubuntu on their repository site) if you like, it may help in future.

---

### Post by dcstar on 2008-11-15
> **C-free said:**
> Thank you! Removed all Third-party software sources from the list, changed server to Main and got a Successful update.

This could be a mistake, most ISPs allow downloads from their mirror repositories for free, getting them from the main server is usually much slower and also can cost you part of your data quota.

If you are going to change servers from your own ISP, use the "Find Best Server" option in Synaptic.

---

