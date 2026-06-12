---
title: "apt problem! possible cause: unmet dependencies"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by rat_poison on 2009-08-21
Hello, I'm using ubuntu 9.04 on asus eee pc 1000 with the latest array kernel. 
I can't update packages and can't use apt-get, synaptic, update-manager, etc effectively.

a sudo apt-get update causes this:
```
ratpoison@bistromath:~$ sudo apt-get check
[sudo] password for ratpoison: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

my sources.list looks like this:
```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by Partyboi2 on 2009-08-21
Hi, open a terminal and move the file out of the way and download it again
```
sudo mv /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages /home/$USER
sudo apt-get update
```

---

### Post by starcraft.man on 2009-08-21
Ack, I've run across this problem before. The package file listed in the error is corrupted. Deletion of the file, will cause apt to get a new version and fix this. In a terminal type the following to delete it (preferably copy paste) or delete it manually by gksudo nautilus and navigate there.

```
sudo rm /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
```

Then 
```
sudo apt-get update
```

If ya use rm, ensure no typos...

Edit: Rah, beaten to post, got bogged down by IRC folks.

---

### Post by rat_poison on 2009-08-22
Thank you everyone! Most helpful advice!

---

