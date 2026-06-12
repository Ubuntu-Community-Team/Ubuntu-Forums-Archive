---
title: "Updating Ubuntu 8.10 failed"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by spnoe on 2009-03-19
I have a problem with the update manager. I am not knowlageable enogh to correct this problem.

Any help please.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'e' is not known on line 41 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by avtolle on 2009-03-19
Please post your /etc/apt/sources.list here.

---

### Post by spnoe on 2009-03-20
> **avtolle said:**
> Please post your /etc/apt/sources.list here.

I tried putting etc/apt/sources.list in the terminal but the reply was command not found. What am I doing wrong?

Steve

---

### Post by tad1073 on 2009-03-20
try this

```
sudo gedit /etc/apt/sources.list
```

---

### Post by spnoe on 2009-03-20
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

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
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
e

---

### Post by tad1073 on 2009-03-20
remove the 
```
e
```
from the very bottom

---

### Post by spnoe on 2009-03-20
> **tad1073 said:**
> remove the 
```
e
```
from the very bottom

I removed the e and tried to save but a message says I do not have permission.

I am sorry to be such a pain but I do appreciate your help.

Thanks
Steve

---

### Post by bruno9779 on 2009-03-20
are you sure you wrote "sudo" before "Gedit"?

---

### Post by kpatz on 2009-03-20
Type **gksudo gedit /etc/apt/sources.list** in Alt-F2 or a terminal.

Enter your password when prompted.

Remove the stray "e", save and exit.

Re-run the update manager, or type **sudo apt-get update** in a terminal.

---

### Post by spnoe on 2009-03-20
> **bruno9779 said:**
> are you sure you wrote "sudo" before "Gedit"?
I tried again and this time it worked.

Thanks to all of you who offered help. Much appreciated.

Steve

---

