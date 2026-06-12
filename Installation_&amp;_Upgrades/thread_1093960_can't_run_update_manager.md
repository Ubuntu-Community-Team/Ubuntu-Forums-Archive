---
title: "can't run update manager"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by jayanramesh on 2009-03-12
Dear pals,
when I run synaptic package manager it gives the following massage-"E: Type 'x' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.".help to resolve this problem will be very much appreciated.

---

### Post by Partyboi2 on 2009-03-12
Looks like you have a bad entry in your sources.list. Can you open a terminal (Applications>Accessories>Terminal) and post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by binbash on 2009-03-12
there is something wrong at line 57 @ /etc/apt/sources.list  . Paste it here or you can check that line

---

### Post by jayanramesh on 2009-03-12
Dear partyboi2
It's wonderful seeing you again.I did what you asked me to do .This is what I got at terminal---"# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #Google
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock #Cairo Dock
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-proposed main universe
x
".And your help will be highly esteemed.
Thank you.

---

### Post by jayanramesh on 2009-03-12
> **binbash said:**
> there is something wrong at line 57 @ /etc/apt/sources.list  . Paste it here or you can check that line

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #Google
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock #Cairo Dock
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-proposed main universe
x

---

### Post by Therion on 2009-03-12
> **jayanramesh said:**
> 
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-proposed main universe
**[COLOR="Red"]x[/COLOR]** [COLOR="Blue"]<--- Rogue Character![/COLOR]
".And your help will be highly esteemed.
Thank you.
There's your problem, according to the error message.  Just clean up that line and you should be fine.

---

### Post by avtolle on 2009-03-12
You need to edit the list and delete the "x" on the last line. ```
sudo nano /etc/apt/sources.list
```delete the "x", then Ctrl+o to write, Enter to save to the file, Ctrl+x to exit nano, then do```
sudo aptitude update
sudo aptitude safe-upgrade
```please post any error messages you might get.

---

### Post by jayanramesh on 2009-03-14
Dear Avtolle,
Thank you very much for your explicit and transparent help you provided me.Problem solved and my little knowledge growing stronger imbibing lessons from good people like you.Once again thanks a lot.

---

### Post by jayanramesh on 2009-03-14
> **Therion said:**
> There's your problem, according to the error message.  Just clean up that line and you should be fine.
Dear Therion
if I say" otoconia" or just a "cor"you won't understand unless  anyone gives you clear definition . Being a physician I can understand but not a lay-people.So please furnish a simple to tough remedy depends on someone's grade on that particular field of knowledge.If you are stronger in one field naturally weaker in another
No arrogance any-time-any-where.If you do so you will really  be always behind me as you mentioned.
Thank you very much-For your sophisticated way of answering.

---

