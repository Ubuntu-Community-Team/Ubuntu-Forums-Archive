---
title: "Suspend2 on Dapper"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2006-11-19
Hello,

I'd like to enable **suspend-to-DISK** or **hibernate** on my Dell i8100 laptop.  I am using 6.06.1 LTS (Dapper Drake).  I have the restricted modules enabled in my sources list as well as some other "non-standard" repositories. I've appended my **sources.list** at the end of this post.

I would like to somehow install Software Suspend 2 so that I can make use of hibernate.  I require the binary nvidia drivers as this is i8100 laptop is a mission critical machine and I need to have twinview output for work presentations.  I also need to have openGL rendering for several software packages.

I am using the 2.6.15-27-386 kernel.  I am unclear as to how to install Software Suspend 2 and still be able to use the restricted (or any other) respositories.  From my perspective, it appears that Bernard Blackham has precompiled some dapper drake kernels for simple download(?)  I think that installing & using the patched kernels from the dagobah repos will allow me to do this ( [http://www.ucc.asn.au/~dagobah/dapper-kernels/](http://www.ucc.asn.au/~dagobah/dapper-kernels/) ).  However, there doesn't appear to be a patched kernel (2.6.15-27-386) that matches my specific kernel in this repo.  Can I use a 2.6.15-26-386 patched version from this dagobah repo?

Additionally, it is unclear to me whether patching with one of these dagobah kernels will preclude me from using the restricted repos, or any of the other repos that I may need in the future (hard to determine at this point).

Any advice, or links, or help would be appreciated.  Any feedback & experiences with these precompiled kernels and how they work would also be of help.  Hibernate (suspend-to-DISK) is the only thing that seems to have me "beat" on Dapper.

-CH  :-k 


```
## Main Restricted Dapper Drake Repository
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## Main Restricted Dapper Drake Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

## Universe Dapper Drake Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## Broadcom 43xx WiFi PCMCIA Card Driver Repository
deb http://ubuntu.cafuego.net dapper-cafuego bcm43xx
deb-src http://ubuntu.cafuego.net dapper-cafuego bcm43xx

## BiBUS Bibliography Programme Repository
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./


## Automatix Repository
deb http://www.getautomatix.com/apt dapper main


#AUTOMATIX REPOS START

deb http://people.ubuntu.com/~seb128/deb ./

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

