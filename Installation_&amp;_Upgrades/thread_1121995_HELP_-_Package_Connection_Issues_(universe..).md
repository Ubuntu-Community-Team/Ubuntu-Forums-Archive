---
title: "HELP - Package Connection Issues (universe..)"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by gbxfan on 2009-04-10
I am running Ubuntu 8.10 client and have internet access, but for some reason I can not update my sources to get packages from universe, multiuniverse, canonical or regular updates for security for the OS (the boxes are checked so it looking for them). The error I get is:

Failed To Fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/packages.gz) 404 Not Found [ip:135.179.17.79 8081]

I get this 25 times when it attempts to reload sources - looks like mainly 135.179.17.xx. I have tried other servers and this doesn't work either so I probably have a network issue, but not sure what. I am running DHCP and the internet WORKS fine so I am able to get out. When I try to ping one of the 135.179.17.79 hosts they don't answer so it makes sense to a point. What am I missing - is there a service I need to start? Anyone else have these issues? THANKS!!!

Here is my sourcelist - I removed the '/' between ubuntu and intrepid from other post I saw, but I don't think that helped.
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by rodtrekker on 2009-04-10
I am using Ubuntu 8.04 (Hardy Heron) and am having a similar problem.  I seem to get some updates to misc. programs; but, I keep getting a message that I'm having a connection/network problem and can't access the repositories.  I tried using Software Sources to find the best source, which it did; but, then I get the same error message when trying to update!  (Actually, while typing this post, I think I figured my problem out--See below--Remove out-dated third party sources)

Here is the error message:

"[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/I]"

and:

"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead."

Well, looking at this closer now, I guess I need to remove the Feisty entries since it's not supported any more.  Doh!

I think that got it.  I've removed all the old entries from the Third party sources and didn't the error message this time.  Yeah, that got it.  I was getting a status that my update info was 41 days old, now it says it's just an hour old.

Maybe you've got something similar going on.  If not, maybe other nubes like me are having the same problem I did.

:)

Rodman

---

