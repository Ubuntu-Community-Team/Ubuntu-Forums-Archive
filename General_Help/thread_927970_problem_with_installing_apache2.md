---
title: "problem with installing apache2"
date: 2008-09-23
forum: General Help
---

### Post by Chilliman on 2008-09-23
hi.
i started to load apache2 using webmin V1.430 on my Ubuntu Linux server 7.10 when i go any error mesaage asking me to load my cd in the drive and press enter, which i did the system keeps asking me to load the cd in the drive and press enter.
i tried doing it from the command line with the same out come this was the same setup i load the software to start with.
can any one help.

chilliman

---

### Post by Titan8990 on 2008-09-23
Post the output of the following command:


cat /etc/apt/sources.list

---

### Post by Chilliman on 2008-09-23
here is the messages it returned.


# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
steve@snickers:~$ # deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
steve@snickers:~$

## Uncomment the following two lines to add software from the 'backports'
steve@snickers:~$ deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
-bash: syntax error near unexpected token `('
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
steve@snickers:~$ # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
steve@snickers:~$ # newer versions of the distribution.
steve@snickers:~$
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
-bash: deb-src: command not found
steve@snickers:~$
steve@snickers:~$ ## Major bug fix updates produced after the final release of the
steve@snickers:~$ ## distribution.
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
-bash: deb-src: command not found
steve@snickers:~$
steve@snickers:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
steve@snickers:~$ ## team, and may not be under a free licence. Please satisfy yourself as to
steve@snickers:~$ ## your rights to use the software. Also, please note that software in
steve@snickers:~$ ## universe WILL NOT receive any review or updates from the Ubuntu security
steve@snickers:~$ ## team.
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
-bash: deb-src: command not found
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
-bash: deb-src: command not found
steve@snickers:~$
steve@snickers:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
steve@snickers:~$ ## team, and may not be under a free licence. Please satisfy yourself as to
steve@snickers:~$ ## your rights to use the software. Also, please note that software in
steve@snickers:~$ ## multiverse WILL NOT receive any review or updates from the Ubuntu
steve@snickers:~$ ## security team.
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
-bash: deb-src: command not found
steve@snickers:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
-bash: deb: command not found
steve@snickers:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
-bash: deb-src: command not found
steve@snickers:~$
steve@snickers:~$ ## Uncomment the following two lines to add software from the 'backports'
steve@snickers:~$ ## repository.
steve@snickers:~$ ## N.B. software from this repository may not have been tested as
steve@snickers:~$ ## extensively as that contained in the main release, although it includes
steve@snickers:~$ ## newer versions of some applications which may provide useful features.
steve@snickers:~$ ## Also, please note that software in backports WILL NOT receive any review
steve@snickers:~$ ## or updates from the Ubuntu security team.
steve@snickers:~$ # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
steve@snickers:~$ # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
steve@snickers:~$
steve@snickers:~$ ## Uncomment the following two lines to add software from Canonical's
steve@snickers:~$ ## 'partner' repository. This software is not part of Ubuntu, but is
steve@snickers:~$ ## offered by Canonical and the respective vendors as a service to Ubuntu
steve@snickers:~$ ## users.
steve@snickers:~$ # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
steve@snickers:~$ # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
steve@snickers:~$
steve@snickers:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
-bash: deb: command not found
steve@snickers:~$ deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
-bash: deb-src: command not found
steve@snickers:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
-bash: deb: command not found
steve@snickers:~$ deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
-bash: deb-src: command not found
steve@snickers:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
-bash: deb: command not found
steve@snickers:~$ deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
-bash: deb-src: command not found

---

### Post by taladan on 2008-09-23
open /etc/apt/sources.list in your favourite text editor (preferably from the command line using sudo) and change the 2nd line from:


deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

to:


#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

Save it, then run:
sudo apt-get update;sudo apt-get install -f

This is telling apt NOT to use the CDrom repository (as there's no need for it), and then running an update of repositories, then fixing (-f) any broken installs.

Hope this helps,
Tal

---

### Post by Chilliman on 2008-09-23
Thanks it worked great

chilliman

---

