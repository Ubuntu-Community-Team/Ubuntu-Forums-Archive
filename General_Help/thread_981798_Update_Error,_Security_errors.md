---
title: "Update Error, Security errors"
date: 2008-11-14
forum: General Help
---

### Post by volaer on 2008-11-14
This is the last error that I used to get now every time I update my Ubuntu:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

This also causes my 8.10 upgrade to fail. Please help. Thanks!!!

---

### Post by mikewhatever on 2008-11-14
It looks like you have Intrepid's repositories mixed with those of Hardy Heron. Can you post the output of <cat /etc/apt/sources.list>.

---

### Post by volaer on 2008-11-14
> **mikewhatever said:**
> It looks like you have Intrepid's repositories mixed with those of Hardy Heron. Can you post the output of <cat /etc/apt/sources.list>.


Here's the output:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse

deb [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free
deb-src [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free


Please help me... Thanks!!!

---

### Post by mikewhatever on 2008-11-14
Hey, looks like I got it wrong, the repository list looks fine. Did you try running <sudo apt-get update>?

---

