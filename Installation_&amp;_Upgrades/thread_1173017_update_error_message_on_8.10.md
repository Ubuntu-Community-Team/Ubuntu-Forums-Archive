---
title: "update error message on 8.10"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Prium on 2009-05-29
I haven't been able to update for a while now. 
Today I tried again and it still gave an error (see below)

I have tried a bunch of different download sources but in doing so has made no difference. I don't understand what is going on. Suggestions?  

[[IMG]http://img38.imageshack.us/img38/809/screenshotsnb.png[/IMG]](http://img38.imageshack.us/my.php?image=screenshotsnb.png)

---

### Post by _Purple_ on 2009-05-29
Can you post the contents of 
```
gedit /etc/apt/sources.list
```

---

### Post by Prium on 2009-05-29
Thanks for your reply. Here are the contents:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid main restricted
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid universe
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid universe
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates universe
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid multiverse
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid multiverse
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security main restricted
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security universe
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security universe
deb [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.uasw.edu/](http://archive.ubuntu.uasw.edu/) intrepid-security multiverse
# deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu intrepid/
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu jaunty/

---

### Post by _Purple_ on 2009-05-29
Are you using intrepid or jaunty? Your profile says jaunty but you have entries for both intrepid and jaunty.

---

### Post by Prium on 2009-05-29
It is indeed Intrepid that I am inquiring about - sorry for the confusion. I am on my work PC. My own person computer has Jaunty.

---

### Post by _Purple_ on 2009-05-29
This is the line that is triggering the error message
```
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu jaunty/
``` 

Open the file using
```
gksudo gedit /etc/apt/sources.list
```

and place # in front of that line mentioned above and save. Then run in terminal
```
sudo apt-get update
```

In case you need that repository for anything, replace jaunty with intrepid in that line.

---

### Post by Prium on 2009-05-29
Yes that did the trick \\:D/

Thank you Purple

---

### Post by _Purple_ on 2009-05-29
You are welcome. :)

---

