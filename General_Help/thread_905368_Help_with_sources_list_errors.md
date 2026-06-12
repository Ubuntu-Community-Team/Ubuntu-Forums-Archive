---
title: "Help with sources list errors"
date: 2008-08-30
forum: General Help
---

### Post by bj_ninetysix on 2008-08-30
I am a new user having a little difficulty with the software sources.  Several of my sources are not found. If you can direct me how to fix my specific errors, or perhaps a tutorial on fixing them it would be appreciated.

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/| Packages  
  404 Not Found
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/sudo Packages
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/tee Packages                               
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/-a Packages                                
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy//etc/apt/sources.list Packages             
  404 Not Found                          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/| Sources                                  
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/sudo Sources
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/tee Sources 
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/-a Sources  
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy//etc/apt/sources.list Sources
  404 Not Found

---

### Post by Elfy on 2008-08-30
Can you post it here please, run this command in a terminal and we can look

```
cat /etc/apt/sources.list
```

---

### Post by bj_ninetysix on 2008-08-30
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy universe
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy multiverse
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security main restricted
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security universe
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security multiverse
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list
deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock

deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe

---

### Post by Elfy on 2008-08-30
Open the file to edit it -```
gksudo gedit /etc/apt/sources.list
```

Find thes 2 lines and delete the red part

> deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main [COLOR="Red"]| sudo tee -a /etc/apt/sources.list[/COLOR]
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main [COLOR="#ff0000"]| sudo tee -a /etc/apt/sources.list[/COLOR]save and close the file, then this in a terminal

```
sudo apt-get update
```
Report any errors

---

### Post by bj_ninetysix on 2008-08-30
Thanks, that cleared up the errors. Now it just says I have a couple of duplicate entries:

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_non-free_binary-amd64_Packages)

I removed the duplicates from the sources, reran sudo apt-get update and it's all clear.  Thanks again for the help.

---

### Post by Elfy on 2008-08-30
Ok - if this first command returns medibuntu in a terminal remove medibuntu from your sources list with second as before

```
ls /etc/apt/sources.list.d[code] 

[code]gksudo gedit /etc/apt/sources.list
```
remove> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

then ```
sudo apt-get update
```

---

