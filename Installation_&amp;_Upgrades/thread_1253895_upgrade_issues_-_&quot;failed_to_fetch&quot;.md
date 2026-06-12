---
title: "upgrade issues - &quot;failed to fetch&quot;"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by calvimm on 2009-08-30
hi.
when i turn on my laptop, the upgrade window pops open and nags me to upgrade. so i follow suit but always get this error message in the Software Sources menu:

Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead.

what do i do?

---

### Post by running_rabbit07 on 2009-08-30
It is because you recently installed something from the [bisigi]("https://launchpad.net/zgegball-themes") website and it was added to update sources but didn't get a key.

If you want the Update Manager to stop bugging you, then go to System>Administration>Software Sources and uncheck and/or remove the above mentioned repository from the list.

---

### Post by Partyboi2 on 2009-08-30
Hi, looks like you may have an incorrect entry in your sources.list, can you open a terminal and post your sources.list 
```
cat /etc/apt/sources.list
```

---

### Post by calvimm on 2009-08-31
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by Partyboi2 on 2009-09-01
Looks like you need to fix the last line of your sources.list, it should be
```
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
```not
 ```
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
``````
gksu gedit /etc/apt/sources.list
```Once you have finished making the changes back in the terminal run
```
sudo apt-get update
```
Edit: If you are still wanting to use that repo you can remove the # from in front of the line
so it would be
```
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
```
Any changes you make to your sources.list you will need to run
sudo apt-get update afterwards.

---

### Post by calvimm on 2009-09-01
Awesome!

It worked. Thank you very much!

---

