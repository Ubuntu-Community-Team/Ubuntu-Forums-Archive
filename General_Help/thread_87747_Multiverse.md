---
title: "Multiverse"
date: 2005-11-08
forum: General Help
---

### Post by tikal26 on 2005-11-08
Hey:
I am really confuses maybe I did something wrong, but I am trying to get acroreader and Realplayer, but I keep on beign told they are in multivers the problem is that in my list the only thing that has multiverse is the backports. Am I missing something?:confused:

---

### Post by Manny C on 2005-11-08
Quite possibly. Copy and paste your /etc/sources.list file here please.

---

### Post by tikal26 on 2005-11-08
here it is
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#koffice
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu) breezy main

---

### Post by Manny C on 2005-11-08
The required changes are in **bold**.
```

**#** deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted **universe multiverse**
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted **universe multiverse**

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe **multiverse**
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe **multiverse**

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe **multiverse**
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe **multiverse**
#koffice
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu]("ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu") breezy main 
```

---

### Post by tikal26 on 2005-11-08
thanks:p

---

### Post by alvonsius on 2005-11-08
Can I have a question? What is the difference between main restricted universe and multiverse ???

---

### Post by Manny C on 2005-11-09
See [this]("http://www.ubuntuforums.org/showpost.php?p=459045&postcount=2") post.

---

### Post by asimon on 2005-11-09
[QUOTE=alvonsius]Can I have a question? What is the difference between main restricted universe and multiverse ???[/QUOTE]
main contains free software software which is supported by Ubuntu
restricted contains non-free software which is supported by Ubuntu, i.e. some hardware drivers.
universe contains free software which is supported by the community (i.e. [MOTU](https://wiki.ubuntu.com/MOTU?highlight=%28motu%29))
multiverse contains non-free software which is supported by the community

---

### Post by alvonsius on 2005-11-09
Humm, thanks for the explanation. Now everything is clear ... :D

---

