---
title: "Error When Trying To Install The Gimp With Apt-Get"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by nathanpc on 2009-08-20
Hello,
 I'm a Ubuntu senior, but when i try to install The Gimp with apt-get i get an error, that says about the library libgimp, here is the console log:
```
eeepc@eeepc:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (<= 2.6.1-z) but 2.6.3-1ubuntu1~intrepid1 is to be installed
E: Broken packages
```
Remember that i'm using Ubuntu Intrepid Ibex in Eee PC(Easy Peasy).
If is needed here is my sources.list file:
```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://br.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://br.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://br.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://br.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```
Thanks,
 Nathan Paulino Campos

---

### Post by nathanpc on 2009-08-20
Please, someone help me!

---

### Post by Partyboi2 on 2009-08-20
Hi, open Synaptic (System>Admin>Synaptic) and do a search for 'libgimp2.0' then highlight the package and go to Package>Force Version) and see if you can downgrade the package.

---

### Post by nathanpc on 2009-08-20
It not work!

---

### Post by Partyboi2 on 2009-08-20
If that did not work then open a terminal and remove  libgimp2.0
```
sudo apt-get remove libgimp2.0
```
then install gimp which will reinstall libgimp2.0
```
sudo apt-get update
sudo apt-get install  gimp
```

---

### Post by louieb on 2009-08-20
Odd that Gimp was not a part of the original install. Did you at one time uninstall it?

Also your sources.list has a mix of **br.archive** and **archive** repositories. Perhaps you are running into a repository sync problem.

Try System>Administration>Software Sources > Download from > other > Select Best Server.

Just something to try.

---

### Post by ukbobby55 on 2010-02-05
> **Partyboi2 said:**
> If that did not work then open a terminal and remove  libgimp2.0
```
sudo apt-get remove libgimp2.0
```
then install gimp which will reinstall libgimp2.0
```
sudo apt-get update
sudo apt-get install  gimp
```

Just to say this worked for me first time..many thanks

---

