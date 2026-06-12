---
title: "source.list permissions got changed."
date: 2008-10-14
forum: General Help
---

### Post by AerosolSP on 2008-10-14
As the title says, the source.list permissions got changed to read only, and I can't switch them back due to not being the owner (which is preposterous, for I **am** the owner!). I can't install any apps at all, cause Synaptic Package Manager gives me this:
```

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

and Add/Remove gives me this:
```

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

The contents of my source.list file is as follows:

```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info harty all

deb http://repoubuntusoftware.info harty all

deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.canonical.com/ubuntu hardy partner
#ULTAMATIX REPOS END
```

Any help would be appreciated. Alot.

---

### Post by Yellow Pasque on 2008-10-14
The file should be read-only for your user, as it should be owned by root. Edit it with:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by AerosolSP on 2008-10-14
well the reason i keep thinking that the permissions got changed is because I never had this problem before. I opened up Add/Remove to look for anjuta, and it hit with that error. I also cant tell if my source.list is...correct. I can barely read the thing.

EDIT: I'm asking the wrong question. I'll post a new topic. Feel free to let this topic sink into oblivion!

---

### Post by oldos2er on 2008-10-14
Remove the ULTAMATIX entries.

---

### Post by aysiu on 2008-10-14
I don't see anything in the error messages indicating that the /etc/apt/sources.list file is misconfigured.

There seems to be some kind of broken package or not-properly-installed dependency.

What happens when you run ```
sudo apt-get -f install
``` ?

---

### Post by drs305 on 2008-10-14
The problem is with the sources.list entry:
```
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_***harty***_all_binary-i386_Packages

```

Open sources.list and change it to ***hardy*** wherever it's mentioned and your problem will be solved unless the problem has been compounded. It's in the Ultamatix section.

```

gksudo gedit /etc/apt/sources.list

```

---

### Post by aysiu on 2008-10-14
Oops. You're right. I misread the error. The Ultamatix entries are indeed the culprit and should be removed.

---

