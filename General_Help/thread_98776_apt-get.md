---
title: "apt-get"
date: 2005-12-04
forum: General Help
---

### Post by Dooffas on 2005-12-04
When ever i try and use apt-get it says E: Couldn't find package <NameOfFile>.:confused: 
I canot seem to fix it any help would be apreceated.
Chears
Dooffas

---

### Post by HighPlainsDrifter on 2005-12-04
apt-get **install** package

:)

---

### Post by heimo on 2005-12-04
Check your /etc/apt/sources.list and run *apt-get update*. Search for exact package name using *apt-cache search [search term]* or search in [http://packages.ubuntu.com]("http://packages.ubuntu.com")

If you still can't install any packages, please let us know which package you're trying to install.

[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

---

### Post by Dooffas on 2005-12-04
I tryed apt-get update and this is what i get :confused: 
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Dooffas

---

### Post by Dooffas on 2005-12-04
ok have done the update it updates nothing 
  dooffas@ubuntuGreenBox:~$ sudo apt-get update
  Password:
  Reading package lists... Done
  dooffas@ubuntuGreenBox:~$ sudo apt-get upgrade
  Reading package lists... Done
  Building dependency tree... Done
  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Im trying to install ati drivers and the comand im trying to do is 
  sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make   debconf libstdc++5 gcc-3.3-base

all i get is 

dooffas@ubuntuGreenBox:~$ sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make             debconf libstdc++5 gcc-3.3-base
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4

---

### Post by heimo on 2005-12-04
Could you post your /etc/apt/sources.list? Or you could try to change it using these instructions:
[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
EDIT: Be sure to use the sources for "Breezy".

After changing sources.list, run apt-get update and try again.

---

### Post by shreevatsa on 2005-12-04
Better yet, let [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) autogenerate your sources.list for you. 
Also, try replacing "gcc-3.4" by "gcc-4.0" and "gcc-3.3-base" by "gcc-4.0-base", because those are the packages that Breezy uses.

---

### Post by Dooffas on 2005-12-04
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by aysiu on 2005-12-04
Do you see all the # signs in front of each line?
That # sign basically tells your computer "ignore whatever is after this sign," so you essentially have **no** sources in your /etc/apt/sources.list except the CD-ROM.

Follow the instructions in the first link in my sig. Use the Breezy 5.10 instructions.

---

### Post by Dooffas on 2005-12-08
thanks to all that helped I think i have fixed the falt i will get back to you soon as to wether it did work or not.

Thanks again
Dooffas:smile:

---

### Post by unisol on 2005-12-08
make sure you are only running one package manager at a time

---

### Post by missmoondog on 2005-12-08
very handy to keep this link somewhere!!

 [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

