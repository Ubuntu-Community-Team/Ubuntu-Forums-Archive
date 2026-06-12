---
title: "Can someone post your sources.list"
date: 2005-12-05
forum: General Help
---

### Post by KrisDwyer on 2005-12-05
I am in dire need of a proper sources.list

If someone could post this, please do so...

Thanks
Kris

---

### Post by Bachstelze on 2005-12-05
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```

Thanks to aysiu :)

---

### Post by mcmuffy on 2005-12-05
This is my list though you may want to use the stuff below the dotted line with care.

```

deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# Breezy Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse 

#---------------------------------------------------------

#Non free
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# Enlightenment E17
#deb http://ubuntu.nooms.de/ hoary/

#KLibido
#deb http://orniere-du-globe.net/debian ./
#deb-src http://orniere-du-globe.net/debian ./

#Nzb
#deb http://people.realnode.com/~mnordstr/ package/

#Gambas
#deb http://www.linex.org/sources/linex/debian/ cl gambas

#KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main

#K9copy
#deb http://repos.knio.it/ sarge main contrib non-free
#deb-src http://repos.knio.it/ sarge main contrib non-free

#Main Debian Library - Trackballs
#deb http://http.us.debian.org/debian unstable main contrib non-free

```

---

### Post by -DarkMind- on 2005-12-05
```
deb file:/var/cache/apt-build/repository apt-build main

##UBUNTU
deb http://cl.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://cl.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## Extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted

#JAVA

deb http://ubuntu.tower-net.de/ubuntu/ breezy java

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free

#aMule
deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

#BMPx
deb http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx ./

#SKYPE
deb http://download.skype.com/linux/repos/debian/ stable non-free

#KDE3.5
deb http://kubuntu.org/packages/kde35 breezy main

```

---

### Post by KrisDwyer on 2005-12-05
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

I get that when i use either sources.list and it times out and says it cant stat packages... help?

---

### Post by -DarkMind- on 2005-12-05
[QUOTE=KrisDwyer]0% [Connecting to archive.ubuntu.com (1.0.0.0)]

I get that when i use either sources.list and it times out and says it cant stat packages... help?[/QUOTE]


change to **us**.archive.ubuntu.com

or the code of your country, in my case is cl 8)

---

### Post by KrisDwyer on 2005-12-05
Nope i have the same problem :(

and after timing out i get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by -DarkMind- on 2005-12-05
[QUOTE=KrisDwyer]Nope i have the same problem :(

and after timing out i get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (**1.0.0.0**), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out[/QUOTE]

very extrange..

1.0.0.0 the ip?  :o

---

### Post by KrisDwyer on 2005-12-05
obviously not the IP for the repository :(

---

### Post by Chickenmonger on 2005-12-05
Do you have internet connectivity at all?

---

### Post by KrisDwyer on 2005-12-05
Of course...

---

### Post by Bandit on 2005-12-06
[QUOTE=Chickenmonger]Do you have internet connectivity at all?[/QUOTE]
Well she did post this topic somehow :rolleyes:

---

### Post by Bachstelze on 2005-12-06
[QUOTE=KrisDwyer]Nope i have the same problem :(

and after timing out i get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out[/QUOTE]

Run "sudo apt-get update" with an empty sources.list and then copy your file back and run it again. It should solve the issue.

---

