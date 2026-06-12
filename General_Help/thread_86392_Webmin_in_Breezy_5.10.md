---
title: "Webmin in Breezy 5.10"
date: 2005-11-05
forum: General Help
---

### Post by ajburch on 2005-11-05
I can't install Webmin because a dependency, libnet-ssleay-perl, won't install. Synaptic says 'it's not installable'. Using apt-get says, "it's not available, but is referred to by another package. This may mean the package is missing, has been obsoleted, or is only available from another source."

What does this mean, and how can I get around it to install webmin?

<--AJ

---

### Post by dutler on 2005-11-05
What reps are you using? I think you may need to use universe.

My /etc/apt/sources.list looks like this and webmin installed fine:> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
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

Installed, but I can login it... the defualt account is suppose to be root with the passwd from the system.... dont know what to do about it, but it was easy to install.

---

### Post by cora on 2005-11-28
In case anyone is looking for the answer, here's the solution:

set webmin root password:
sudo /usr/share/webmin/changepass.pl /etc/webmin root [password]


cheers!


[QUOTE=dutler]What reps are you using? I think you may need to use universe.

My /etc/apt/sources.list looks like this and webmin installed fine:

Installed, but I can login it... the defualt account is suppose to be root with the passwd from the system.... dont know what to do about it, but it was easy to install.[/QUOTE]

---

