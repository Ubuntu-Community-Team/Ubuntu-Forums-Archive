---
title: "Update Manager not updating date"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by Foxfan100 on 2009-10-08
I'm using Ubuntu 9.04.

Suddenly (as in it was OK but now isn't - for no apparent reason) the Update Manager fails to reflect recent updates i.e.it says "Your system was last updated 47 days ago"!

This appears even after today, when I have just updated Open office etc etc etc.

How do I reset/solve this, as it's really annoying not being able to see the true update picture?

---

### Post by zvacet on 2009-10-09
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Foxfan100 on 2009-10-10
Thanks. I gave that a try but no change.

I think the problem is this. In Update Manager I get a message saying "Could not download all repository indexes". There then follows a list of 404 errors, but relating to Gutsy security and updates (see below)

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

In Update manager I have these settings:
Ubuntu tab - all checked xcept source code, and set to download from UK server
Third Party tab - recommended and important security
Updates - Important Security (Jaunty Security)

Every day I do this, I'm told my system is up to date but the package information was last updated by yet another day - I'm up to day 49 now!

---

### Post by MelDJ on 2009-10-10
try changing your software server in software sources

---

### Post by Foxfan100 on 2009-10-11
I've tried servers all over the world I presume that it must be something inherent in my Ubuntu system. I have a dual boot system with XP, using GRUB to start up. That reports my versions as being 9.04 with kernels 14 and 15, so I don't think I have another old Ubuntu version on here.

I'm now up to day 50!

---

### Post by spcwingo on 2009-10-11
There may be something wrong to your sources.list.  Please post the output of this command so we can give it a good once-over:

```
cat /etc/apt/sources.list
```

---

### Post by slakkie on 2009-10-11
You are running Gutsy, which has become EOL a while ago and they (the ubuntu maintainers) moved the repo's to another archive. I advise you to upgrade.

Read this document carefully: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Then proceed to: [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

If you wish to continue Gutsy for whatever reason, use the sources.list as described in the last document. Then you should be able to update your system. But remember, it is not supported anymore by both community and Canonical.

If you are indeed running 9.04 (check with lsb_release -a) then your sources.list is incorrect. 
Have a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You can find my sources.list below.

```

# Uncomment deb-src if you really need them                                                            
## Keepers
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

## Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

## Optional, remove if you don't like them
deb http://archive.canonical.com/ubuntu jaunty partner
#deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ jaunty free non-free
#deb-src http://packages.medibuntu.org/ jaunty free non-free

```

---

### Post by Foxfan100 on 2009-10-12
Thanks both for your answers.

Point 1. I've run lab_release -a and it definitely is 9.04 Jaunty. Output message is:
No LSB modules
Distributor id: Ubuntu
Description: Ubuntu 9.04
Release: 9.04
Codename: Jaunty


My sources.list doesn't bear much resemblance to slakkie's. My Ubuntu networking connection has gone down (a frequent and unresolved problem-see my other posts) and I'm responding via Firefox under XP, so pasting the output is a tad difficult.

However - there are a couple of lines in it (uncommented) which refer to gutsy. The first thing to do I guess is to comment them out.

The jaunty deb lines end thus:-
jaunty main
jaunty-security main
 " -updates main
 " -proposed main

i.e no restricted universe and so forth

I'll have a look at the Repositories help link you posted, and as soon as I can get connected in Ubuntu I'll post the full text of my sources.list.

** to be continued **

---

### Post by Foxfan100 on 2009-10-12
Here is my sources.list, which looks a bit of a mess.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main # disabled on upgrade to jaunty


I think the best thing is to set it up from scratch again.

---

### Post by Foxfan100 on 2009-10-12
Right. I backed up and then deleted /etc/apt/sources.list, then reran the Update Manager. This was a "blank sheet" as regards options, so i set them up again.

After this, I reran updates and the time message is now correct. The recreated sources.list file has also shrunk to a few lines.

I still can't quite see how sources.list got into that state!

---

### Post by Partyboi2 on 2009-10-12
> After this, I reran updates and the time message is now correct. The recreated sources.list file has also shrunk to a few lines.
If you sources.list is only a few lines make sure you have all the correct repositories enabled. One way to do this is to open Software Sources and make sure on the first tab all the boxes above source code are enabled. and under the "Updates" tab that the first 2 are enabled.

---

### Post by Foxfan100 on 2009-10-13
I'll certainly check those points.

Thanks to all respondents on this topic, as I wouldn't have got anywhere near solving it in a hundred years without your help.

Cheers,
Peter

---

