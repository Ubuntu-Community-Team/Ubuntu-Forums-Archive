---
title: "Updating Error"
date: 2008-07-27
forum: General Help
---

### Post by snkngshps on 2008-07-27
When I try to perform an update I'm getting this error:

"Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead."

Does anyone know how I can fix this?

---

### Post by snkngshps on 2008-07-28
anyone?

---

### Post by dark_phantom on 2008-07-28
What version of Ubuntu do you currently have?  Post your /etc/apt/sources.list.

---

### Post by snkngshps on 2008-07-28
> **dark_phantom said:**
> What version of Ubuntu do you currently have?  Post your /etc/apt/sources.list.

I'm running hardy 8.04

"## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe"


I think the problem happened when my laptop battery died mid-update but I don't know how to clear it up.

---

### Post by dark_phantom on 2008-07-28
> **snkngshps said:**
> 
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main


comment this line, save and retry

---

### Post by snkngshps on 2008-07-28
That stops checking for that update but it doesn't actually fix whatever wasn't updating. I'm not even sure what that source updates.. is it going to be anything I might need down the road? If it's nothing I need I'll leave it commented out but if I need it, I'd like to fix the update.

---

### Post by dark_phantom on 2008-07-29
I don't think you need that package that it downloads, besides it's for feisty which is an old version.  If you need it by any odd reason then you can just uncomment it.  You can manually download the packages zip and see what it is about.  It seems to be emulators for playstation and supernes.

---

