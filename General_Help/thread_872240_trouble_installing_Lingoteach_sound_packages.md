---
title: "trouble installing Lingoteach sound packages"
date: 2008-07-27
forum: General Help
---

### Post by Xoanan on 2008-07-27
Hi all

I am having trouble installing the sound packages for Lingoteach.  The directions say> If you are running Debian, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) etch main 

Replacing ftp.de.debian.org/debian with the mirror in question. 

There is a list of sites to add to sources.list, but everytime I attempt to add them, synaptic returns error in line 44.  Now here is the list without being changed

```
# 
# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.linux.duke.edu/ubuntu/ hardy main restricted multiverse 
deb-src http://archive.linux.duke.edu/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.linux.duke.edu/ubuntu/ hardy-updates main restricted multiverse 
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb http://wine.budgetdedicated.com/apt edgy main
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://archive.linux.duke.edu/ubuntu/ hardy-security main restricted multiverse 
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
# deb http://archive.canonical.com/ubuntu hardy partner
# deb http://packages.medibuntu.org/ hardy free non-free
deb http://archive.linux.duke.edu/ubuntu/ hardy-proposed restricted main multiverse universe 
```

If I add the next line with any of the mirrors, I get errors. I have a feeling that its a formatting issue.  Any ideas?

:popcorn:

---

