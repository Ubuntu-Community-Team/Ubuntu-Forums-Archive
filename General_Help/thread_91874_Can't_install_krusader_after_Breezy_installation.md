---
title: "Can't install krusader after Breezy installation"
date: 2005-11-18
forum: General Help
---

### Post by nomeat on 2005-11-18
Nothing anymore in Synaptic and apt-get returns nothing useful.

Help, I can't live without krusader. 
I don't understand those who can :???:

---

### Post by teaker1s on 2005-11-18
change hoary to breezy in sources list

---

### Post by teaker1s on 2005-11-18
sudo gedit /etc/apt/sources.list
kde uses kwrite or kate instead of gedit i believe


## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe main restricted
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by nomeat on 2005-11-18
Thanks for the new sources list.
I'll check it once I am through with Automatix.

Just curious:
All over the forum I read about OpenOffice2 having to be installed after breezy.
Even Automatix has this option, but I left it unticked.

OO2 was up and running straight after my virgin Breezy installation.

---

### Post by angrykeyboarder on 2005-11-18
[quote=nomeat]Thanks for the new sources list.
I'll check it once I am through with Automatix.

Just curious:
All over the forum I read about OpenOffice2 having to be installed after breezy.
Even Automatix has this option, but I left it unticked.

OO2 was up and running straight after my virgin Breezy installation.[/quote]

Breezy comes with a Beta of OOo2.  The final was released after Breezy was, that is what people are installing.

[http://ubuntuforums.org/showthread.php?t=80392&page=10](http://ubuntuforums.org/showthread.php?t=80392&page=10)

---

### Post by nomeat on 2005-11-18
Krusader works :D 

Needed still an apt-get update after changing sources list.

I will update OO2.

Thanks

---

