---
title: "Upgrade from gutsy to hardy"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by tblom on 2009-07-06
Hello,

I am trying to upgrade from gutsy to hardy. I think the fact that gutsy is no longer supported is causing me some problems.

When trying to upgrade, I get the following message:
> 
"No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'gutsy' to 'hardy' entries.
If you select 'no' the update will cancel."

If I click Yes, I get the following errors:

> Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://old-releases.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz) 404 Not Found 


BEFORE trying to upgrade, my sources.list file looked like this:
(I changed "archive.ubuntu.com" to "old-releases.ubuntu.com" a while ago because I could no longer install software from synaptic)
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://old-releases.canonical.com/ubuntu](http://old-releases.canonical.com/ubuntu) gutsy partner
# deb-src [http://old-releases.canonical.com/ubuntu](http://old-releases.canonical.com/ubuntu) gutsy partner

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free 

What should I do? I don't have much experience in Ubuntu installations so I would really appreciate an explanation in small steps.

Thank you in advance!!

---

### Post by Sef on 2009-07-06
> What should I do? I don't have much experience in Ubuntu installations so I would really appreciate an explanation in small steps.

There's a way to [upgrade]("https://help.ubuntu.com/community/HardyUpgrades") by using the alternate cd.  Otherwise you have to do a clean install.

---

### Post by snowpine on 2009-07-06
Change all of the "old-releases.ubuntu.com" back to "archive.ubuntu.com" and you should be OK.

---

