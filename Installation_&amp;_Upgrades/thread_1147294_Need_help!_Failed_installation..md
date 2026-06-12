---
title: "Need help! Failed installation."
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by SuperZ on 2009-05-03
Everytime I try to install my automatic updates I get this error.

[IMG]http://img75.imageshack.us/img75/5100/errorr.png[/IMG]

Please help, because none of my games and most of my apps arent working.

Thanks.

---

### Post by SuperZ on 2009-05-03
Also tried installing to Jaunty... basically the same error...
[IMG]http://img75.imageshack.us/img75/2513/error2.png[/IMG]

---

### Post by SuperZ on 2009-05-03
bump

---

### Post by Old_Grey_Wolf on 2009-05-03
> **SuperZ said:**
> Everytime I try to install my automatic updates I get this error.

Please help, because none of my games and most of my apps arent working.

Thanks.

Try these commands
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 91DAE98F32FFB679

gpg --export --armor 91DAE98F32FFB679 | sudo apt-key add -

```

Then try automatic updates again.

---

### Post by SuperZ on 2009-05-03
still getting the same errors
> 
W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://br.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://br.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)


---

### Post by Old_Grey_Wolf on 2009-05-03
What do you get if you enter in this command
```
cat /etc/apt/sources.list
```

---

### Post by SuperZ on 2009-05-03
@ Old gray wolf

I get this

> root@ZgameZ:/home/superz# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main partner
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid partner
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid partner

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security partner restricted main multiverse universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
root@ZgameZ:/home/superz# 


---

### Post by Old_Grey_Wolf on 2009-05-03
Open the file /etc/apt/sources.list in an editor, and comment out these lines

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security partner restricted main multiverse universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

Then try the update again.

You can uncomment them later if this doesn't help.

If it doesn't work try a different server in Synaptic. Pick a different location from the "Download from" menu.

---

### Post by SuperZ on 2009-05-03
ok... i did that... now no updates are shown and the windown on the Update manager to upgrade to jaunty is gone too >.<

Plus I get this after I check for updates

> Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://br.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://br.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Old_Grey_Wolf on 2009-05-03
> **SuperZ said:**
> ok... i did that... now no updates are shown and the windown on the Update manager to upgrade to jaunty is gone too >.<

Uncomment the two lines.

Then try a different server in Synaptic. Pick a different location from the "Download from" menu. 

If that doesn't work someone else will need to help you.

---

### Post by Old_Grey_Wolf on 2009-05-03
Just another guess. The two lines do not have an accompanying line for deb-src. Maybe you need to copy the deb http......line and make a deb-src http......line from it.

Just a question: why are you logged in as root?

---

### Post by SuperZ on 2009-05-03
Oh... i do most of my things with root so i dont have to keep sudoing all the time... 
and wolf... Im going to kill myself.
Iv been messing around with all these tutorials and stuff to see what I was doing wrong, and I cant find anything... wow.

getting the same error as before. Can you please explain a little better what you said? on the previous post about adding an http line?

---

### Post by SuperZ on 2009-05-04
bump

---

### Post by SuperZ on 2009-05-05
bump

---

### Post by SuperZ on 2009-05-07
last bump then i give up >.<

---

