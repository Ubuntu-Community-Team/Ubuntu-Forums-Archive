---
title: "sources"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by num on 2009-02-09
I used the alternative disk to install Ubuntu 8.10 Desktop Edition but I only have two sources and I cannot find much of the software I am looking for in Synaptic Manager. So I am wondering how do I add SourceForge into the sources list? I don't see it there.

---

### Post by N4zgu1 on 2009-02-09
you mean repositories??

I think that sourceforge doesnt have reppositories

---

### Post by num on 2009-02-09
what to do cause I cannot find anything. I cannot find flash i cannot find rar-free i cannot find amule azueras and nothing. what to do?

---

### Post by num on 2009-02-09
can someone please help?

---

### Post by oldos2er on 2009-02-10
Check System, Administration, Software Sources, and make sure all boxes under 'Downloadable from the internet' are checked.

---

### Post by num on 2009-02-10
yup i done that but still nothing :( please help.

---

### Post by oldos2er on 2009-02-10
Can you please post the output of
```
cat /etc/apt/sources.list
```
entered into a terminal?

---

### Post by num on 2009-02-10
here you go:

```

administrator@server:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe main #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
administrator@server:~$ 

```

---

### Post by oldos2er on 2009-02-10
Nothing jumps out at me as being obviously wrong with your sources.list. If you use the original search (not quick search) function in Synaptic, are you able to find flash and amule?

 Oh, and before you search, run Reload.

---

### Post by num on 2009-02-10
i have done reload numerous times and no i am not able to find flash or amule.

---

### Post by num on 2009-02-11
can anyone help?

---

### Post by oldos2er on 2009-02-11
Here's mine:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081030)]/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse main #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted multiverse universe main #Added by software-properties
deb http://ubuntusatanic.org/hell intrepid main

deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main

deb http://ppa.launchpad.net/file-browser-applet-dev/ubuntu intrepid main
deb-src http://ppa.launchpad.net/file-browser-applet-dev/ubuntu intrepid main

## deb http://apt.boxee.tv intrepid main
```

 You might want to comment out proposed and backports. Make a copy of your current list, then copy mine over yours (you need to do this as root).

---

