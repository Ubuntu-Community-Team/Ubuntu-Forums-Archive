---
title: "medibuntu problems"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by lozanoa11 on 2009-05-04
im trying to install medibuntu and i keep getting an error:
 Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'
im not sure what im doing wrong here and im kinda new at this so any help would be apreciated. 
I just want to watch streaming video on like you tube and stuff, am i on the right track?

---

### Post by lozanoa11 on 2009-05-04
running jaunty btw

---

### Post by kostkon on 2009-05-04
I think that's the old URL for [*Medibuntu*]("http://medibuntu.org/").

I recommend you to check its instructions [here]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by lozanoa11 on 2009-05-04
that is what i have been folowing and when i get to the gpg key part i get that error:
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by kostkon on 2009-05-04
First of all, do a
```
sudo apt-get update
```
in a terminal and post the output here.

Also, do:
```
gedit /etc/apt/sources.list.d/medibuntu.list
```
and post its contents here.

Also, to be sure, do:
```
gedit /etc/apt/sources.list
```
and post again the contents here.

---

### Post by lozanoa11 on 2009-05-04
for the first one:
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/jaunty/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Un less you want the whole thing

#2:
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope"

#3:
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #google
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #medibuntu
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./

## Medibuntu - Ubuntu 6.10 "jaunty eft"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) jaunty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) jaunty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by kostkon on 2009-05-04
OK. I'll give you a quick fix. Open a terminal and give the following command (it will ask for a password, give yours):
```
gksudo gedit /etc/apt/sources.list
```
and delete these lines:
```
## Medibuntu - Ubuntu 6.10 "jaunty eft"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ jaunty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ jaunty free non-free
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free
```
save, and then do a
```
sudo apt-get update
```
and everything should be OK.

---

### Post by lozanoa11 on 2009-05-04
i did what you said first and no fix but then i did it in:
gedit /etc/apt/sources.list
and it seems to be ok. no errors any way. thanks

---

### Post by kostkon on 2009-05-04
> **lozanoa11 said:**
> i did what you said first and no fix but then i did it in:
gedit /etc/apt/sources.list
and it seems to be ok. no errors any way. thanks
Yeah, sorry about this. :frown:

I hope you didn't change the contents of the file
```
/etc/apt/sources.list.d/medibuntu.list
```
It should contain the following lines:
```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
#deb-src http://packages.medibuntu.org/ jaunty free non-free #Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope"
```

---

### Post by lozanoa11 on 2009-05-04
fixed that, is there anything else i have to do to get embedded videos to play?
i am using opera btw

---

### Post by kostkon on 2009-05-04
> **lozanoa11 said:**
> fixed that, is there anything else i have to do to get embedded videos to play?
i am using opera btw
Now do a
```
sudo apt-get update
```
to be sure.

Do you mean Flash videos or avi/mp4/other videos embedded in pages?

---

### Post by lozanoa11 on 2009-05-04
yea but now i got this error:
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)

yea like youtube and other similar webpages

---

### Post by kostkon on 2009-05-04
> **lozanoa11 said:**
> yea but now i got this error:
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)

yea like youtube and other similar webpages
It seems that you have duplicate entries in
```
/etc/apt/sources.list.d/medibuntu.list
```
Post its output again here if you want, doing
```
gedit /etc/apt/sources.list.d/medibuntu.list
```

For *Flash*, try installing the *flashplugin-nonfree* package from *Synaptic*.

For other videos, I believe you'll need to install the *totem-mozilla* package, if it not already installed. It is the *Totem* plugin for *Firefox* but I think *Opera* will pick it up and use it.

You could also install the *ubuntu-restricted-extras* package to get some more codecs among other things.

And finally, the windows codecs package called *w32codecs* (or *w64codecs* if you have a 64bit system).

You can search for them and install them using *Synaptic*.

---

### Post by lozanoa11 on 2009-05-04
i found the problem. 
well video's work in firefox but not opera so ill have to try to find a solution for that or just use firefox.
thanks again

---

