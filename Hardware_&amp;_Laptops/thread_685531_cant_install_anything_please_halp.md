---
title: "cant install anything please halp"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by zuknivek on 2008-02-02
I cant install anything with my laptop. I used to be able to now when i try and install anything it says that i need to go into synaptic manager because there is a program that would interfere with this program, or something is wrong with your hardware. Please help.

---

### Post by taurus on 2008-02-02
Open a terminal and post the outputs of these two commands here.

Applications- > Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zuknivek on 2008-02-02
> **taurus said:**
> Open a terminal and post the outputs of these two commands here.

Applications- > Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

Ok i did and i still get the same errors. It says "Movie Player cannot be installed on your computer type (i386) Either the application requires special hardware features or the vendor decided to not support your computer type."
I had this program installed before but it wouldn't let me download a codec to watch movies so i decided to uninstall it and now i can't reinstall it. 
Another error i get is "cannot install 'mplayer'. This application conflicts with other installed software. To install 'mplayer' the conflicting software must be removed first. Swith to the 'synaptic' package manager to resolve this conflict." 
Any ideas on what i need to uninstall to make it work? I just installed ubuntu 7.10 on my laptop yesterday and i could install any programs i wanted until i installed my broadcom wireless driver and i installed a couple things trying to make my AWN to work. Other than that there is nothing that i have installed on my computer. Please help.

---

### Post by taurus on 2008-02-02
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Sounds to me like you didn't have any repos available in there because your network was not working during the installing process.  Therefore, you need to edit /etc/apt/source.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  Now, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zuknivek on 2008-02-02
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Sounds to me like you didn't have any repos available in there because your network was not working during the installing process.  Therefore, you need to edit /etc/apt/source.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  Now, run

```
sudo apt-get update
sudo apt-get upgrade
```

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse

```

Terminal just got done downloading 250mb of files and is installing them now so i will post after they are installed. This seems like it will work. Thank you for the help.

---

### Post by gyuszika on 2008-02-02
Well I also had the problem with the standard movie player. I don´t use it anymore, because it always has problems with CODECs and so on. I now use mplayer and that works fine.

code:

apt-get install mplayer

---

### Post by zuknivek on 2008-02-02
This solved my problem. Thank you for your help. It was greatly appreciated.

---

