---
title: "sudden problem"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by apoudis on 2009-09-28
I am new to ubuntu. I have installed ubuntu 9.04 at my laptop for 2 months and I was pretty happy.  Suddenly an error message popped up:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages (/var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages (/var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_restricted_binary-i386_Packages)

Can anyone help????

---

### Post by ajgreeny on 2009-09-28
It sounds as if you have the ubuntu CD as one of the sources in your sources.list file.  So go to **System ->Administration ->Software Sources** and have a look there.  If the CD is checked in the first tab uncheck it, click OK and reload the sources, which you will be prompted to do.  That may sort the problem.  If not come back again.

---

### Post by apoudis on 2009-09-29
thanks for the quick reply. Your advice partially solved the problem. I still have this error message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by earthpigg on 2009-09-29
post output of this, please:

```
cat /etc/apt/sources.list
```

---

### Post by apoudis on 2009-09-29
ok the output is:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe

---

### Post by earthpigg on 2009-09-29
back that file up, then try replacing all that text in that file with this:

```
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse 
```

then run:

```
sudo apt-get update
```

i got that text from here, if you are wondering: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by apoudis on 2009-09-29
please be a little more specific, since i am a novice. How to back up and replace????

---

### Post by earthpigg on 2009-09-29
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.hi-apoudis-i-like-beer
```

will exactly copy sources.list to a new file called sources.list.hi-apoudis-i-like-beer.... so ***if*** the chances to sources.list don't work, you can do this to undo them:

```
sudo cp /etc/apt/sources.list.hi-apoudis-i-like-beer /etc/apt/sources.list
```

see how that worked? we just reversed the two.

once it is backed up, to edit/modify the origional:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by apoudis on 2009-09-29
thank you very much. worked perfectly. Much appreciated...

---

### Post by apoudis on 2009-10-09
Well it worked for a week, but now the problem is persisting. I get this error message again when I try to update:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Any suggestions??

---

