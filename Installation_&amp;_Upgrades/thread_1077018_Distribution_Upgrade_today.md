---
title: "Distribution Upgrade today?"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by ricardisimo on 2009-02-21
Why is Update Manager trying to run a Distribution Upgrade - albeit only a "partial" one? I'm already on 8.10 and it's only February. The only "extra" repositories I've added are Medibuntu.

I have recently removed both PulseAudio (replaced with esound) and OpenOffice 2.4 (replaced with version 3.0), and as I recall, one or the other of these also removed ubuntu-desktop. Is my ubuntu trying to restore how it was before this got removed?

I've attached a snapshot of the upgrade window. Thanks for any help.

---

### Post by ricardisimo on 2009-02-22
OK, so why it's trying to run a distribution upgrade, I have not a clue. The root of the problem appears to be some recent big changes to KDE4, at least so far as I can tell. On both comps, the major updates are all KDE, and the one that is giving me the most grief is Kmail, which installed along with Kontact... I never use it, mind you.

During the update, one of the new components that Kmail needs - mysql-server-5.0 - keeps asking for a "new root user password". What the hell is that? I doubt that it's anything malicious, but I guess I don't understand why anything installed via Update Manager - which obviously requires a password - would also require a password to install. What is going on, and should I go ahead and enter my password for this? Thanks.

---

### Post by Kareeser on 2009-02-22
Doesn't seem like it needs a password to **install**, but rather, a password because it is installing a new version.

Careful what you put in there :)

---

### Post by ricardisimo on 2009-02-22
It's a brand new app that it's installing. I'm assuming that all of KDE4 has been somehow reorganized, and has new dependencies. But why does mysql-server-5.0 need a separate password to install?

My sources.list looks quite bland, don't you think?
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
# deb-src http://packages.medibuntu.org/ intrepid free non-free
```

I'm tempted to just give it my password, but what's with this "new root password" business?

---

### Post by ricardisimo on 2009-02-22
Sorry to be annoying about this, but could anyone tell me if mysql-server-5.0 is safe to install, and why it is asking for a "New password for the MySQL 'root' user"? See attached screenshot.

---

### Post by ricardisimo on 2009-02-23
Evidently, it is safe and sound. I'm marking this as resolved. Thanks.

---

### Post by ricardisimo on 2009-02-23
... or not. I'm assuming that "solved" and "thank you" have been removed for technical reasons? Or is it just that my brain can't find them on the screen right now?

---

### Post by ricardisimo on 2009-02-25
Something's not right. There have been several KDE updates these past few weeks (I'm assuming they are instituting some rather big changes there) and every round of updates causes Update Manager to suggest a Distribution Upgrade. Obviously, I'm not going to upgrade past 8.10 just yet.

Furthermore, all of these KDE updates are listed in the "Backports" category, and Synaptic warns that I am about to install stuff "that cannot be authenticated!" Since when can KDE packages not be authenticated. Are my keys wrong? How do I fix them if they are? Is no one else having this issue? Thanks.

---

### Post by grissu.org on 2009-02-27
> **ricardisimo said:**
> Sorry to be annoying about this, but could anyone tell me if mysql-server-5.0 is safe to install, and why it is asking for a "New password for the MySQL 'root' user"? 

The mysql database server requires you to set a password for its **own** root user since mysql has a user management of its own for its databases. 

You can set any password you like for this account, it has nothing to do with a "normal" user. It's just for the internal mysql user management. Make sure you remember the password if you want to access/change your mysql database.

---

