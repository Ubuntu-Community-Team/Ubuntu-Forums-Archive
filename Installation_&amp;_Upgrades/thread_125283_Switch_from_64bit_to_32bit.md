---
title: "Switch from 64bit to 32bit"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by matsie on 2006-02-03
Hi

Currently I run a dual boot system on AMD64 with Sata Raid Hdd. Ubuntu 5.10 64 bit distribution and Windows XP. 

I would like to change the Ubuntu 5.10 64 bit distri for a 32 bit distri. 
How can I do that without installing the Ubuntu from a LiveCD or DVD. I would like to save the Sata Raid installation. 

Any ideas are welcome. 

mat

---

### Post by o_fortuna on 2006-02-03
[QUOTE=matsie]Hi

Currently I run a dual boot system on AMD64 with Sata Raid Hdd. Ubuntu 5.10 64 bit distribution and Windows XP. 

I would like to change the Ubuntu 5.10 64 bit distri for a 32 bit distri. 
How can I do that without installing the Ubuntu from a LiveCD or DVD. I would like to save the Sata Raid installation. 

Any ideas are welcome. 

mat[/QUOTE]
You could try changing your sources.list:
```
sudo gedit /etc/apt/sources.list
```
This is my sources.list for 32-bit Ubuntu:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted univers e multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted uni verse multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://people.ubuntu.com/~doko/OOo2 ./

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-fr ee
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free no n-free

deb http://deb.opera.com/opera/ etch non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe m ultiverse

deb http://kubuntu.org/packages/kde35 breezy main
## created by arniemaxremoved
```
(It's the one created by automatix) Now do this in the terminal:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade
```
I really have no clue if this will work, though. It's been awhile since I used 64-bit Ubuntu, and I installed 32-bit with the CD. Theoretically, it should work.

---

