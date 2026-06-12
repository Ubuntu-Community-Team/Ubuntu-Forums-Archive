---
title: "Uppdate"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by JohanA on 2009-05-08
[LEFT]Hi can anybody help me when I try to uppdate Ubuntu this happend:


The repository may no longer be available or could not be contacted because of network problems. An older version of the index will be used if available. If not, the repository will be ignored. Check your network connection and make sure that the address of the repository in the settings are correct. 





 Failed to fetch cdrom: / / Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) / dists/intrepid/main/binary-i386/Packages Use the apt-cdrom to APT will recognize this cd. apt-get update can not be used to add records 
Failed to fetch cdrom: / / Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) / dists/intrepid/restricted/binary-i386/Packages Use the apt-cdrom to APT will recognize this cd. apt-get update can not be used to add records 
 Some index files could not be retrieved, they have been ignored or they have old used instead.




Not sure it's spelled correct used google translate.
Thanks for all help.
[/LEFT]

---

### Post by _Purple_ on 2009-05-08
Are you using a different language in ubuntu other than English? If so, type the following command 
```
export LANG=
```
This will show the rest of the text in English on same terminal window.

Then run and post the output of
```
sudo apt-get update
```

---

### Post by Partyboi2 on 2009-05-08
> **JohanA said:**
> [LEFT]Hi can anybody help me when I try to uppdate Ubuntu this happend:


The repository may no longer be available or could not be contacted because of network problems. An older version of the index will be used if available. If not, the repository will be ignored. Check your network connection and make sure that the address of the repository in the settings are correct. 





 Failed to fetch cdrom: / / Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) / dists/intrepid/main/binary-i386/Packages Use the apt-cdrom to APT will recognize this cd. apt-get update can not be used to add records 
Failed to fetch cdrom: / / Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) / dists/intrepid/restricted/binary-i386/Packages Use the apt-cdrom to APT will recognize this cd. apt-get update can not be used to add records 
 Some index files could not be retrieved, they have been ignored or they have old used instead.




Not sure it's spelled correct used google translate.
Thanks for all help.
[/LEFT]

Hi, open up Software Sources (System>Admin>Software Sources) and under the first tab make sure under "Installable from cdrom/dvd" that the cdrom is unticked.

---

### Post by JohanA on 2009-05-08
W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.



this is what i see...

---

### Post by _Purple_ on 2009-05-08
Did you try what Partyboi2 has said and run sudo apt-get update? Do you still get the error?

---

### Post by JohanA on 2009-05-08
ye still error

---

### Post by _Purple_ on 2009-05-08
Can you run this command and post the content of the file 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by JohanA on 2009-05-08
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty main
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty universe main multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates main
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe main multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" inaktiverad vid uppgradering till jaunty
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 8.10 inaktiverad vid uppgradering till jaunty
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by Sef on 2009-05-08
> deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
Put a # before deb cdrom:.  It should look like this:  #deb cdrom:.  That will comment out the line, i.e.,  it will be ignored.

---

### Post by JohanA on 2009-05-08
Thanks for all helps works fine now

---

